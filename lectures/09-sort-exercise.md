# Sort exercise
Give a list of users,
* Create a query to match all users, people with `taller height coming first`
* If height of the users are the same, `younger people coming first`

Hints:
* use match_all query
* `sort` accepts multiple elements as an array
* Consider dob date as a `number`, 2021-5-15 is `larger` than 2020-5-15

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

# Put your query in here

# Create a query to match all users, people with `taller height coming first`

# If height of the users are the same, `younger people coming first`

```
