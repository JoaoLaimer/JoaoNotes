# Indexing Documents
## Indexing Documents
Indexing is the action of adding new documents to the Elasticsearch index (optimized collection of documents). This can be done using basic operations using REST APIs.
To create an index, you can send a POST request that specifies: index name, resource/endpoint and document.
Example using curl:
```shell 
curl -X POST "localhost:9200/my_blogs/_doc" -H 'Content-Type: application/json' -d '
{
	"title": "Doing Something with Thing",
	"category": "Engineering",
	"author": {
		"first_name": "John",
		"last_name": "Doe"
	}
}'
```
- `my_blogs` - The index name.
- `_doc` - The endpoint.
By default, Elasticsearch generates the ID for you. 
To use your own IDs or update an index use PUT request. When updating an index the `_version` field is incremented by 1.
You can also use the `Dev Tools > Console`, to index documents.
## Retrieving a Document
Use the GET API with the document's unique ID.
Example: `GET my_blogs/_doc/<id>`.
## Creating a Document
Indexing and creating documents is two different operations on Elasticsearch. Creating a document means exclusively creating the document, where indexing can be used for updating if the document already exists.
To index a new JSON document with the `_create` resource, it guarantees that the document is only indexed if it does not already exist and cannot be used to update an existing document.
Example: `POST my_blogs/_create/<id> <body>`
## Updating a Document
Like creating, updating is also used for a exclusive function.
We use the `_update` resource  to modify specific field in a document and add the `doc` context.
Example: 
```
POST my_blogs/_update/4
{
	"doc": {
		"category": "Fiction"
	}
}
```
When the operation is done, the `_version` field is incremented by 1.

## Deleting a Document
Use the DELETE request to delete an indexed document, making sure to specify the ID.
Example: `DELETE my_blogs/_doc/4` 

## Bulk API
To index many documents in a single API call we can use the `_bulk` resource. We are able to use four action simultaneously: **create, index, update and delete**. 
The response can indicate single action failures that does not affect the remaining actions.
To create a request, we use Newline Delimited JSON (NDJSON) structure, where the whole document is in a single line, and other documents are separated by new lines.
Example: 
```
POST comments/_bulk
{"index" : {}}
{"title": "Comment 1", "category": "Examples"}
{"index" : {"_id": 4}}
{"title": "Comment 4", "category": "Examples"}
{"create" : {"_id": 5}}
{"title": "Comment 5", "category": "Examples"}
{"update" : {"_id": 2}}
{"doc": {"title": "Comment 2"}}
{"delete" : {"_id": 1}}
```

#### Upload a File in [[Kibana]]
You can quickly upload a log file or delimited CSV, TSV, or JSON File. It should be used for initial exploration of your data and not intended as part of production process.

# Searching Data
## Query Languages

| Use Case                                                    | Language                            |
| ----------------------------------------------------------- | ----------------------------------- |
| Used in Kibana query bar.                                   | **KQL**<br>**Lucene**<br>**ES\|QL** |
| Gives access to all ElasticSearch option.<br>Most Flexible. | **Query DSL**                       |
| Search indices using the familiar SQL syntax.               | **ElasticSearch SQL**               |
| For security data, threat hunting.                          | **EQL**                             |
## Basic Structure of Search
In ElasticSearch, search breaks down into two basic parts:
 - **Queries** - "Which **documents** meet a specific set of criteria?";
 - **Aggregations** - "Tell me something about a **group of documents**.";



