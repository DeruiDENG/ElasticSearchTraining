# Index exercise

## Hints in general
* In each exercise, you will be given one or more requirement
* Copy the code below to your Kibana devtools
* In the devtools, run the commands one-by-one
* Write new code to meet the requirement
* In case you may get stuck, refer to the lecture demo code. You may find it useful to copy the lecture code to your place. Be careful with the file names.

## Requirement
Given an array of listings
* List all the listings in the index. 
> Hints: use match_all query
* Write a request to remove the listing with address `2 Church St, Richmond`
* Write a request to add a new list with address: `Desa ParkCity, 52000, Kuala Lumpur`
* List all the listings again to make sure everything is correct. 


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


# Write a request to remove the second listing `2 Church St, Richmond`


# List all the listings again to make sure everything is correct. You should only see 2 items.


# Write a request to add a new list with address: `Desa ParkCity, 52000, Kuala Lumpur`


# List all the listings again to make sure everything is correct. You should see the newly added item.
```
