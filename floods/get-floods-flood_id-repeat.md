# GET-floods-flood\_id-repeat

## Definition

Repeats a previous flood test and returns its details. This may be a long-running request. 

```text
GET https://api.flood.io/floods/:flood_id/repeat
```

## Parameters

| Parameter | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| flood\_id | true | string | unique identifier of flood |

You can get the flood ID of a flood from its URL. For example, a flood with the URL

```text
https://app.flood.io/p/27852/f/e2FpMqrnH7AEbn5YgBugrQ/grids/fkamuTolBOCf7EW0MDNdZg/timeline
```

would have the flood ID `e2FpMqrnH7AEbn5YgBugrQ`.

## Examples

```text
curl -u ${API_TOKEN}: -X GET https://api.flood.io/floods/A9PMwdqff1E2eTsxEc9hbq/repeat
```

## Result Format

```javascript
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

