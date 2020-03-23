# POST-grids

## Definition

Creates a new grid. This may be a long-running request.

```text
POST https://api.flood.io/grids
```

## Parameters

| Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| grid\[region\] | true | string | target region to start the grid in, any value from ap-southeast-2, us-east-1, us-west-1, us-west-2, eu-west-1, eu-central-1, ap-southeast-1, ap-northeast-1, sa-east-1 |
| grid\[instance\_quantity\] | true | integer | number of grid nodes to launch |
| grid\[stop\_after\] | true | integer | stop after n minutes, greater than 0, less than or equal to 2,880 \(48 hours\) |
| grid\[infrastructure\] | true | string | On Demand `demand` or Host Your Own `hosted` |
| grid\[aws\_platform\] | false | string | aws platform to use `ec2_default_vpc`, `ec2_classic` |
| grid\[aws\_tags\] | false | string | optional tags e.g. `key1=value, key2=value` |
| grid\[aws\_availability\_zone\] | false | string | optional availability zone within a region e.g. `us-east-1a` |
| grid\[aws\_spot\_price\] | false | double | optional spot price for instances in decimal cents e.g. 0.48 |
| grid\[credential\_id\] | false | string | required for `hosted` grids; retrieved from GET [https://api.flood.io/account](https://api.flood.io/account) |
| grid\[azure\_tenant\_id\] | false | string | optional for Azure based `hosted` grids as an alternative to specifying the `credential_id` |
| grid\[aws\_arn\] | false | string | optional for AWS based `hosted` grids as an alternative to specifying the `credential_id` |
| grid\[aws\_vpc\_identifier\] | false | string | optional VPC ID e.g. `vpc-4991ab20` |
| grid\[aws\_vpc\_subnet\_public\] | false | string | optional public subnet e.g. `subnet-4991ab21` |
| grid\[aws\_vpc\_subnet\_private\] | false | string | optional private subnet e.g. `subnet-4991ab22` |
| grid\[aws\_vpc\_security\_groups\] | false | string | optional security groups e.g. `sg-11692834` |
| grid\[instance\_type\] | true | string | instance type e.g. `m5.xlarge` |

## Examples

### Launch on demand grid

```bash
curl -u ${API_TOKEN}: -X POST https://api.flood.io/grids \
  -F "grid[region]=ap-southeast-2" \
  -F "grid[infrastructure]=demand" \
  -F "grid[instance_quantity]=2" \
  -F "grid[stop_after]=60" \
  -F "grid[instance_type]=m5.xlarge"
```

### Launch hosted grid

```bash
curl -u abc123: -X POST https://api.flood.io/grids \
  -F "grid[region]=ap-southeast-2" \
  -F "grid[infrastructure]=hosted" \
  -F "grid[aws_platform]=ec2_default_vpc" \
  -F "grid[instance_quantity]=1" \
  -F "grid[stop_after]=60" \
  -F "grid[instance_type]=m5.xlarge" \
  -F "grid[credential_id]=1"
```

## Result Format

```javascript
{
  "_links": {
    "self": {
      "href": "/api/grids/ypg1ZVWjsCiSN8mOfCdybw"
    }
  },
  "uuid": "ypg1ZVWjsCiSN8mOfCdybw",
  "name": "screeching-cavern-production-ypg1ZVWjsCiSN8mOfCdybw",
  "region": "ap-southeast-2",
  "origin": "Australia (Sydney)",
  "instance_quantity": 2,
  "instance_type": "m5.xlarge",
  "infrastructure": "demand",
  "stop_after": 60,
  "status": "queued",
  "nodes": []
}
```

