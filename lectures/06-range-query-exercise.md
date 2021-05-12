# Range query exercise
Given a list of users,
* Create a query to get all the people with `170 < height < 185` (exclusive)
* Create a query to get all the people that is `older than 45 years old`

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

# Put your query in here
# Create a query to get all the people with `170 < height < 185` (exclusive)
# Hints: Use the range query. Check the lecture note about difference between lt, lte, gt, gte

# Create a query to get all the people that is `older than 45 years old`
# Hints: Use date math


```
