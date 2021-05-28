# Sort

```text
DELETE /listing

PUT /listing

# Put multiple documents into elastic search in one shot
POST /listing/_bulk
{"index":{}}
{"price":13,"year":2018,"title":"18 Madge, Taman U-Thant, Ampang Hilir"}
{"index":{}}
{"price":15,"year":2018,"title":"Nobleton Crest, Taman U-Thant, Ampang Hilir"}
{"index":{}}
{"price":15,"year":2010,"title":"Taman Sri Ukay, Ampang"}
{"index":{}}
{"price":20,"year":2010,"title":"Taman Sri Ukay, Ampang"}
{"index":{}}
{"price":25,"year":2010,"title":"Taman Sri Ukay, Ampang"}
{"index":{}}
{"price":16,"year":2010,"title":"Taman Sri Ukay, Ampang"}

# Default sort
GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Ampang Crest",
        "operator": "or"
      }
    }
  }
}

# Sort by year
GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Ampang Crest",
        "operator": "or"
      }
    }
  },
  "sort": [
    {
      "year": {
        "order": "desc"
      }
    }
  ]
}

# Sort by multiple factors
# Sort by year, then by price
GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Ampang Crest",
        "operator": "or"
      }
    }
  },
  "sort": [
    {
      "year": {
        "order": "desc"
      }
    },
    {
      "price": {
        "order": "desc"
      }
    }
  ]
}

# Pagination using `from` and `size`
GET /listing/_search
{
  "from": 0,
  "size": 2, 
  "query": {
    "match": {
      "title": {
        "query": "Ampang Crest",
        "operator": "or"
      }
    }
  },
  "sort": [
    {
      "year": {
        "order": "desc"
      }
    },
    {
      "price": {
        "order": "desc"
      }
    }
  ]
}
```
