# Mappings

When inserting a new document into the ES, ES will `index` the document to optimize for future queries.

Mapping defines how ES will index a document and its fields
E.g.
* Which field should be tokenized or treated as keywords
* Which field can be queried as number, dates, or geolocations
* How text field should be indexed and analyzed

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

POST /listing/_doc
{
  "address": "Jalan PJU 3 Tropicana Golf Country Resorts, Tropicana Indah Resort Homes , Petaling Jaya, 47410, Selangor",
  "postedDate": "2016-01-01",
  "Storey": 3,
  "ReferenceNumber": 123456
}

GET /listing/_mapping

# Add a field to existing mapping
PUT /listing/_mapping
{
  "properties": {
    "address": {
      "type": "keyword"
    }
  }
}

# Multi-field mapping:
# Add a multi-field mapping
POST /listing/_mapping
{
  "properties": {
    "address": {
      "type":"text",
      "fields": {
        "raw": {
          "type": "keyword"
        }
      }
    }
  }
}

GET /listing/_mapping

# Query by keyword
GET /listing/_search
{
  "query": {
    "term": {
      "address.raw": {
        "value": "1 Churches St, Blakeview"
      }
    }
  }
}


# After changing the mapping, to make it able for query, you have to do REINDEX
# Create a new index with correct mapping
PUT /new-listing

PUT /new-listing/_mapping
{
  "properties": {
    "address": {
      "type":"text",
      "fields": {
        "raw": {
          "type": "keyword"
        }
      }
    },
    "postedDate": {
      "type": "date"
    },
    "Storey": {
      "type": "long"
    }
  }
}

# Reindex the current index to the new index
POST _reindex
{
  "source": {
    "index": "listing"
  },
  "dest": {
    "index": "new-listing"
  }
}

GET /new-listing/_mapping

GET /new-listing/_search
{
  "query": {
    "match_all": {}
  }
}

# Query by keyword
GET /new-listing/_search
{
  "query": {
    "term": {
      "address.raw": {
        "value": "1 Churches St, Blakeview"
      }
    }
  }
}
```


## Other options
* Dynamic mapping with template
* Runtime fields
