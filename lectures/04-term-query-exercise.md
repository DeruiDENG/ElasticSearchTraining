# Term query exercise
Given a list of users
* Create a query to get all the `Male` users
* Create a query to get all the `Developer` and `Senior Developer`

## Hints:
* Be careful with field types, check the mapping first.
* If you are stuck with solutions, refer to `04-term-query.md`

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

# Write your answer below
# Hints: Check the mapping before writing your query
GET /users/_mapping

# Hints: Do not do term query on 'text' field

# Create a query to get all the `Male` users

# Create a query to get all the `Developer` and `Senior Developer`
```
