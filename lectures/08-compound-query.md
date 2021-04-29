# Compound query

Compound multiple query conditions.

## Bool Query
Combine multiple queries in a boolean manner
* must
* should 
* filter
* must_not

```text
DELETE /listing

PUT /listing

POST /users/_bulk
{"index":{}}
{"name":"Larry Sanger","title":"Developer","dob":"1968-01-10","height":183,"gender":"male"}
{"index":{}}
{"name":"Magnus Manske","title":"Lead Developer","dob":"1974-01-02","height":170,"gender":"male"}
{"index":{}}
{"name":"Emna Mizouni","title":"Developer","dob":"1983-03-04","height":162,"gender":"female"}
```
