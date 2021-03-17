# Index exercise
* Run the sample code below (line by line)
* Remove the second listing `2 Church St, Richmond`
* List all the listings in the index
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
