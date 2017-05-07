# Definition

Return JSON based report for a particular flood identifier, this may be a long running request.

    GET https://api.flood.io/floods/:flood_id/results

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| flood_id | true | string | unique identifier of flood |

# Examples

    curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/results.csv

# Result Format

```csv
Time,Measurement,Label,Account,Flood,Project,Grid,Region,Value
1493022120000,failed,app_about,1,2556,16,1095,us-west-2,0
1493022120000,failed,app_contact,1,2556,16,1095,us-west-2,0
1493022120000,failed,app_registration_step_1,1,2556,16,1095,us-west-2,1
1493022120000,failed,app_homepage,1,2556,16,1095,us-west-2,0
1493022135000,failed,app_about,1,2556,16,1095,us-west-2,0
1493022135000,failed,app_contact,1,2556,16,1095,us-west-2,0
...
```


