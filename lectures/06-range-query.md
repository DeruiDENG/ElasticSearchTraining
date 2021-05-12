# Range query
Range query is another term-based query.
* Match the documents with the values in specific range
* Support the field types: numeric types, date types, keyword(with a condition)

```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","dob":"1968-01-10","height":183,"gender":"male"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","dob":"1974-01-02","height":170,"gender":"male"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","dob":"1983-03-04","height":162,"gender":"female"}

GET /users/_mapping

# Search by range
# Query for people whose height is within a range
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

# Range query works for date time
GET /users/_mapping

# Query for people whose dob is within a given range
GET /users/_search
{
  "query": {
    "range": {
      "dob": {
        "gte": "1980-01-01",
        "lte": "now"
      }
    }
  }
}

# Query for people who was more than 40 years old
# Date math syntax
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
