# Definition

Return JSON based report for a particular flood identifier, this may be a long running request.

    GET https://api.flood.io/floods/:flood_id/result

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| flood_id | true | string | unique identifier of flood |

# Examples

    curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/result

# Result Format

```json
[
  {
    "name": "failed",
    "tags": {
      "account": "1091",
      "flood": "272",
      "grid": "75",
      "label_id": "1",
      "project": "1"
    },
    "values": [
      {
        "time": 1490784165000,
        "value": 122
      },
      ...
```


