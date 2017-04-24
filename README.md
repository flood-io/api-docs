This document describes the make up of the Flood API. 

# Schema
The Flood API follows the [Hypertext Application Language](http://stateless.co/hal_specification.html) serialization format for responses, and accepts a standard ActiveModel style request body format for JSON requests, and form-data based requests for application/multipart.

# Current Version
The current version of the API is v2, which is also accepted as the default version. We encourage you to explicitly specify the correct version:
  
    Accept: application/vnd.flood.v2+json
  
# Making requests
The Flood API server is `https://api.flood.io`, you must use HTTPS for requests or your client will be redirected to the HTTPS version.

# HTTP Verbs
Where possible, Flood API strives to use appropriate HTTP verbs for each action.

| Verb       | Description     | 
| ---------- |-----------------|
| `HEAD`     | Can be issued against any resource to get just the HTTP header info. |
