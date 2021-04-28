```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","dob":"1968-01-10","height":183,"address":"55 Station St, Fitzroy, VIC 3065"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","dob":"1974-01-02","height":170,"gender":"male","address":"25 Smith St, Coburg, VIC 3058"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","dob":"1983-03-04","height":162,"gender":"female","address":"25 Smith St, Brunswick, VIC 3056"}

GET /users/_search
{
  "query": {
    "exists": {
      "field": "gender"
    }
  }
}

GET /users/_search
{
  "query": {
    "bool": {
      "must_not": [
        {
          "exists": {
            "field": "gender"
          }
        }
      ]
    }
  }
}
```
