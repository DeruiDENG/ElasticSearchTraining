# Compound query

Compound multiple query conditions.

## Bool Query
Combine multiple queries in a boolean manner

Syntax:
```text
GET /{target}/_search
{
  "query": {
    "bool": {
      "{keyword}": [
        {
          "term": {
            "FIELD": {
              "value": "VALUE"
            }
          }
        }
      ]
    }
  }
}
```

Supported keywords:
* must
* should 
* filter
* must_not

```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{"index":{}}
{"price":600,"propertyType":"house","city":"beijing","sold":"2017-10-28"}
{"index":{}}
{"price":800,"propertyType":"house","city":"beijing","sold":"2017-11-05"}
{"index":{}}
{"price":150,"propertyType":"apartment","city":"shanghai","sold":"2017-05-18"}
{"index":{}}
{"price":240,"propertyType":"condo","city":"xian","sold":"2017-07-02"}
{"index":{}}
{"price":1500,"propertyType":"apartment","city":"xian","sold":"2017-08-19"}
{"index":{}}
{"price":250,"propertyType":"townhouse","city":"beijing","sold":"2017-11-05"}
{"index":{}}
{"price":60,"propertyType":"house","city":"chengdu","sold":"2017-01-01"}
{"index":{}}
{"price":145,"propertyType":"land","city":"shanghai","sold":"2017-02-12"}

GET /listing/_mapping

# Must: all the conditions must meet 
GET /listing/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "city.keyword": {
              "value": "beijing"
            }
          } 
        },
        {
          "term": {
            "propertyType.keyword": {
              "value": "house"
            }
          }
        }
      ]
    }
  }
}

# Should: at least one condition must meet (configurable)
GET /listing/_search
{
  "query": {
    "bool": {
      "should": [
        {
          "term": {
            "city.keyword": {
              "value": "beijing"
            }
          } 
        },
        {
          "term": {
            "propertyType.keyword": {
              "value": "house"
            }
          }
        }
      ]
    }
  }
}

# Combine multiple keyword
GET /listing/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "range": {
            "price": {
              "gte": 1000
            }
          }
        }
      ],
      "should": [
        {
          "term": {
            "city.keyword": {
              "value": "beijing"
            }
          }
        },
        {
          "term": {
            "propertyType.keyword": {
              "value": "hobart"
            }
          }
        }
      ]
    }
  }
}

# Nested usage of bool for more complex query requirement
GET /listing/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "bool": {
            "should": [
              {
                "range": {
                  "price": {
                    "gte": 1000
                  }
                }
              },
              {
                "range": {
                  "price": {
                    "lte": 100
                  }
                }
              }
            ]
          }
        }
      ],
      "should": [
        {
          "term": {
            "city.keyword": {
              "value": "beijing"
            }
          }
        },
        {
          "term": {
            "propertyType.keyword": {
              "value": "hobart"
            }
          }
        }
      ]
    }
  }
}
```
