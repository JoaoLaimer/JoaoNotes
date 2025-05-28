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

#### Upload a File in Kibana
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