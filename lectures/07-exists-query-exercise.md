# Bool query exercise
For a list of users,
* Query for users whose `gender is KNOWN`
* Query for users whose `gender is UNKNOWN`

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

# Put your query in here
```
