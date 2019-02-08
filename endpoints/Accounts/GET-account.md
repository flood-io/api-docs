# Definition

List account details

    GET https://api.flood.io/account

# Result Format

```json
{
  "_links": {
    "self": {
      "href": "/api/account"
    }
  },
  "email": "products@acme.co",
  "_embedded": {
    "users": [
      {
        "_links": {
          "self": {
            "href": "/api/users/101"
          },
          "account": {
            "href": "/api/account"
          }
        },
        "id": 101,
        "email": "coyote@acme.co",
        "authentication_token": "0x42424242",
        "sign_in_count": 10,
        "current_sign_in_at": "2015-04-10T04:08:34.000Z",
        "last_sign_in_at": "2015-04-10T04:08:26.000Z",
        "created_at": "2013-07-22T10:03:34.000Z"
      },
      ...
    ],
    "credentials": [
      {
        "id": 1,
        "provider": "aws",
        "description": "account devtest",
        "arn": null,
        "access_key_id": "SMJHNDsIhzcSyucPJPpZFA"
      },
      {
        "id": 2,
        "provider": "aws",
        "description": "offline account",
        "arn": "127372697123",
        "access_key_id": null
      }
    ]
  }
}
```