# Index

## What is ElasticSearch index?
An optimized collection of JSON documents. Each document is a collection of fields, the key-value pairs that contain your data.

An index is like a ‘database’ in a relational database.

## Index APIs

```text
# Create a new index
PUT /listings

# Index JSON document
POST /listings/_doc
{
  "address": "1 Church St, Richmond"
}

POST /listings/_doc
{
  "address": "2 Church St, Richmond"
}

POST /listings/_doc
{
  "address": "1 Churches St, Blakeview"
}

# List document
GET listings/_doc

GET listings/_doc/1

# Delete a document
DELETE listings/_doc/1

GET listings/_doc

# Query for a document
GET /listings/_search
{
  "query": {
    "match": {
      "address": {
        "query": "Churches"
      }
    }
  }
}

DELETE /listing

```
