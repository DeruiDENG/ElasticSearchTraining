# Elasticsearch 101

Warning:
This training material has not really been designed for self guidance.
It assumes an instructor will verbally explain a lot of the material.

## Topics

- Hello World
- Manage index
- Indexing/putting documents 
- Understand mappings
- Text analysis(Analyzers)
- Queries
    - Term query
    - Match query
    - Match phrase query
    - Range query
    - Bool query
    - Sort the result
- Others advance stuff preview

## Prerequisites

You need to install various software tools.

Requirements:

- Docker (if on OSX, Docker for Mac is recommended)
- docker-compose


## Notes

There are scripts in the `scripts` directory that use docker-compose to create, stop and destroy an Elasticsearch + Kibana environment.

If you have previously run a different version of Elasticsearch with these scripts,
especially anything before version 7.10.2
then it may be best to destroy your existing Elasticsearch data with `scripts/destroy`.

Create an environment with:
```bash
scripts/up
```

Elasticsearch should now be available on `http://localhost:9200`

Kibana should now be available on `http://localhost:5601`

Stop the environment with:
```bash
scripts/down
```
Data is persisted so a subsequent `scripts/up` will start up ES and Kibana with your data still there.

Cleanup the environment and delete all data with:
```bash
scripts/destroy
```
