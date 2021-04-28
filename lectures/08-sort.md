# Sort

```text
DELETE /listing

PUT /listing

# Put multiple documents into elastic search in one shot
POST /listing/_bulk
{ "index": {}}
{ "address": "9 Malambing Street, UP Village U.P.", "title": "3 Storey Townhouses (7 Units) in Teachers Village Quezon City", "price": 13 }
{ "index": {}}
{ "address": "Philippines, Metro Manila, Quezon City, Batasan Hills Batasan Hills, Quezon City", "title": "2-Storey Townhouse for Sale in Filinvest Northview, QC", "price": 4.8 }
{ "index": {}}
{ "address": "Bank Drive Ortigas Business Center behind SM Mega Mall Wack-Wack Greenhills, Mandaluyong", "title": "BSA Twin Towers Condo Unit near SM Megamall, ADB, La Salle, Poveda, Podium", "price": 18.5 }

GET /listing/_mapping

# Search for text
GET /listing/_search
{
  "query": {
    "match": {
      "address": {
        "query": "quezon manila malambing",
        "operator": "or"
      }
    }
  }
}

# Sort by price
GET /listing/_search
{
  "query": {
    "match": {
      "address": {
        "query": "quezon manila malambing",
        "operator": "or"
      }
    }
  },
  "sort": [
    {
      "price": {
        "order": "desc"
      }
    },
    {
      
    }
  ]
}

# Multiple sort
```
