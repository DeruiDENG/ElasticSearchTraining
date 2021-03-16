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
# Create a new index
DELETE /listing
PUT /listings

# Index JSON document
POST /listings/_doc
{
  "address": "1 Church St, Richmond",
  "postedDate": "16 Mar 2021",
  "Storey": 3,
}

POST /listings/_doc
{
  "address": "1 Churches St, Blakeview"
  "postedDate": "12 Mar 2020",
  "Storey": 2,
}

# Get dynamic mappings
GET /listings/_mapping

# Get mapping for specific field
GET /listings/_mapping/field/Storey

# Mapping will be updated when new documents are added
POST /listings/_doc
{
  "address": "1 Churches St, Blakeview"
  "postedDate": "12 Mar 2020",
  "Storey": 2,
  "ReferenceNumber": 101727193
}

GET /listings/_mapping

```

## Explicit mappings
```text
DELETE /listing

PUT /listings

# Specify the mapping
PUT /listings/_mapping
{
  "properties": {
    "address": {
      "type": "text"
    },
    "postedDate": {
      "type": "date"
    }
    "Storey": {
      "type": "long"
    }
  }
}

POST /listings/_doc
{
  "address": "1 Churches St, Blakeview"
  "postedDate": "12 Mar 2020",
  "Storey": 2,
  "ReferenceNumber": 101727193
}

GET /listings/_mapping
```
