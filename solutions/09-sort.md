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
{"index":{}}
{"name":"Will Smith","title":"Senior Developer","dob":"1988-04-02","height":162,"gender":"female"}

# Answers:
GET /users/_search
{
  "query": {
    "match_all": {}
  },
  "sort": [
    {
      "height": {
        "order": "desc"
      }
    },
    {
      "dob": {
        "order": "desc"
      }
    }
  ]
}
```
