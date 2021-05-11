# Index

## What is ElasticSearch index?
An optimized collection of JSON documents. Each document is a collection of fields, the key-value pairs that contain your data.

An index is like a ‘database’ in a relational database.

## Index APIs
```text
# Create a new index
DELETE /listings

PUT /listings

# Index JSON document
POST /listings/_doc
{
  "address": "Lebuhraya Bandar Cassia, Batu Kawan, 14110, Penang"
}

POST /listings/_doc
{
  "address": "Persiaran Bayan Indah, Bayan Lepas, 11900, Penang"
}

POST /listings/_doc
{
  "address": "Desa ParkCity, Kuala Lumpur, Amelia Garden Homes, Desa ParkCity, 52000, Kuala Lumpur"
}

# List all the document
GET /listings/_search
{
    "query": {
        "match_all": {}
    }
}

# List document by ID
GET listings/_doc/{id}

# Query for document
GET /listings/_search
{
  "query": {
    "match": {
      "address": {
        "query": "Penang"
      }
    }
  }
}

# Delete a document by ID
DELETE listings/_doc/1

GET /listings/_search
{
    "query": {
        "match_all": {}
    }
}

# Delete a document by query
POST /listings/_delete_by_query
{
  "query":{
        "match": {
          "address": "Kuala Lumpur"
        }
  }
}

GET /listings/_search
{
    "query": {
        "match_all": {}
    }
}
```
