# GET-grids

## Definition

Returns a list of all grids.

```text
GET https://api.flood.io/grids
```

## Parameters

None

## Examples

```bash
curl -u ${API_TOKEN}: -X GET https://api.flood.io/grids
```

## Result Format

```javascript
{
  "_links": {
    "self": {
      "href": "/api/grids"
    }
  },
  "total": 2,
  "_embedded": {
    "grids": [
      {
        "_links": {
          "self": {
            "href": "/api/grids/X1JLIgBhCLFwmUfsAZ4EOw"
          }
        },
        "uuid": "X1JLIgBhCLFwmUfsAZ4EOw",
        "name": "moonlit-galaxy-production-X1JLIgBhCLFwmUfsAZ4EOw",
        "region": "us-east-1",
        "origin": "US East (Virginia)",
        "instance_quantity": 1,
        "instance_type": "m3.xlarge",
        "infrastructure": "shared",
        "stop_after": 0,
        "status": "started",
        "resources": [
          {
            "ip": "54.152.39.34",
            "private_ip": "172.31.47.129",
            "instance_id": "i-c57d1034",
            "started": "2015-02-03T04:13:10.000Z",
            "state": "running"
          }
        ]
      },
      ...
```

