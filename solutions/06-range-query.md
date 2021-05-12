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

# Put your query in here
# Create a query to get all the people with `170 < height < 185` (exclusive)
# Hints: Use the range query. Check the lecture note about difference between lt, lte, gt, gte
GET /users/_search
{
  "query": {
    "range": {
      "height": {
        "gt": 170,
        "lt": 185
      }
    }
  }
}


# Create a query to get all the people that is `older than 45 years old`
# Hints: Use date math
GET /users/_search
{
  "query": {
    "range": {
      "dob": {
        "lte": "now-45y/y"
      }
    }
  }
}

```
