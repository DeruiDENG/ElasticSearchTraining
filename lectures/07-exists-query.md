# Exists query
Query by `existance` of a field.

An indexed value may not exist for a document’s field due to a variety of reasons:
* The field in the source JSON is null or []
* The field does not exist
* etc

```text
DELETE /listing

PUT /listing

# Put multiple documents into elastic search in one shot
POST /listing/_bulk
{ "index": {}}
{ "title": "3 Storey Townhouses (7 Units) in Teachers Village Quezon City" }
{ "index": {}}
{ "title": "2-Storey Townhouse for Sale in Filinvest Northview, QC", "price": null }
{ "index": {}}
{ "title": "BSA Twin Towers Condo Unit near SM Megamall, ADB, La Salle, Poveda, Podium", "price": 18.5 }

GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}


# Returns documents that contain an indexed value for a field. 
GET /listing/_search
{
  "query": {
    "exists": {
      "field": "price"
    }
  }
}

# Search for non-existence
# Using bool query
GET /listing/_search
{
  "query": {
    "bool": {
      "must_not": [
        {
          "exists": {
            "field": "price"
          }
        }
      ]
    }
  }
}
```
