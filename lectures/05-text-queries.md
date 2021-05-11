# Text Queries
Full-text search in Elasticsearch

When putting a document to ES, Text analysis takes place to convert unstructured text, like the body of an email or a product description, into a structured format that’s optimized for search.

Use `match` query to perform full-text search.

```text
DELETE /listing

PUT /listing

PUT /listing/_mapping
{
  "properties": {
    "title": {
      "type": "text",
      "fields": {
        "english":{
          "type": "text",
          "analyzer": "english"
        }
      }
    },
    "price": {
      "type": "long"
    }
  }
}

# Put multiple documents into elastic search in one shot
POST /listing/_bulk
{ "index": {}}
{ "title": "3 Storey Townhouses (7 Units) in Teachers Village Quezon City", "price": 13 }
{ "index": {}}
{ "title": "2-Storey Townhouse for Sale in Filinvest Northview, QC", "price": 4.8 }
{ "index": {}}
{"title": "BSA Twin Towers Condo Unit near SM Megamall, ADB, La Salle, Poveda, Podium", "price": 18.5 }

GET /listing/_mapping

# Search for a word
GET /listing/_search
{
  "query": {
    "match": {
      "address": "Manila"
    }
  }
}

# Full-text search for word: townhouse
GET /listing/_search
{
  "query": {
    "match": {
      "title": "Townhouse"
    }
  }
}

# Will this work?
GET /listing/_search
{
  "query": {
    "match": {
      "title": "townhouse"
    }
  }
}

GET /listing/_search
{
  "query": {
    "match": {
      "title": "ownhouse"
    }
  }
}

# Use English analysizer to make ES understand English
# Query for townhouse should also include townhouses
GET /listing/_search
{
  "query": {
    "match": {
      "title.english": "townhouse"
    }
  }
}

GET /listing/_search
{
  "query": {
    "match": {
      "title.english": "townhouses"
    }
  }
}

# How analyzier work
GET _analyze
{
  "analyzer": "english",
  "text": "3 Storey Townhouses"
}

GET _analyze
{
  "analyzer": "english",
  "text": "3 Storey Townhouse"
}

# Search for word in multiple fields
GET /listing/_search
{
  "query": {
    "multi_match": {
      "query": "Quezon", 
      "fields": ["address","price"]
    }
  }
}

# Search for multiple words
GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Townhouse QC"
      }
    }
  }
}

GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Quezon QC",
        "operator": "or"
      }
    }
  }
}
```

