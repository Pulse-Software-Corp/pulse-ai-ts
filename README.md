# Pulse SDK for TypeScript

[![npm version](https://img.shields.io/npm/v/@pulse-software/sdk.svg)](https://www.npmjs.com/package/@pulse-software/sdk)

The Pulse SDK for TypeScript provides access to the [Pulse API](https://docs.runpulse.com/v2/introduction) from server-side TypeScript or JavaScript applications. It covers every route of API version 2, sends `Pulse-Version: 2` on every request, and returns typed results.

## Documentation

Full documentation is available at **[docs.runpulse.com/v2/sdks](https://docs.runpulse.com/v2/sdks)**. Every method and its parameters are listed in [reference.md](./reference.md).

## Installation

```sh
npm install @pulse-software/sdk
```

## Getting started

Create an API key in the [Pulse dashboard](https://platform.runpulse.com) under **API Keys**, then:

```ts
import { PulseClient } from "@pulse-software/sdk";

const client = new PulseClient({ apiKey: process.env.PULSE_API_KEY! });

const { parseId } = await client.parse.run({
  fileUrl: "https://platform.runpulse.com/api/examples/637e5678-30b1-45fa-acc4-877f2d636419/pdf",
  config: { model: "ultra-2" },
});

const parse = await client.parse.getResult({ parseId });
console.log(parse.markdown);
```

`apiKey` is required. The client doesn't read it from the environment.

## Usage

### Endpoints

Each endpoint is a group on the client, and every group has the same four calls. For Parse:

| Call | HTTP |
| --- | --- |
| `client.parse.run({ ... })` | `POST /parse` |
| `client.parse.get({ parseId })` | `GET /parse/{parse_id}` |
| `client.parse.getResult({ parseId })` | `GET /parse/{parse_id}/result` |
| `client.parse.cancel({ parseId })` | `DELETE /parse/{parse_id}` |

`classify`, `extract`, `split`, `tables`, `charts`, `pipeline` and `parse.batch` work the same way. Saved configs are in `client.<endpoint>.configs`, such as `client.extract.configs`. Webhooks are in `client.webhook`, usage is `client.usage.get()`, and organization settings are in `client.settings.org`.

Extract, Split, Tables and Charts read a completed parse by its `parseId`:

```ts
const { extractId } = await client.extract.run({
  parseId,
  config: {
    inputSchema: {
      type: "object",
      properties: {
        account_holder: { type: "string" },
        closing_balance: { type: "number" },
      },
    },
  },
});

const { extraction } = await client.extract.getResult({ extractId });
console.log(extraction.enriched);
```

### Async jobs

By default, `run` waits for its job to end. Send `async: true` to get the job's id at once, then poll its status. Use it for long documents, and wherever a proxy or load balancer might time out first. Pipelines and batches always run async.

```ts
const { parseId } = await client.parse.run({
  fileUrl: "https://example.com/report.pdf",
  config: { model: "ultra-2" },
  async: true,
});

let status = await client.parse.get({ parseId });
for (let delay = 2000; status.status === "queued" || status.status === "processing"; delay = Math.min(delay * 1.5, 15000)) {
  await new Promise((resolve) => setTimeout(resolve, delay));
  status = await client.parse.get({ parseId });
}

if (status.status === "completed") {
  const result = await client.parse.getResult({ parseId });
}
```

Status reads are free. Instead of polling, a [webhook](https://docs.runpulse.com/v2/webhooks) can tell your server when a job ends. [Jobs and results](https://docs.runpulse.com/v2/jobs) covers statuses and how long results are kept.

### File uploads

Send a document as `file` or `fileUrl`, never both:

```ts
import { createReadStream } from "node:fs";

const job = await client.parse.run({
  file: createReadStream("statement.pdf"),
  config: { model: "ultra-2" },
});
```

`file` accepts:

- Stream types: `fs.ReadStream`, `stream.Readable` and `ReadableStream`.
- Buffered types: `Buffer`, `Blob`, `File`, `ArrayBuffer`, `ArrayBufferView` and `Uint8Array`.
- A path: `{ path: "statement.pdf" }`.

To set the part's metadata, wrap the data:

```ts
const job = await client.parse.run({
  file: {
    data: createReadStream("statement.pdf"),
    filename: "statement.pdf", // optional
    contentType: "application/pdf", // optional
    contentLength: 1949, // optional
  },
  config: { model: "ultra-2" },
});
```

The SDK sets `Content-Type`, `Content-Disposition` and `Content-Length` from the metadata, or works them out when you leave it out. For an `fs.ReadStream`, it reads the size from the filesystem without loading the file into memory.

A `file` is limited to 100 MB. Send a larger PDF or TIFF by `fileUrl`. See [Files and limits](https://docs.runpulse.com/v2/files).

### Request and response types

Every request and response type is exported under the `Pulse` namespace:

```ts
import { Pulse } from "@pulse-software/sdk";

const config: Pulse.ParseConfig = { model: "ultra-2" };
```

Members are camelCase, such as `fileUrl` and `parseId`. The SDK sends and reads the API's snake_case names for you. Free-form values keep their keys as written, such as the property names in an `inputSchema` and the values in `extraction.enriched`.

### Handling errors

A failed request throws a subclass of `PulseError`, such as `Pulse.BadRequestError` or `Pulse.NotFoundError`. For a status the API documents, `body` is the error's [problem details](https://docs.runpulse.com/v2/errors), typed as `Pulse.Problem`:

```ts
import { Pulse, PulseError } from "@pulse-software/sdk";

try {
  await client.parse.getResult({ parseId });
} catch (err) {
  if (err instanceof Pulse.GoneError) {
    console.log(err.body.code); // such as "RESULT_EXPIRED"
  }
  if (err instanceof PulseError) {
    console.log(err.statusCode);
    console.log(err.requestId); // quote it to support
    console.log(err.body);
    console.log(err.rawResponse);
  }
  throw err;
}
```

Branch on the problem's `code`, never on `title` or `detail`. [Error codes](https://docs.runpulse.com/errors) lists every code and what to do about it.

A status the API doesn't document, such as a `502` from a proxy, throws a plain `PulseError` with the body as it arrived. A timeout throws `PulseTimeoutError`.

### Retries

The SDK never retries a request. The `maxRetries` option has no effect.

Reads are safe to retry: a status or result read never starts a job or costs credits. A `run` is not. When a `run` fails with a `5xx` or times out, Pulse may already have started the job, and a second `run` starts a second, billed job. [Errors and retries](https://docs.runpulse.com/v2/errors#retry-without-starting-a-job-twice) shows how to retry each case safely.

### Timeouts

Calls have no timeout by default, so a call without `async` waits until its job ends or the connection closes. To set one, in seconds:

```ts
const client = new PulseClient({
  apiKey: process.env.PULSE_API_KEY!,
  timeoutInSeconds: 120, // every call
});

await client.parse.get({ parseId }, { timeoutInSeconds: 10 }); // one call
```

### Aborting requests

Pass an `AbortSignal` to cancel a request in flight:

```ts
const controller = new AbortController();
const status = client.parse.get({ parseId }, { abortSignal: controller.signal });
controller.abort();
```

Aborting a `run` drops the connection, not the job. Cancel the job with `cancel`.

### Raw responses

`.withRawResponse()` returns the parsed body as `data` and the HTTP response as `rawResponse`. Use it to read headers, such as the `Link` header on a page of a batch's manifest:

```ts
const { data, rawResponse } = await client.parse.batch.getResult({ batchId }).withRawResponse();

console.log(rawResponse.headers.get("Link"));
```

### Additional headers and query parameters

```ts
const client = new PulseClient({
  apiKey: process.env.PULSE_API_KEY!,
  headers: { "X-Custom-Header": "custom value" }, // every call
});

await client.parse.get(
  { parseId },
  {
    headers: { "X-Custom-Header": "custom value" }, // one call
    queryParams: { customQueryParamKey: "custom query param value" },
  },
);
```

### Logging

Logging is off by default. To turn it on:

```ts
import { PulseClient, logging } from "@pulse-software/sdk";

const client = new PulseClient({
  apiKey: process.env.PULSE_API_KEY!,
  logging: {
    level: logging.LogLevel.Debug, // defaults to logging.LogLevel.Info
    logger: new logging.ConsoleLogger(), // defaults to ConsoleLogger
    silent: false, // defaults to true
  },
});
```

To use your own logger, pass an object that implements `logging.ILogger`:

```ts
import pino from "pino";

const pinoLogger = pino();

const logger: logging.ILogger = {
  debug: (msg, ...args) => pinoLogger.debug(args, msg),
  info: (msg, ...args) => pinoLogger.info(args, msg),
  warn: (msg, ...args) => pinoLogger.warn(args, msg),
  error: (msg, ...args) => pinoLogger.error(args, msg),
};
```

### Custom fetch

The SDK uses the runtime's `fetch`. To use another implementation, such as in a runtime without one:

```ts
const client = new PulseClient({
  apiKey: process.env.PULSE_API_KEY!,
  fetch: myFetch,
});
```

## Moving from 1.x

`@pulse-software/sdk` replaces `pulse-ts-sdk`. It calls API version 2, where two endpoints change names: version 1's `/extract` is version 2's `/parse`, and version 1's `/schema` is version 2's `/extract`.

| 1.x (`pulse-ts-sdk`) | 2.x (`@pulse-software/sdk`) |
| --- | --- |
| `client.extract(...)` | `client.parse.run(...)`, then `client.parse.getResult({ parseId })` |
| `client.extractAsync(...)` | `client.parse.run({ ..., async: true })` |
| `client.jobs.getJob(...)` | `client.parse.get({ parseId })`, or the `get` of the job's own endpoint |
| `client.schema(...)` | `client.extract.run({ parseId, config })` |
| `client.split(...)`, `client.tables(...)` | `client.split.run({ parseId, config })`, and the same for `tables` |
| `client.batch.extract(...)` | `client.parse.batch.run(...)` |
| `client.batch.schema(...)`, `client.batch.split(...)`, `client.batch.tables(...)` | None: run the step on each document's parse |
| `client.pipeline.execute(...)` | `client.pipeline.run(...)` |
| `client.webhooks.createWebhookLink()` | `client.webhook.create(...)` |
| `client.form`, `client.results`, `client.largeResults` | None: these stay on version 1 |

Version 2 also changes what a call returns: a `run` returns the job's id, and you read the result with `getResult`. [Moving from V1](https://docs.runpulse.com/v2/moving-from-v1) maps every option.

<!-- prettier-ignore -->
> [!WARNING]
> Keep your organization's default API version at 1 while any code still uses `pulse-ts-sdk`. The 1.x SDK sends no `Pulse-Version` header, so with the default at 2, its calls reach version 2 and fail.

## Requirements

The following runtimes are supported:

- Node.js 18 or later.
- Deno v1.25 or later.
- Bun 1.0 or later.
- Cloudflare Workers.
- Vercel.
- React Native.

The client sends your API key on every request. Call Pulse from a server, not from a browser.

## Contributing

This library is generated from the Pulse API's OpenAPI document. A change made directly to the code here is overwritten by the next release. Open an issue first, or a PR as a proof of concept, and we'll move the change into the generator.

Changes to this README are welcome: it's maintained by hand.
