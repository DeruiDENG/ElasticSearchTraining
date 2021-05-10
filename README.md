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
    - Sorting of query results
- Summary

## Before the workshop

To make the workshop run more smoothly, please follow the steps before you attend the workshop:
* Install Docker following the instruction in https://docs.docker.com/engine/install/ (if they are not in your machine). Make sure `docker` and `docker-compose` commands are available in your terminal
* Clone the repo to your local machine from this url: https://git.realestate.com.au/asia-workshops/elastic-search-workshop-101
* In your terminal, go to the repo's root folder and run `docker-compose pull`. This will pull all the images needed by the workshop.

## Useful commands
### Start the server
Create an environment with:
```bash
docker-compose up
```

Elasticsearch should now be available on `http://localhost:9200`

Kibana should now be available on `http://localhost:5601`


### Stop the server
Stop the environment with:
```bash
cmd+c
```
or

```bash
docker-compose down
```

### Cleanup the server
Cleanup the environment and delete all data with:
```bash
docker-compose down --volumes --remove-orphans
```
