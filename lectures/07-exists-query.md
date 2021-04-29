# Exists query
Returns documents that contain an indexed value for a field.

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
{ "address": "9 Malambing Street, UP Village U.P.", "title": "3 Storey Townhouses (7 Units) in Teachers Village Quezon City" }
{ "index": {}}
{ "address": "Philippines, Metro Manila, Quezon City, Batasan Hills Batasan Hills, Quezon City", "title": "2-Storey Townhouse for Sale in Filinvest Northview, QC", "price": null }
{ "index": {}}
{ "address": "Bank Drive Ortigas Business Center behind SM Mega Mall Wack-Wack Greenhills, Mandaluyong", "title": "BSA Twin Towers Condo Unit near SM Megamall, ADB, La Salle, Poveda, Podium", "price": 18.5 }

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
