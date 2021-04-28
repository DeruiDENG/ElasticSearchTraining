# Term query exercise
Given a list of users
* Create a query to get all the `Male`
* Create a query to get all the `Developer` and `Senior Developer`

## Hints:
* Be careful with field types, check the mapping first.

```text
DELETE /users

PUT /users

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","yearOfBirth":1968,"gender":"Male","address":"55 Station St, Fitzroy, VIC 3065"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","yearOfBirth":1974,"gender":"Male","address":"25 Smith St, Coburg, VIC 3058"}
{"index":{}}
{"name":"Emna Mizouni","title":"Senior Developer","yearOfBirth":1983,"gender":"Female","address":"25 Smith St, Brunswick, VIC 3056"}

# Check the mapping before writing your query

# Put your query in here
```
