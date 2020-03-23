# GET-floods-flood\_id

## Definition

Return details for a particular flood identifier

```text
GET https://api.flood.io/floods/:flood_id
```

## Parameters

| Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| flood\_id | true | string | unique identifier of flood |

## Examples

```text
curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq
```

## Result Format

```javascript
{
  "_links": {
    "self": {
      "href": "/api/floods/A9PMwdqff1E2eTsxEc9hbq"
    }
  },
  "uuid": "A9PMwdqff1E2eTsxEc9hbq",
  "batch_id": "T7QJwqJxD1biVwY22gTiaw",
  "apdex": "0.83 [3000]",
  "tool": "jmeter-2.11",
  "name": "MyTest",
  "notes": null,
  "threads": null,
  "rampup": null,
  "duration": 300,
  "tag_list": [],
  "status": "finished",
  "permalink": "https://flood.io/A9PMwdqff1E2eTsxEc9hbq",
  "remote_errors": null,
  "started": "2015-05-27T05:52:46.425Z",
  "stopped": "2015-05-27T05:52:55.501Z",
  "_embedded": {
    "grids": [
      {
        "_links": {
          "self": {
            "href": "/api/grids/Zx2M6I0BsflNOSoevG4Jan"
          }
        },
        "uuid": "Zx2M6I0BsflNOSoevG4Jan",
        "batch_id": "Zx2M6I0BsflNOSoevG4Jan",
        "name": "homeless-reef-production-Zx2M6I0BsflNOSoevG4Jan",
        "region": "sa-east-1",
        "origin": "South America (Sao Paulo)",
        "instance_quantity": 1,
        "instance_type": "m3.xlarge",
        "infrastructure": "demand",
        "stop_after": 60,
        "status": "invoiced",
        "nodes": [
          {
            "ip": "homeless-ElasticL-1X1MQ6XW2HYAJ-80378827.sa-east-1.elb.amazonaws.com",
            "url": "http://homeless-ElasticL-1X1MQ6XW2HYAJ-80378827.sa-east-1.elb.amazonaws.com",
            "private_ip": "127.0.0.1",
            "instance_id": "n/a",
            "chef": null,
            "port": 80,
            "started": "2015-05-27T05:16:19.605Z",
            "state": "running"
          }
        ]
      },
      {
        "_links": {
          "self": {
            "href": "/api/grids/Xmmu3fmoG79KFUP3AahZ7s"
          }
        },
        "uuid": "Xmmu3fmoG79KFUP3AahZ7s",
        "batch_id": "Xmmu3fmoG79KFUP3AahZ7s",
        "name": "homeless-moss-production-Xmmu3fmoG79KFUP3AahZ7s",
        "region": "ap-southeast-2",
        "origin": "Australia (Sydney)",
        "instance_quantity": 1,
        "instance_type": "m3.xlarge",
        "infrastructure": "shared",
        "stop_after": 0,
        "status": "started",
        "nodes": [
          {
            "ip": "54.79.32.10",
            "url": "http://54.79.32.10",
            "private_ip": "172.31.25.28",
            "instance_id": "i-76c455b8",
            "chef": "complete",
            "port": 80,
            "started": "2015-05-26T08:58:31.000Z",
            "state": "running"
          }
        ]
      }
    ],
    "files": [
      {
        "name": "rec_complex.jmx",
        "href": "https://flood-io.s3.amazonaws.com/3018/files/F35LfGdSqTx9Jd9uv8YKaa"
      }
    ],
    "results": [
      {
        "name": "homeless-reef",
        "region": "sa-east-1",
        "href": "https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/result.csv?grid_id=Zx2M6I0BsflNOSoevG4Jan"
      },
      {
        "name": "homeless-moss",
        "region": "ap-southeast-2",
        "href": "https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/result.csv?grid_id=Xmmu3fmoG79KFUP3AahZ7s"
      }
    ],
    "archives": []
  }
}
```

