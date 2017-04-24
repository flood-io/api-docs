# Definition

Stops a flood test and returns its status. This may be a long-running request.

    GET https://api.flood.io/floods/:flood_id/stop

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| flood_id | true | string | unique identifier of flood |

# Examples

    curl -u ${API_TOKEN}: -X POST https://api.flood.io/floods/aad1e863cdb884/stop

# Result Format

```json
...
  "_links": {
    "self": {
      "href": "/api/floods/uPYa4XdM1HAnQFsNsE5TLg"
    }
  },
  "uuid": "uPYa4XdM1HAnQFsNsE5TLg",
  "apdex": "1.0 [4000]",
  "tool": "jmeter-2.13",
  "name": "",
  "notes": "",
  "threads": null,
  "rampup": null,
  "duration": 300,
  "tag_list": [],
  "status": "finished",
  "permalink": "https://flood.io/uPYa4XdM1HAnQFsNsE5TLg",
  "remote_errors": null,
  "started": "2015-02-16T02:37:14.000Z",
  "stopped": "2015-02-16T03:01:24.752Z",
  "_embedded": {
    "flood_files": [
      {
        "uuid": "Ezk9CoWdHfcGem3jUw90eQ",
        "name": "jmeter-example.jmx"
      }
    ]
  }
}
```