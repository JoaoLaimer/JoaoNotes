Elastic Stack is the collection of different open source components linked together to help take data from any source and perform search, analyze and visualize data.

## Ingest
#### Beats
Beats is a host-based agent known as Data-shippers that is used to ship/transfer data from the endpoints to elasticsearch. Each beat is a single-purpose agent that sends specific data to the elasticsearch.
#### Logstash
Logstash is a data processing engine used to take the data from different sources, apply filter on it or normalize it, and then send it to the destination which could be Kibana or a listening port. 
Logstash config file:
- The **input** is where the user defines the source from which the data is being ingested. Logstash supports [plugins](https://www.elastic.co/guide/en/logstash/8.1/input-plugins.html).
- The **filter** part is where the user specifies the filter options to normalize the log ingested above. Logstash supports [filter plugins]([https://www.elastic.co/guide/en/logstash/8.1/filter-plugins.html](https://www.elastic.co/guide/en/logstash/8.1/filter-plugins.html)).
- The **output** part is where the user wants the filtered data to be send. Ir can be a listening port, Kibana interface, elasticsearch database, etc. Logstash supports [output plugins]([https://www.elastic.co/guide/en/logstash/8.1/output-plugins.html](https://www.elastic.co/guide/en/logstash/8.1/output-plugins.html)).
## Store
#### [[ElasticSearch]]
Elasticsearch is a full-text search and analytics engine used to store JSON-formatted documents. It is used to store, analyze, perform correlation on the data,etc. Elasticsearch supports RESTful API to interact with the data.
A **node** is an instance of Elasticsearch, a **cluster** is a collection of Elasticseach nodes.

## Visualize
#### [[Kibana]]
Kibana is a web-based data visualization that works with Elasticsearch to analyze, investigate and visualize the data stream in real-time. It provides **search** and **data visualization** capabilities for data in Elasticsearch.


**How they work together:**
Beats -> Logstash -> Elasticsearch -> Kibana

## Elastic Cloud
Elastic Stack managed through Elastic Cloud. It can be hosted on the cloud or serverless where projects are managed and automatically scaled by Elastic. The serverless approach provides different solutions for each use case:
- Elasticsearch Serverless
- Elastic Observability Serverless
- Elastic Security Serverless