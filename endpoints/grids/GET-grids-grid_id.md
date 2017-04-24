# Definition

Return details for a particular grid identifier

    GET https://api.flood.io/grids/:grid_id

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| grid_id | true | string | unique identifier of grid |

# Examples

    curl -u ${API_TOKEN}: -X GET https://api.flood.io/grids/fa715a4be23d6e

# Result Format

```json
{
  "_links": {
    "self": {
      "href": "/api/grids/xSEREOvLBX0d8Xp2C8WI5g"
    }
  },
  "uuid": "xSEREOvLBX0d8Xp2C8WI5g",
  "name": "withered-cove-production-xSEREOvLBX0d8Xp2C8WI5g",
  "region": "ap-southeast-2",
  "origin": "Australia (Sydney)",
  "instance_quantity": 1,
  "instance_type": "m3.xlarge",
  "infrastructure": "demand",
  "stop_after": 60,
  "status": "started",
  "resources": [
    {
      "ip": "54.66.199.235",
      "private_ip": "172.31.30.92",
      "instance_id": "i-c38d4d0d",
      "chef": "complete",
      "port": 80,
      "started": "2015-02-16T02:44:45.000Z",
      "state": "running"
    }
  ]
}
```


