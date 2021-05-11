# Term-level query

You can use term-level queries to find documents based on `precise` values in structured data. Examples of structured data include date ranges, IP addresses, prices, or product IDs.

In short, `Term-level query is Exact-match query.`

```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","yearOfBirth":1968,"gender":"male"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","yearOfBirth":1974,"gender":"male"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","yearOfBirth":1983,"gender":"female"}

# Search by a keyword
GET /users/_search
{
  "query": {
    "term": {
      "title": {
        "value": "Developer"
      }
    }
  }
}

GET /users/_search
{
  "query": {
    "term": {
      "title": {
        "value": "developer"
      }
    }
  }
}

GET /users/_mapping

# Query by keyword, the correct way
# Attention: term query cannot be used in the text field
GET /users/_search
{
  "query": {
    "term": {
      "title.keyword": {
        "value": "Developer"
      }
    }
  }
}

GET /users/_search
{
  "query": {
    "term": {
      "title.keyword": {
        "value": "developer"
      }
    }
  }
}

# Search by multiple keywords
GET /users/_search
{
  "query": {
    "terms": {
      "yearOfBirth": [
        "1974",
        "1983"
      ]
    }
  }
}
```
