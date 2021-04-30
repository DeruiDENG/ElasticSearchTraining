# Range query
Range query is another term-based query.
* Match the documents with the values in specific range
* Support the field types: numeric types, date types, keyword(with a condition)

```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","dob":"1968-01-10","height":183,"gender":"male","address":"55 Station St, Fitzroy, VIC 3065"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","dob":"1974-01-02","height":170,"gender":"male","address":"25 Smith St, Coburg, VIC 3058"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","dob":"1983-03-04","height":162,"gender":"female","address":"25 Smith St, Brunswick, VIC 3056"}

GET /users/_mapping

# Search by range
# Keywords to use: gt(greater than), gte(greater than or equal to), lt(less than), lte(less than or equal to)
GET /users/_search
{
  "query": {
    "range": {
      "height": {
        "gte": 150,
        "lte": 175
      }
    }
  }
}

# Search for datetime
GET /users/_mapping

GET /users/_search
{
  "query": {
    "range": {
      "dob": {
        "gte": "1970-01-01",
        "lte": "1980-01-01"
      }
    }
  }
}

GET /users/_search
{
  "query": {
    "range": {
      "dob": {
        "lte": "now-40y/y"
      }
    }
  }
}
```
