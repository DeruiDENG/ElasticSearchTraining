# Text queries exercise
* Create a query so that it contains the word in the address: Coburg
* Create a query so that it contains either `Coburg` or `Fitzroy` in the address

```text
DELETE /listing

PUT /listing

POST /listing/_bulk
{ "index" : {} }
{ "address": "31 Smith St, Brunswick, VIC 3056" }
{ "index" : {} }
{ "address": "25 Smith St, Brunswick, VIC 3056" }
{ "index" : {} }
{ "address": "25 Smith St, Coburg, VIC 3058" }
{ "index" : {} }
{ "address": "55 Station St, Fitzroy, VIC 3065" }


# Write your query in here：

```