## Elasticsearch Query Languages (ES|QL)
A piped query language that delivers advanced search capabilities, bringing together the capabilities of multiple languages.
Composed by a series of commands chained together by pipes.
`source-command | processing-command 1| processing-command n | ...`
- **Source** commands retrieve or generate data in the form of tables.
- **Processing** commands take a table as input and produces a table as output.
To run an ES|QL Query we can use a POST request to the query API, wrapping the query like so:
```
POST /_query
{
	"query": "FROM blogs | KEEP publish_data, authors.full_name | SORT (publish_date)"
}
```
Obs: Triple quotes support multi-line requests.
We can use the format option to retrieve the results in alternative formats (csv, json, tsv, txt, yaml, cbor and smile): 
`POST /_query?format=csv

## Strings 
When searching for specific strings within the documents, the search string is case-insensitive and queries like `"content": "united states"` and `"content":"United States"` return the same hits. This is also due to the process called **text analysis** which breaks a string into tokens and lower cases it.
The text strings are analyzed in query time and index time.
### Analyzers
There are many built-in analyzers included in Elasticsearch (white-space, stop, patterns, simple, language-specific analyzers, and more) and each one has it's own function and you can also define your own custom analyzers.

An analyzer consists of three parts:
- zero or more character filters. Enable to pre-process the string.
- exactly one tokenizer.
- zero or more token filters. Post-process the tokens.

The standard analyzer has no character filters, uses the standard tokenizer, lower cases all tokens, and optionally removes stop words.

To test an analyzer we can use the `_analyze` API, to see what it does to the text:
```json
GET _analyze
{
	"analyzer": "english",
	"text": "Some text in english"
}
```
**Keyword vs. text** 
Elasticsearch has two kinds of strings:
- **Keywords** are for aggregations, sorting and exact searches and are not analyzed.
- **Text** is for full-text search and is analyzed.
## Query DSL
To use Query DSL we can use the search API: 
`GET <index>/_search`
### match_all
Most common query, it returns every document which is hit the search.
This is the default request for the search API.
Example: 
Request: `GET blogs/_search` (no need for body).
Response:
```JSON 
{
	"took": 1,
	"timed_out": false,
	"_shards": {...},
	"hits": {
		"total": {...},
		"max_score": 1,
		"hits": [...]
	}
}
```
Where: 
- **took** - the number of milliseconds Elasticserach took to process the query.
- **total** - the number of documents that matched this query.
- **hits** - array containing the documents that hit the search criteria.
OBS: ElasticSearch returns 10 documents by default, this can be changed by the admin.
### match Query
by default uses "or" logic if multiple terms appear in the search query and is case-insensitive.
The "operator" parameter inside the "match field", can be changed to "and".
We can use the "minimum_should_match" parameter to specifies the minimum number of clauses that must match.
The order of terms doesn't matter and how far apart the terms are.
### match_phrase Query
Searches for the exact sequence of terms specified in the query.
The "slop" parameter specifies how far apart the terms are.

### multi_match Query
To query multiple fields using the comma-delimited list using square brackets [].
- The "type" parameter can be set to "most_fields" to let the score be the sum of the scores of the individual fields instead (the more fields contain the word, the higher the score.
- The "type" parameter can also be set to "phrase".
### Score
Calculate a **score** for each document hit. 
- Uses the **BM25** scoring algorithm, determines a document's score using, **TF (Term Frequency)**, **IDF (inverse document frequency)**, **field length** (shorter is better).

### Term-level Queries
Find documents based on precise values in structured data.
### "term" 
Use the keyword field to match on an exact term (including capitalization and whitespaces). Keywords are commonly used for structured content.
### "range"
To search for dates, numbers and ids.
Use the following parameters to specify a range:
- **gt**, **gte**, **lt**, **lte**
Date math.
### "exists"
Returns documents that contain an indexed value for a field.
### Async Search
Will respond with a search Id instead of the search, using the `_async_search` API.
You can set a time using the parameter `?wait_for_completion_timeout=`.
The body is identical to a regular `_search`.
#### Retrieve the results
Use the id to retrieve search results: `GET /_asyn_search/<id>`

### Combining Queries
### Bool Query
The "bool" query combines one or more boolean clauses:
- must
- filter
- must_not
- should
Each of the clauses is optional, clauses can be combined, any clause accepts one or more queries. 
#### "must"
Any query in a must clause must match for a document to be hit, each query contributes to the score.
#### "filter"
Any query has to match for a document to be a hit. But does not contribute ot the score.
Great for yes/no type queries.
#### "must_not"
Exclude documents that match a query. Do not contribute to the score.
#### "should"
To boost documents that match a query.  Contribute to the score, documents that do not match the queries in **should** are returned as hits too.
Use **minimum_should_match** to specify the number or percentage of should clauses returned.
### Changing Response
Set "from" and "size" to paginate through the search results, set "sort" to sort on one or more fields instead of the "`_score`".
## Mapping
Is a per-index schema definition that contains name of fields, data types of fields and how the field should be indexed and stored.
Elasticsearch will index any document without knowing its details (number of fields, their data types, etc.) and will assigns data types to fields in a mapping.

Simple Types:
- **text**: for full-text (analyzed) strings
- **keyword**: for exact value strings and aggregations
- **date and date-nanos**: strings formatted as dates, or numeric dates.
- **numbers**: byte, short, integer, long, float, double, half_float
- **boolean**
- **geo** types
Hierarchical types: like **object** and **nested**

#### Defining a Mapping
In many cases, you will need to define your own mapping. Mapping are defined in the **mappings** section of an index
```json
PUT my_index
{
	"mappings": {
		//define mappings here
	}
}
```

- When you index a document with unmapped fields, Elasticsearch dynamically creates the mapping for those fields.

You can see any mapping of a index using the `_mapping` endpoint.
#### Multi-Fields
When Elasticsearch sees text in a document it doesn't know if it should be a *text* or a *keyword* so it gives both by default.
Example:  
- _country_name_ is a text.
- _country_name.keyword_ is the keyword version.

Indexing every string twice slows down indexing and takes more disk space, so you should optimize the mapping
#### Mapping Optimization
Dynamic mapping is rarely optimal. A integer may be saved as a long while it should be a short.
You can't change a mapping without reindexing your documents.
Is best to create a good mapping after going to production.

To fix a mapping create a new index with the optimized mapping, then use the reindex API to copy data of the old index to the new one.

```json
POST _reindex
{
	"source": {
		"index": "blogs"
	},
	"dest": {
		"index": "blogs_v2"
	}
}
```
Using Kibana's file uploader allows you to customize data mappings after indexing.

### Types and Parameters
In addition to the type, fields in a mapping can be configured with additional parameters, for example to set a analyzer for a text field.

**Date formats** can be specified using the format field: `"format": "dd/MM/yyy || epoch_millis"`

Elasticsearch attempts to **coerce** data to match the data type of the field.
You can disable coercion on the mapping definition.

By default, Elasticsearch creates a **doc values** data structure for many fields during indexing, enabling aggregation/sorting on these fields. This too, can be disabled.

You can choose **not to index a field** which trades fast querying for less disk space usage.

A field that won't be used at all and should be stored in `_source` can be disabled.

#### Dynamic Templates
Using dynamic templates to define a fields's mapping based on one of the following:
- the field's data type.
- the name of the field.
- the path to the field.
Example: 
- Map any string field with a name that starts with "ip*" as type IP:
```json
PUT my_index
{
	"mappings": {
		"dynamic_templates": [
		{
			"strings_as_ip": {
				"match_mapping_type": "string",
				"match": "ip*",
				"mapping": {
					"type": "ip"
				}
			} 
		}
		]
	}
}
```
```json
POST my_index/_doc
{
	"ip_address": "157.97.192.70"
}
GET my_index/_mapping
//reponse
"properties": {
	"ip_address":{
		"type": "ip"
	}
}
```

## Aggregations
Summarizes your data as metrics, statistics, or other analytics and results are typically computed values that can be grouped.

| Aggregation | Capability                                                                    |
| ----------- | ----------------------------------------------------------------------------- |
| Metric      | calculate metrics, such as a sum or average, from field values                |
| Bucket      | group documents into buckets based on field values, ranges, or other criteria |
| Pipeline    | take input from other aggregation instead of documents or fields              |
### Basic Structure of Aggregations
```json
GET blogs/_search
{
	"aggs": {
		"my_agg_name": {
			"AGG_TYPE": {
				...
			}
		}
	}
}
```
Aggregation results are in the response's "aggregation" object.
To return only aggregations results, set "size" to 0. Faster responses and smaller payload.

### Metrics Aggregations
Compute numeric values based on your dataset:
- count, avg, sum, min, max, median, cardinality.
- stats, percentiles, percentile_ranks.
### Bucket Aggregations
Categorize documents according to certain criterion

| Bucket By   | Aggregation                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| Time Period | - Date Range<br>- `date_histogram`:<br>`calendar_interval`<br>`fixed_interval`<br> |
| Numerics    | - Range<br>- Histogram                                                             |
| Keyword     | - Terms<br>- Significant Terms                                                     |
| IP Address  | IPV4 Range                                                                         |

#### date_histogram
`calendar_interval`:
- calendar unit name such as day, month or year.
`fixed_interval`:
- SI unit name such as seconds, minutes, hours, or days.
#### histogram
Using `"field"`s specifying `"interval"`.
#### sorting
```json
...
{
	"order":{
		"_key": "desc"
	}
}
```

`_count` in order for terms.
`_key` for histogram and date_histogram.

#### terms
Dynamically create a new bucket for every unique term of a specified **field**.
```json
...
{
	"terms": {
		"field": "authors.job_title.keyword",
		"size": 5
	}
}
```

### Combine aggregations

Specify different aggregations in a single request.
#### Reducing Scope
Combine with a query to reduce the scope.
#### Run Multiple Aggregations
You can specify multiple aggregations in the same request.
#### Sub-Aggregations
Embed aggregations inside other aggregations, no depth limit for nesting sub-aggregations.
```json
...
{
	"aggs": {
		...
		"aggs": {
		...
		}
	}
}
```
#### Pipeline Aggregation
Work on output produced from other aggregations.

## Transforms
Summarize existing Elasticsearch indices using aggregation to create more efficient datasets.
- Continuous Mode: transforms run continuously, processing new data as it arrives
- Retention Policy: identify and manage out-of-date documents in the destination index.
- Checkpoints: created each time new source data is ingested and transformed.
- Frequency: advanced option to set the interval between checkpoints (max 1 hour).
### Destination Index
Pre-create the destination index with custom setting for performance:
- use the Preview transform API to review `generated_dest-index`.
- disable `_source` to reduce storage usage
- use index sorting if grouping by multiple fields.
#### Latest Transforms
Use Latest transforms to copy the most recent documents into a new index.
