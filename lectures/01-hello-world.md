
# Hello World

## Setup

Let's get your hand wet.

Create an environment with:
```bash
docker-compose up
```

Wait a while.  It will take quite a while for everything to start!


> Elasticsearch should now be available on http://localhost:9200
>
> Kibana should now be available on http://localhost:5601

## Demo
```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{ "index": {}}
{ "price" : 600, "propertyType" : "house",     "city" : "hobart",    "sold" : "2017-10-28" }
{ "index": {}}
{ "price" : 800, "propertyType" : "house",     "city" : "hobart",    "sold" : "2016-11-05" }
{ "index": {}}
{ "price" : 150, "propertyType" : "apartment", "city" : "brisbane",  "sold" : "2017-05-18" }

```

## Shutdown

Shutdown:

```
cmd+c
```
