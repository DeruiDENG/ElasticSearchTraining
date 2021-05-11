```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{ "index" : {} }
{ "title": "Tropicana Indah Resort Homes, Petaling Jaya, Tropicana" }
{ "index" : {} }
{ "title": "Bukit Damansara (Guarded), KL, Damansara Heights" }
{ "index" : {} }
{ "title": "Tropicana Indah Resort Homes, PJU, Tropicana" }
{ "index" : {} }
{ "title": "Paraiso Residence, Bukit Jalil" }

# Write your query in here：
# Create a query so that it contains the word in the title: Tropicana
# Hints: use match query
GET /listing/_search
{
  "query": {
    "match": {
      "title": "Tropicana"
    }
  }
}

# Create a query so that it contains either `Tropicana` or `KL` in the title
GET /listing/_search
{
  "query": {
   "match": {
     "title": {
       "query": "Tropicana KL",
       "operator": "or"
     }
   }
  }
}
```
