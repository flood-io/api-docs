# Authentication

Flood API supports multiple authentication strategies, depending on how you're using the API.

## Basic Token

The simplest way to authenticate is by using your API token, which can be found on your account page. Example:

```bash
curl "https://api.flood.io/api/floods" -u "<USER_TOKEN_HERE>:"
```

## OAuth 2

We also support OAuth2, which allows you to generate user tokens, or register an application to develop against and allow your own users to authenticate with their account. This is ideal if you're developing an application for release as a desktop or mobile app.

This feature is still in private beta, if you would like to request access, please email support@flood.io

