# Compound query exercise
Given a list of listings, 
* Create a query get all the listing that is `in hobart OR melbourne, with house property type AND sold before 2017-01-01`

```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{ "index": {}}
{ "price" : 600, "propertyType" : "house",     "city" : "hobart",    "sold" : "2017-10-28" }
{ "index": {}}
{ "price" : 800, "propertyType" : "house",     "city" : "hobart",    "sold" : "2016-11-05" }
{ "index": {}}
{ "price" : 150, "propertyType" : "apartment", "city" : "brisbane",  "sold" : "2017-05-18" }
{ "index": {}}
{ "price" : 240, "propertyType" : "condo",      "city" : "melbourne", "sold" : "2017-07-02" }
{ "index": {}}
{ "price" : 1500, "propertyType" : "apartment", "city" : "melbourne", "sold" : "2017-08-19" }
{ "index": {}}
{ "price" : 250, "propertyType" : "townhouse",     "city" : "hobart",    "sold" : "2015-11-05" }
{ "index": {}}
{ "price" : 60, "propertyType" : "house",     "city" : "sydney",    "sold" : "2017-01-01" }
{ "index": {}}
{ "price" : 145, "propertyType" : "land",      "city" : "brisbane",  "sold" : "2017-02-12" }

```
