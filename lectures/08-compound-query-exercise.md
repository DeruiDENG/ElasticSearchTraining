# Compound query exercise
Given a list of listings, 
* Create a query get all the listing that is `in shanghai OR beijing, house property type AND sold before 2017-01-01`

```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{"index":{}}
{"price":600,"propertyType":"house","city":"shanghai","sold":"2017-10-28"}
{"index":{}}
{"price":800,"propertyType":"house","city":"shanghai","sold":"2016-11-05"}
{"index":{}}
{"price":150,"propertyType":"apartment","city":"xian","sold":"2017-05-18"}
{"index":{}}
{"price":240,"propertyType":"condo","city":"beijing","sold":"2017-07-02"}
{"index":{}}
{"price":1500,"propertyType":"apartment","city":"beijing","sold":"2017-08-19"}
{"index":{}}
{"price":250,"propertyType":"townhouse","city":"shanghai","sold":"2015-11-05"}
{"index":{}}
{"price":60,"propertyType":"house","city":"chengdu","sold":"2017-01-01"}
{"index":{}}
{"price":145,"propertyType":"land","city":"xian","sold":"2017-02-12"}

# Start your work in here:
# Create a query get all the listing that `the city is shanghai OR beijing, house property type AND price larger than 700`

# Hints:Check the mapping before you start
GET /listing/_mapping

# Hints: Combine the usage of `should` and `must`
```
