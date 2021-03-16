# Index exercise
* Create a new index called listing
* Query for a listing with the address containing the word: `Blakeview`

Sample code to start with:
```text
# Create a new index
DELETE /listing
PUT /listings

# Index JSON document
POST /listings/_doc
{
  "address": "1 Church St, Richmond"
}

POST /listings/_doc
{
  "address": "2 Church St, Richmond"
}

POST /listings/_doc
{
  "address": "1 Churches St, Blakeview"
}

# Query for a document
# WRITE YOUR QUERY HERE

```
