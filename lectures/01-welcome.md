# Welcome to Elasticsearch 101 workshop

## Setup

Start the Elasticsearch server:

```bash
docker-compose up -d
```

Wait a while. It will take quite a while for everything to start!


> Elasticsearch should now be available on http://localhost:9200
>
> Kibana should now be available on http://localhost:5601

## Demo

```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{ "index": {}}
{ "price" : 600, "propertyType" : "house",     "city" : "Kuching",    "sold" : "2017-10-28" }
{ "index": {}}
{ "price" : 800, "propertyType" : "house",     "city" : "Seremban",    "sold" : "2016-11-05" }
{ "index": {}}
{ "price" : 150, "propertyType" : "apartment", "city" : "Kuantan",  "sold" : "2017-05-18" }

GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}

```

## Introduction to the workshop

### Topics
- Manage index
- Indexing/putting documents
- Understand mappings
- Queries
    - Term query
    - Match query
    - Range query
    - Bool query
    - Sorting of query results
- Summary

### Structure
* Lecture
* Exercise
  * Split into rooms
  * Time-boxed
  * Solutions

