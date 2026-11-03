# Reference
## Parse
<details><summary><code>client.parse.<a href="/src/api/resources/parse/client/Client.ts">run</a>({ ...params }) -> Pulse.ParseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Parse a document into Markdown and elements, each with its page and position. Send a `file` or a `file_url`, with `config` or a saved `config_id`. A parse costs 1 credit per page. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the result at `GET /parse/{parse_id}/result`. Uploads are limited to 100 MB, so send a larger PDF or TIFF by `file_url`. The result's `failed_pages` lists any page that couldn't be parsed.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.run({});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunParseRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ParseClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.<a href="/src/api/resources/parse/client/Client.ts">get</a>({ ...params }) -> Pulse.ParseStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a parse's status. Once it is `completed`, read its result at `GET /parse/{parse_id}/result`. Anyone in your organization can read the status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.get({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetParseRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ParseClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.<a href="/src/api/resources/parse/client/Client.ts">cancel</a>({ ...params }) -> Pulse.ParseStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a parse that is still `queued` or `processing`. A canceled parse never completes and isn't charged, and anything it saved is deleted. Only the user who started it can cancel it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.cancel({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelParseRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ParseClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.<a href="/src/api/resources/parse/client/Client.ts">getResult</a>({ ...params }) -> Pulse.ParseResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a completed parse's Markdown, elements and requested outputs, with the pages and credits it used. Anyone in your organization can read it. If your organization's retention deletes a result the first time it's read, save the response, because a later read returns `410`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.getResult({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultParseRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ParseClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Classify
<details><summary><code>client.classify.<a href="/src/api/resources/classify/client/Client.ts">run</a>({ ...params }) -> Pulse.ClassifyResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sort a document into one of the categories you list in `config.classifications`. Send a `file` or a `file_url`, with `config` or a saved `config_id`. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the result at `GET /classify/{classify_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.run({});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunClassifyRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ClassifyClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.<a href="/src/api/resources/classify/client/Client.ts">get</a>({ ...params }) -> Pulse.ClassifyStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a classification's status. Once it is `completed`, read its result at `GET /classify/{classify_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.get({
    classifyId: "classify_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetClassifyRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ClassifyClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.<a href="/src/api/resources/classify/client/Client.ts">cancel</a>({ ...params }) -> Pulse.ClassifyStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a classification that is still `queued` or `processing`. Only the user who started it can cancel it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.cancel({
    classifyId: "classify_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelClassifyRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ClassifyClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.<a href="/src/api/resources/classify/client/Client.ts">getResult</a>({ ...params }) -> Pulse.ClassifyResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a completed classification's category and confidence, with the credits it used.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.getResult({
    classifyId: "classify_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultClassifyRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ClassifyClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Extract
<details><summary><code>client.extract.<a href="/src/api/resources/extract/client/Client.ts">run</a>({ ...params }) -> Pulse.ExtractResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Fill in your JSON Schema with data from a completed parse. Send the parse's `parse_id` with `config` or a saved `config_id`. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the data at `GET /extract/{extract_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.run({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunExtractRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ExtractClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.<a href="/src/api/resources/extract/client/Client.ts">get</a>({ ...params }) -> Pulse.ExtractStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an extraction's status. Once it is `completed`, read its data at `GET /extract/{extract_id}/result`. Anyone in your organization can read the status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.get({
    extractId: "extract_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetExtractRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ExtractClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.<a href="/src/api/resources/extract/client/Client.ts">cancel</a>({ ...params }) -> Pulse.ExtractStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel an extraction that is still `queued` or `processing`. Only the user who started it can cancel it. For anyone else, the cancel returns `404`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.cancel({
    extractId: "extract_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelExtractRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ExtractClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.<a href="/src/api/resources/extract/client/Client.ts">getResult</a>({ ...params }) -> Pulse.ExtractResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a completed extraction's data in the formats `config.format` asked for, with the credits it used and the parse it read.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.getResult({
    extractId: "extract_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultExtractRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ExtractClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Split
<details><summary><code>client.split.<a href="/src/api/resources/split/client/Client.ts">run</a>({ ...params }) -> Pulse.SplitResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Find the pages of a completed parse that belong to each topic you name. A split reads the whole parse and costs 1 credit per page (6 with `effort: high`), however many topics you send. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the pages at `GET /split/{split_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.run({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunSplitRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `SplitClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.<a href="/src/api/resources/split/client/Client.ts">get</a>({ ...params }) -> Pulse.SplitStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a split's status. Once it is `completed`, read its pages at `GET /split/{split_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.get({
    splitId: "split_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetSplitRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `SplitClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.<a href="/src/api/resources/split/client/Client.ts">cancel</a>({ ...params }) -> Pulse.SplitStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a split that is still `queued` or `processing`. A canceled split never completes and isn't charged. Only the user who started it can cancel it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.cancel({
    splitId: "split_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelSplitRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `SplitClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.<a href="/src/api/resources/split/client/Client.ts">getResult</a>({ ...params }) -> Pulse.SplitResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the pages a completed split found for each topic, with the credits it used and the parse it read.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.getResult({
    splitId: "split_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultSplitRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `SplitClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tables
<details><summary><code>client.tables.<a href="/src/api/resources/tables/client/Client.ts">run</a>({ ...params }) -> Pulse.TableResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Merge a completed parse's tables across pages and return each in the formats you ask for. Send the parse's `parse_id` with `config` or a saved `config_id`. It costs 0.5 credits per table returned. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the tables at `GET /tables/{tables_id}/result`. Tables must be enabled for your organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.run({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunTablesRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `TablesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.<a href="/src/api/resources/tables/client/Client.ts">get</a>({ ...params }) -> Pulse.TableStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a tables job's status. Once it is `completed`, read its tables at `GET /tables/{tables_id}/result`. Anyone in your organization can read the status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.get({
    tablesId: "tables_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetTablesRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `TablesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.<a href="/src/api/resources/tables/client/Client.ts">cancel</a>({ ...params }) -> Pulse.TableStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a tables job that is still `queued` or `processing`. A canceled job never completes and isn't charged, and anything it saved is deleted. Only the user who started it can cancel it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.cancel({
    tablesId: "tables_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelTablesRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `TablesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.<a href="/src/api/resources/tables/client/Client.ts">getResult</a>({ ...params }) -> Pulse.TableResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a completed job's tables in the formats `config.format` asked for, with the credits it used. Anyone in your organization can read it. A `TABLE_ANALYSIS_SKIPPED`, `MERGE_NOT_VERIFIED` or `MERGE_FALLBACK` warning means some cross-page merges may be wrong, so check those tables.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.getResult({
    tablesId: "tables_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultTablesRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `TablesClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Charts
<details><summary><code>client.charts.<a href="/src/api/resources/charts/client/Client.ts">run</a>({ ...params }) -> Pulse.ChartsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Read every chart on the selected pages of a completed parse as data (type, axes, series and points), and build the export files you ask for. It costs 1 credit per chart read. By default, the call waits for the job to end. With `async: true`, it returns `202` at once. Read the charts and exports at `GET /charts/{charts_id}/result`. Charts must be enabled for your organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.run({
    parseId: "parse_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunChartsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ChartsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.<a href="/src/api/resources/charts/client/Client.ts">get</a>({ ...params }) -> Pulse.ChartsStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a charts job's status. Once it is `completed`, read its result at `GET /charts/{charts_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.get({
    chartsId: "charts_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetChartsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ChartsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.<a href="/src/api/resources/charts/client/Client.ts">cancel</a>({ ...params }) -> Pulse.ChartsStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a charts job that is still `queued` or `processing`. A canceled job isn't charged. Only the user who started it can cancel it. A job that has already ended returns `409`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.cancel({
    chartsId: "charts_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelChartsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ChartsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.<a href="/src/api/resources/charts/client/Client.ts">getResult</a>({ ...params }) -> Pulse.ChartsResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a completed job's charts, with each export file's full content in `exports`. To save a file, decode its `content_base64` and write it under its `filename`. If your organization's retention deletes a result the first time it's read, exports included, save the response, because a later read returns `410`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.getResult({
    chartsId: "charts_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultChartsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ChartsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Pipeline
<details><summary><code>client.pipeline.<a href="/src/api/resources/pipeline/client/Client.ts">run</a>({ ...params }) -> Pulse.PipelineResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Parse one document (`config.step`), then run up to 10 more steps on the parse once it completes (`config.children`). A pipeline always runs async. Read its status at `GET /pipeline/{pipeline_id}`, each step's status at `GET /pipeline/{pipeline_id}/result`, and a completed step's output at its own endpoint. Each step costs what its endpoint costs, and the pipeline adds nothing. The pipeline and its steps expire together, counted from the pipeline's end.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.run({});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RunPipelineRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `PipelineClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.<a href="/src/api/resources/pipeline/client/Client.ts">get</a>({ ...params }) -> Pulse.PipelineStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a pipeline's status. Each step's own status is at `GET /pipeline/{pipeline_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.get({
    pipelineId: "pipeline_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetPipelineRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `PipelineClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.<a href="/src/api/resources/pipeline/client/Client.ts">cancel</a>({ ...params }) -> Pulse.PipelineStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a pipeline that is still `queued` or `processing`, along with its unfinished steps. Those steps never complete and aren't charged. A step that already completed keeps its result. Only the user who started the pipeline can cancel it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.cancel({
    pipelineId: "pipeline_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CancelPipelineRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `PipelineClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.<a href="/src/api/resources/pipeline/client/Client.ts">getResult</a>({ ...params }) -> Pulse.PipelineResult</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get each step's current status. You can read it as soon as `POST /pipeline` returns, and after the pipeline ends or expires. It holds no step output, so read a completed step at its own endpoint, such as `GET /parse/{parse_id}/result`. `usage` totals the completed steps. Reading this doesn't count as reading a step's result. A step's result returns `410` once it has expired, or once it was read and your organization's retention deletes a result on its first read.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.getResult({
    pipelineId: "pipeline_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetResultPipelineRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `PipelineClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Usage
<details><summary><code>client.usage.<a href="/src/api/resources/usage/client/Client.ts">get</a>({ ...params }) -> Pulse.UsageResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the pages processed and credits used by your organization's jobs created in the window, with your plan's credit allowance. Calling this endpoint is free.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.usage.get();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetUsageRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `UsageClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Webhook
<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">list</a>() -> Pulse.WebhookListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's webhooks, newest first, without their secrets or header values.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">create</a>({ ...params }) -> Pulse.WebhookPostResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Add a webhook. Your organization can have up to 10. Pulse pings the new webhook at once, and the response says whether the ping got through. This is the only response that returns the signing `secret`. Jobs created 15 seconds or more after this call send each listed event, signed per Standard Webhooks and carrying only the job's id. A newer status replaces one not yet delivered. Failed deliveries are retried for about 35 hours, and a webhook that keeps failing is turned off.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.create({
    url: "url"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.CreateWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">get</a>({ ...params }) -> Pulse.WebhookResponseBase</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's webhooks, without its secret or header values.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.get({
    webhookId: "webhook_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.GetWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">delete</a>({ ...params }) -> Pulse.WebhookDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a webhook. Pulse sends it nothing more, including retries.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.delete({
    webhookId: "webhook_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.DeleteWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">update</a>({ ...params }) -> Pulse.WebhookResponseBase</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Change a webhook. Each field you send replaces its current value. You can't change the URL, so create another webhook instead. Turning the webhook back on with `enabled: true` clears `disabled_reason`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.update({
    webhookId: "webhook_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.UpdateWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">rotate</a>({ ...params }) -> Pulse.WebhookRotateResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generate a new signing secret, which only this response returns. For 24 hours, deliveries are signed with both the new and the previous secret. Rotating again within that time retires the oldest secret at once.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.rotate({
    webhookId: "webhook_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.RotateWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhook.<a href="/src/api/resources/webhook/client/Client.ts">ping</a>({ ...params }) -> Pulse.WebhookPingResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Send the webhook a signed `webhook.ping` and report whether it got through within 15 seconds. A ping doesn't count toward the webhook's failures. You can ping each URL 10 times per hour, and your organization's webhooks 30 times per hour in all.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.webhook.ping({
    webhookId: "webhook_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.PingWebhookRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `WebhookClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Charts Configs
<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">list</a>() -> Pulse.ChartsConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/charts` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.ChartsConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /charts` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.create({
    name: "name",
    config: {}
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.charts.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/charts` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.ChartsConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/charts` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.charts.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.charts.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.charts.configs.<a href="/src/api/resources/charts/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.ChartsConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.charts.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.charts.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Classify Configs
<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">list</a>() -> Pulse.ClassifyConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/classify` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.ClassifyConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /classify` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.create({
    name: "name",
    config: {
        classifications: [{
                name: "name"
            }]
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.classify.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/classify` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.ClassifyConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/classify` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.classify.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.classify.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.classify.configs.<a href="/src/api/resources/classify/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.ClassifyConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.classify.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.classify.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Extract Configs
<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">list</a>() -> Pulse.ExtractConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/extract` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.ExtractConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /extract` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.create({
    name: "name",
    config: {
        inputSchema: {
            "key": "value"
        }
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.extract.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/extract` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.ExtractConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/extract` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.extract.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.extract.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.extract.configs.<a href="/src/api/resources/extract/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.ExtractConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.extract.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.extract.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Parse Configs
<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">list</a>() -> Pulse.ParseConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/parse` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.ParseConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /parse` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.create({
    name: "name",
    config: {
        model: "ultra-2"
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/parse` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.ParseConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/parse` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.configs.<a href="/src/api/resources/parse/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.ParseConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Parse Batch
<details><summary><code>client.parse.batch.<a href="/src/api/resources/parse/resources/batch/client/Client.ts">run</a>({ ...params }) -> Pulse.ParseBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Parse up to 1,000 documents with one config. Send them as `files`, as `file_urls`, or as a public `folder_url` in Amazon S3, Google Cloud Storage or Azure Blob Storage. Each document becomes its own `/parse` job, checked against your plan and billed when it runs. A job that fails doesn't stop the others. Uploaded or listed files of an unsupported type are skipped. A batch always runs async. Read its status at `GET /parse/batch/{batch_id}` and its manifest at `GET /parse/batch/{batch_id}/result`. A batch that isn't done in 48 hours fails.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.batch.run({});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.RunBatchRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `BatchClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.batch.<a href="/src/api/resources/parse/resources/batch/client/Client.ts">get</a>({ ...params }) -> Pulse.BatchStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a batch's status, with its documents counted by state. A batch ends `completed`, `failed` or `canceled` within 48 hours of being sent. Once it ends, read its manifest at `GET /parse/batch/{batch_id}/result`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.batch.get({
    batchId: "batch_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.GetBatchRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `BatchClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.batch.<a href="/src/api/resources/parse/resources/batch/client/Client.ts">cancel</a>({ ...params }) -> Pulse.BatchStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Cancel a batch that hasn't ended. The batch becomes `canceled` at once, and its unfinished jobs are canceled within seconds. A job that finishes first keeps its result, so `summary` and the manifest can change until every job has ended. Anyone in your organization can cancel a batch. A batch that has already ended returns `409`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.batch.cancel({
    batchId: "batch_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.CancelBatchRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `BatchClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.parse.batch.<a href="/src/api/resources/parse/resources/batch/client/Client.ts">getResult</a>({ ...params }) -> Pulse.ParseBatchEntry[]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the batch's manifest: one entry per ended job, in the order the jobs ended, each as `GET /parse/{parse_id}` returned it when the job ended. It's readable while the batch runs, and a job that isn't listed hasn't ended. Entries aren't updated, so read a job's own status for its `expires_at`. With `limit`, follow the `Link` header to the next page. While the batch runs, request the last page again later for new entries.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.parse.batch.getResult({
    batchId: "batch_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.parse.GetResultBatchRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `BatchClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Pipeline Configs
<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">list</a>() -> Pulse.PipelineConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/pipeline` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.PipelineConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /pipeline` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.create({
    name: "name",
    config: {
        step: {
            type: "parse",
            config: {
                model: "ultra-2"
            }
        }
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.pipeline.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/pipeline` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.PipelineConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/pipeline` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.pipeline.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.pipeline.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.pipeline.configs.<a href="/src/api/resources/pipeline/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.PipelineConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.pipeline.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.pipeline.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Settings Org
<details><summary><code>client.settings.org.<a href="/src/api/resources/settings/resources/org/client/Client.ts">get</a>() -> Pulse.OrgSettings</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get your organization's name, address and default API version, which is the version a request without a `Pulse-Version` header gets.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.settings.org.get();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `OrgClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.settings.org.<a href="/src/api/resources/settings/resources/org/client/Client.ts">update</a>({ ...params }) -> Pulse.OrgSettings</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Change your organization's settings. Only the fields you send change, and `{}` changes nothing. Only an organization admin can make changes. A new `default_api_version` takes effect within a minute.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.settings.org.update();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.settings.UpdateOrgRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `OrgClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Split Configs
<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">list</a>() -> Pulse.SplitConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/split` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.SplitConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /split` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.create({
    name: "name",
    config: {
        topics: [{
                name: "name"
            }]
    }
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.split.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/split` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.SplitConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/split` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.split.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.split.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.split.configs.<a href="/src/api/resources/split/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.SplitConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.split.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.split.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tables Configs
<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">list</a>() -> Pulse.TableConfigListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List your organization's saved `/tables` configs, newest first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.list();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">create</a>({ ...params }) -> Pulse.TableConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Save a config under a name. Later, send its `config_id` to `POST /tables` in place of `config`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.create({
    name: "name",
    config: {}
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.tables.CreateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">deleteAll</a>() -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete every `/tables` config your organization saved. Their ids are refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.deleteAll();

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">get</a>({ ...params }) -> Pulse.TableConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get one of your organization's saved `/tables` configs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.get({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.tables.GetConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">delete</a>({ ...params }) -> Pulse.ConfigDeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a saved config. Its id is refused afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.delete({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.tables.DeleteConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tables.configs.<a href="/src/api/resources/tables/resources/configs/client/Client.ts">update</a>({ ...params }) -> Pulse.TableConfigResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Rename a saved config, replace its whole config, or both. An empty body changes nothing.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.tables.configs.update({
    configId: "config_id"
});

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Pulse.tables.UpdateConfigsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**requestOptions:** `ConfigsClient.RequestOptions` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

