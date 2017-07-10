# Defintion

Creates a new flood test and returns its details. This may be a long-running request.

Note to windows users when using curl be sure to prepend the flood_files[] value with an @ symbol if using curl. This indicates to curl the rest should be a file name to read the data from e.g. `-F "flood_files[]=@C:/Users/tim/mytest.jmx"`

    POST https://api.flood.io/floods

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| flood[tool] | true | string | type of tool to use, jmeter, gatling, java-selenium-chrome or java-selenium-firefox |
| flood_files | true | file | test plan to use, as a multipart upload |
| flood[grids] | true | array of mixed | array of grid objects to distribute flood to |
| flood[name] | false | string | name of the flood test |
| flood[notes] | false | string | notes or description of the flood test |
| flood[tag_list] | false | string | comma separated tags associated with the flood test |
| flood[privacy_flag] | false | string | public or private [default]|
| flood[threads] | false | integer | number of threads to pass in to test plan |
| flood[rampup] | false | integer | number of seconds rampup to pass in to test plan |
| flood[duration] | false | integer | number of seconds duration to pass in to test plan |
| flood[override_hosts] | false | string | override DNS hostname resolution `example.com/0.0.0.0, ...` |
| flood[override_parameters] | false | string | override parameters `string-Dparam=value, -Jparam=value, ...` |

# Examples

## Launch a flood on a new grid

```sh
curl -u ${API_TOKEN}: -X POST https://api.flood.io/floods \
  -F "flood[tool]=jmeter" \
  -F "flood[threads]=10" \
  -F "flood[privacy]=public" \
  -F "flood[name]=MyTest" \
  -F "flood[tag_list]=ci,shakeout" \
  -F "flood_files[]=@jmeter-with-plugins.jmx" \
  -F "flood[grids][][infrastructure]=demand" \
  -F "flood[grids][][instance_quantity]=1" \
  -F "flood[grids][][region]=us-west-2" \
  -F "flood[grids][][instance_type]=m4.xlarge" \
  -F "flood[grids][][stop_after]=60"
```

## Lauch a flood on multiple new grids

```sh
curl -u ${FLOOD_API_TOKEN}: -X POST https://api.flood.io/floods \
 -F "flood[tool]=jmeter" \
 -F "flood[threads]=10" \
 -F "flood[privacy]=public" \
 -F "flood[name]=MyTest" \
 -F "flood_files[]=@jmeter-with-plugins.jmx" \
 -F "flood[grids][][infrastructure]=demand" \
 -F "flood[grids][][instance_quantity]=1" \
 -F "flood[grids][][region]=ap-southeast-2" \
 -F "flood[grids][][instance_type]=m4.xlarge" \
 -F "flood[grids][][stop_after]=60" \
 -F "flood[grids][][infrastructure]=demand" \
 -F "flood[grids][][instance_quantity]=1" \
 -F "flood[grids][][region]=ap-southeast-2" \
 -F "flood[grids][][instance_type]=m4.xlarge" \
 -F "flood[grids][][stop_after]=60" | jq -r .
 ```

## Launch flood on an existing grid

```sh
curl -u ${API_TOKEN}: -X POST https://api.flood.io/floods \
  -F "flood[tool]=jmeter" \
  -F "flood[threads]=50" \
  -F "flood_files[]=@/path/to/testplan.jmx" \
  -F "flood_files[]=@/path/to/testdata.csv" \
  -F "flood[grids][][uuid]=qpjrj4MnKmR3VgxOLtuMww"
```

# Result Format

```json
{
  "_links": {
    "self": {
      "href": "/api/floods/VCFstUfl0AMdtaKYBo5d7A"
    }
  },
  "uuid": "VCFstUfl0AMdtaKYBo5d7A",
  "batch_id": "1VVGD5LBVvuatWEJ9SB8aA",
  "apdex": null,
  "tool": "jmeter",
  "name": "MyTest",
  "notes": null,
  "threads": 10,
  "rampup": null,
  "duration": null,
  "tag_list": [
    "ci",
    "shakeout"
  ],
  "status": "queued",
  "permalink": "https://flood.io/VCFstUfl0AMdtaKYBo5d7A",
  "remote_errors": null,
  "started": null,
  "stopped": null,
  "_embedded": {
    "grids": [
      {
        "_links": {
          "self": {
            "href": "/api/grids/hg8ZjZcifgsuQvDfcnBONw"
          }
        },
        "uuid": "hg8ZjZcifgsuQvDfcnBONw",
        "batch_id": "1VVGD5LBVvuatWEJ9SB8aA",
        "name": "jubilant-peak-production-hg8ZjZcifgsuQvDfcnBONw",
        "region": "us-west-2",
        "origin": "US West (Oregon)",
        "instance_quantity": 1,
        "instance_type": "m4.xlarge",
        "infrastructure": "demand",
        "stop_after": 60,
        "status": "starting",
        "nodes": []
      }
    ],
    "files": [
      {
        "name": "lRFFUcXvSIp7pHftfnC7x8",
        "href": "..."
      }
    ],
    "archives": []
  }
}
```

