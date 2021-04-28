# Text Queries

Text analysis is the process of converting unstructured text, like the body of an email or a product description, into a
structured format that’s optimized for search.

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

GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}

GET /listing/_mapping

# Search for a word
GET /listing/_search
{
  "query": {
    "match": {
      "address": "Manila"
    }
  }
}

# Will this work?
GET /listing/_search
{
  "query": {
    "match": {
      "address": "manila"
    }
  }
}

GET /listing/_search
{
  "query": {
    "match": {
      "address": "anila"
    }
  }
}

# Search for word in multiple fields
GET /listing/_search
{
  "query": {
    "multi_match": {
      "query": "Quezon", 
      "fields": ["address","title"]
    }
  }
}

# Search for multiple words
GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Townhouse QC"
      }
    }
  }
}

GET /listing/_search
{
  "query": {
    "match": {
      "title": {
        "query": "Quezon QC",
        "operator": "or"
      }
    }
  }
}

```


## Advanced topics:
* Text analyzers

