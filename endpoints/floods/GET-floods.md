# Definition

Returns a list of all flood tests.

    GET https://api.flood.io/floods

# Parameters

None

# Result Format

```json
{
  "_links": {
    "self": {
      "href": "/api/floods"
    },
    "last": {
      "href": "/api/floods?page=4"
    },
    "next": {
      "href": "/api/floods?page=2"
    }
  },
  "total": 192,
  "_embedded": {
    "floods": [
      {
        "_links": {
          "self": {
            "href": "/api/floods/qt4bkaME6yVfR0ATsEQQgA"
          }
        },
        "uuid": "qt4bkaME6yVfR0ATsEQQgA",
        "apdex": "0.95 [3000]",
        "tool": "jmeter-2.13",
        "name": "",
        "notes": "",
        "threads": 50,
        "rampup": 20,
        "duration": 100,
        "tag_list": [],
        "status": "finished",
        "permalink": "https://flood.io/qt4bkaME6yVfR0ATsEQQgA",
        "remote_errors": null,
        "started": "2015-02-12T20:33:46.000Z",
        "stopped": "2015-02-12T20:34:32.000Z",
        "_embedded": {
          "flood_files": [
            {
              "uuid": "fKlx1bUnsjBITRoFMRSKNA",
              "name": "Riot_Checkout_Test_Plan_-_Checkmo.jmx"
            }
          ]
        }
      },
      ...
```


