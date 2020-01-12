This document describes the make up of the Flood API.

# Schema

The Flood API follows the [Hypertext Application Language](http://stateless.co/hal_specification.html) serialization format for responses, and accepts a standard ActiveModel style request body format for JSON requests, and form-data based requests for application/multipart.

# Current Version

The current version of the API is v2, which is also accepted as the default version. We encourage you to explicitly specify the correct version:

```
Accept: application/vnd.flood.v2+json
```

# Making requests

The Flood API server is `https://api.flood.io`, you must use HTTPS for requests or your client will be redirected to the HTTPS version.

# HTTP Verbs

Where possible, Flood API strives to use appropriate HTTP verbs for each action.

| Verb | Description |
| --- | --- |
| HEAD | Can be issued against any resource to get just the HTTP header info. |
| GET | Used for retrieving resources. |
| POST | Used for creating resources. |
| PUT | Used for replacing resources or collections. For PUT requests with no body attribute, be sure to set the Content-Length header to zero. |
| DELETE | Used for deleting resources. Will return a 204 with an empty body on success. |

# Authentication

Flood API supports multiple authentication strategies, depending on how you're using the API.

## Basic Token

The simplest way to authenticate is by using your API token, which can be found on your account page. Example:

```
curl "https://api.flood.io/api/floods" -u "<USER_TOKEN_HERE>:"
```

## OAuth 2

We also support OAuth2, which allows you to generate user tokens, or register an application to develop against and allow your own users to authenticate with their account. This is ideal if you're developing an application for release as a desktop or mobile app.

This feature is still in private beta, if you would like to request access, please email support@flood.io

# End to End Example

Using your favourite CI build automation tool, you could execute a similar script as follows to launch and run flood tests:

```
#!/bin/bash
set -e

# Check we have the jq binary to make parsing JSON responses a bit easier
command -v jq >/dev/null 2>&1 || \
{ echo >&2 "Please install http://stedolan.github.io/jq/download/  Aborting."; exit 1; }

# Start a flood
echo
echo "[$(date +%FT%T)+00:00] Starting flood"
flood_uuid=$(curl -u flood_live_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx: -X POST https://api.flood.io/floods \
-F "flood[tool]=jmeter" \
-F "flood[threads]=5" \
-F "flood[project]=Default" \
-F "flood[privacy]=public" \
-F "flood[name]=CI Shakeout" \
-F "flood_files[]=@data.csv" \
-F "flood_files[]=@basic.jmx" \
-F "flood[grids][][infrastructure]=demand" \
-F "flood[grids][][instance_quantity]=1" \
-F "flood[grids][][region]=us-west-2" \
-F "flood[grids][][instance_type]=m5.xlarge" \
-F "flood[grids][][stop_after]=15" | jq -r ".uuid")

# Wait for flood to finish
echo "[$(date +%FT%T)+00:00] Waiting for flood $flood_uuid"
while [ $(curl --silent --user $FLOOD_API_TOKEN: https://api.flood.io/floods/$flood_uuid | \
  jq -r '.status == "finished"') = "false" ]; do
  echo -n "."
  sleep 3
done

# Get the summary report
flood_report=$(curl --silent --user $FLOOD_API_TOKEN: https://api.flood.io/floods/$flood_uuid/report | \
  jq -r ".summary")

echo
echo "[$(date +%FT%T)+00:00] Detailed results at https://flood.io/$flood_uuid"
echo "$flood_report"

# Optionally store the CSV results
echo
echo "[$(date +%FT%T)+00:00] Storing CSV results at results.csv"
curl --silent --user $FLOOD_API_TOKEN: https://api.flood.io/floods/$flood_uuid/result.csv > result.csv
```



