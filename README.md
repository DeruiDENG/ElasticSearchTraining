# Elasticsearch 101

Warning:
This training material has not really been designed for self guidance.
It assumes an instructor will verbally explain a lot of the material.

## Topics

- Hello World
- Manage index
- Indexing/putting documents 
- Understand mappings
- Queries
    - Term query
    - Match query
    - Range query
    - Bool query
    - Sort the result
- Summary

## Prerequisites

You need to install various software tools.

Requirements:

- Docker (if on OSX, Docker for Mac is recommended)
- docker-compose


## Notes
Create an environment with:
```bash
docker-compose up
```

Elasticsearch should now be available on `http://localhost:9200`

Kibana should now be available on `http://localhost:5601`

Stop the environment with:
```bash
cmd+c
```
or

```bash
docker-compose down
```


Cleanup the environment and delete all data with:
```bash
docker-compose down --volumes --remove-orphans
```
