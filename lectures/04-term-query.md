# Term-level query

You can use term-level queries to find documents based on `precise` values in structured data. Examples of structured data include date ranges, IP addresses, prices, or product IDs.

In short, `Term-level query is Exact-match query.`

```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","yearOfBirth":1968,"gender":"male","address":"55 Station St, Fitzroy, VIC 3065"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","yearOfBirth":1974,"gender":"male","address":"25 Smith St, Coburg, VIC 3058"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","yearOfBirth":1983,"gender":"female","address":"25 Smith St, Brunswick, VIC 3056"}

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
