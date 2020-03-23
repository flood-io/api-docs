# GET-floods-flood\_id-report

## Definition

Return text based report for a particular flood identifier.

```text
GET https://api.flood.io/floods/:flood_id/report
```

## Parameters

| Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| flood\_id | true | string | unique identifier of flood |

## Examples

```text
curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/report
```

## Result Format

```javascript
{
  "_links": {
    "self": {
      "href": "/api/floods/A9PMwdqff1E2eTsxEc9hbq"
    }
  },
  "summary": "This flood simulated up to 1,000 users across 1 grid in us-west-1 for 18 minutes. The mean response time was 552ms with a standard deviation of 209 ms. The median was 593 ms and the 90th percentile was 741 ms. The maximum was 959 ms. A maximum of 88,280 rpm with a mean of 70,628 rpm was observed. 1.22 M transactions passed with 0 failed.",
  "mean_response_time": 552,
  "mean_concurrency": 976,
  "mean_throughput": 50263272,
  "mean_error_rate": 0
}
```

