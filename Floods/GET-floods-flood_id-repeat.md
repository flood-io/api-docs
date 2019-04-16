# Definition

Repeats a previous flood test and returns its details. This may be a long-running request. If a grid region or uuid is not specified then the flood test will be repeated on all available grids for your account.

    GET https://api.flood.io/floods/:flood_id/repeat

# Parameters

| Parameter | Required | Type | Description |
| --------- | -------- | ---- | ----------- |
| flood_id | true | string | unique identifier of flood |
| region | false | string | target region to launch the flood test in |
| grid | false | string | use a specific grid identifier to launch the test in instead of a region |

You can get the flood ID of a flood from its URL. For example, a flood with the URL

```
https://app.flood.io/p/27852/f/e2FpMqrnH7AEbn5YgBugrQ/grids/fkamuTolBOCf7EW0MDNdZg/timeline
```
would have the flood ID `e2FpMqrnH7AEbn5YgBugrQ`.


# Examples

    curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/repeat?region=us-west-2

# Result Format

```json
{
  "_links": {
    "self": {
      "href": "/api/floods/Xp3MeLYfn44HSrXyW8T90A"
    }
  },
  "uuid": "Xp3MeLYfn44HSrXyW8T90A",
  "apdex": null,
  "tool": "jmeter-2.13",
  "name": null,
  "notes": null,
  "threads": 50,
  "rampup": null,
  "duration": null,
  "tag_list": [],
  "status": "queued",
  "permalink": "https://flood.io/Xp3MeLYfn44HSrXyW8T90A",
  "remote_errors": null,
  "started": "2015-02-16T02:56:20.776Z",
  "stopped": null,
  "_embedded": {
    "flood_files": []
  }
}
```
