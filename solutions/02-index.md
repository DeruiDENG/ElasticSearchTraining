```text
# Create a new index
DELETE /listing
PUT /listing

# Index JSON document
POST /listing/_doc
{
  "address": "1 Church St, Richmond"
}

POST /listing/_doc
{
  "address": "2 Church St, Richmond"
}

POST /listing/_doc
{
  "address": "1 Churches St, Blakeview"
}

# WRITE YOUR QUERY HERE

# List all the listings in the index. Hints: use match_all query
GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}

# Write a request to remove the second listing `2 Church St, Richmond`
# ID may be different in your instance
DELETE /listing/_doc/eEgDXHkB81Kj8jpe6MFd

# List all the listings again to make sure everything is correct.
GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}

# Write a request to add a new list with address: `Desa ParkCity, 52000, Kuala Lumpur`
POST /listing/_doc
{
  "address": "Desa ParkCity, 52000, Kuala Lumpur"
}

# List all the listings again to make sure everything is correct.
GET /listing/_search
{
  "query": {
    "match_all": {}
  }
}
```
