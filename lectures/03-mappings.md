# Mappings

Define how a document and its fields are indexed

* Which string should be tokenized or treated as keywords
* Field data types (e.g number, dates, geolocations)
* How text field should be analyzed
* etc

Two types:

* Dynamic mappings
* Explicit mappings

## Dynamic mappings

* Allows for indexing documents without previously defining the mappings
* New fields will be added by indexing new documents
* ElasticSearch will `guess` the mapping for the document

```text
DELETE /listing
PUT /listing

# Index JSON document
POST /listing/_doc
{
  "address": "1 Church St, Richmond",
  "postedDate": "16 Mar 2021",
  "Storey": 3
}

POST /listing/_doc
{
  "address": "1 Churches St, Blakeview",
  "postedDate": "12 Mar 2020",
  "Storey": 2
}

# Get dynamic mappings
GET /listing/_mapping

# Get mapping for specific field
GET /listing/_mapping/field/Storey

# Mapping will be updated when new documents are added
POST /listing/_doc
{
  "address": "1 Churches St, Blakeview",
  "postedDate": "12 Mar 2020",
  "Storey": 2,
  "ReferenceNumber": 101727193
}

GET /listing/_mapping

```
## Explicit mappings

Explicit mapping allows you to precisely choose how to define the mapping definition, such as:
* Which string fields should be treated as full text fields.
* Which fields contain numbers, dates, or geolocations.
* The format of date values.
* Custom rules to control the mapping for dynamically added fields.

https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html

```text
DELETE /listing

PUT /listing

# Specify the mapping
PUT /listing/_mapping
{
  "properties": {
    "address": {
      "type": "text"
    },
    "postedDate": {
      "type": "date"
    },
    "Storey": {
      "type": "long"
    }
  }
}

# Get the current mapping
GET /listing/_mapping

# Get the mapping of specified field
GET /listing/_mapping/field/postedDate

# Index a document
POST /listing/_doc
{
  "address": "1 Churches St, Blakeview",
  "postedDate": "2015-01-01",
  "Storey": 2,
  "ReferenceNumber": 101727193
}

GET /listing/_mapping

# Add a field to existing mapping
// Double check
PUT /listing/_mapping
{
  "properties": {
    "ReferenceNumber": {
      "type": "text"
    }
  }
}

GET /listing/_mapping

# Update the mapping of a field. (Will not work)
PUT /listing/_mapping
{
  "properties": {
    "ReferenceNumber": {
      "type": "text"
    }
  }
}

# Multi-field mapping:
# Add a mutli-field mapping
PUT /listing/_mapping
{
  "properties": {
    "ReferenceNumber": {
      "type":"long",
      "fields": {
        "english": {
          "type": "text"
        },
        "raw": {
          "type":"keyword"
        }
      }
    }
  }
}

// example of query

```
