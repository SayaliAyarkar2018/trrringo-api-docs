---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Carnot-Trringo API! You can use our API to access Carnot-Trringo API endpoints, which is used to transmit accept data from Trringo.

You can view code examples to access the API in the dark area to the right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Apikey: <api_key>"
  -H "Authorization: Token <auth_token>"
```

> Make sure to replace `<api_key>` with your API key and `<auth_token>` with your Auth Token

Carnot uses API keys to allow access to the API. You can get a new API key by writing to us at chakshu.gautam@carnot.co.in

The API key must be included in all API requests to the server in a header that looks like the following:

`Apikey: <api_key>`

Apart from the API key all the endpoints that require user authentication require a Token. The token must be supplied in a header that looks as follows:

`Authorization: Token <auth_token>`

<aside class="notice">
You must replace <code>&lt;api_key&gt;</code> with your personal API key. You must replace <code>&lt;auth_token&gt;</code> with the user's auth token.
</aside>


# Orders

## Start of Order

```shell

Send Start Time.

curl "http://<BASE_URL>/startOrder/"
  -F orderID=1
  -F sessionID=1
  -F startTime=1521115763
  -F tractorID=152763ABdjdkga32342
  -H "Apikey: <api_key>"
  -H "Authorization: Token <auth_token>"
```

> The above command returns JSON structured like this:

```json
{
  "status":true,
  "response":"Success"
}
```

This endpoint starts a particular order.

### HTTP Request (POST startTime)

`POST http://<BASE_URL>/startOrder/`

### URL Parameters

Parameter | Description
--------- | -----------
orderID   | The ID of the order whose startTime is to be posted.
sessionID | The ID of the session whose startTime is to be posted.
startTime | Order start time.
tractorID | Tractor chassis number


## End of Order

```shell

Send Start Time.

curl "http://<BASE_URL>/endOrder/"
  -F orderID=1
  -F sessionID=1
  -F endTime=1521115763
  -F tractorID=152763ABdjdkga32342
  -H "Apikey: <api_key>"
  -H "Authorization: Token <auth_token>"
```

> The above command returns JSON structured like this:

```json
{
  "status":true,
  "response":"Success"
}
```

This endpoint ends a particular order.

### HTTP Request (POST endTime)

`POST http://<BASE_URL>/endOrder/`



# Tractor

## Alerts

> The data will be posted to the Trringo API in the following JSON format:

```json
{
  "tractorID": "152763ABdjdkga32342",
  "alert": "Idling",
  "startTime": 1521115763,
  "endTime": 1521115763,
  "location": "18.8269788,73.2045857"
}
```


```json
{
  "tractorID": "152763ABdjdkga32342",
  "alert": "Unauthorised Work",
  "startTime": 1521115763,
  "endTime": 1521115763,
  "location": "18.8269788,73.2045857"
}
```

This endpoint sends data to Trringo for Alerts to be registered.

### HTTP Request (POST alertData)

`POST URL Yet to be finalised.`

### URL Parameters

Parameter | Description
--------- | -----------
alert     | Type of Alert.
endTime   | Alert activity end time.
startTime | Alert activity start time.
tractorID | Tractor chassis number
location  | Latitude and Longitude for the Alert.


## Reports

> The data will be posted to the Trringo API in the following JSON format.  This is the End of Journey Report: 

```json
{
  "tractorID": "152763ABdjdkga32342",
  "reportData": {
    "KPI-1": 23,
    "KPI-2": 103
  }
}
```

### HTTP Request (POST reports)

`POST URL Yet to be finalised.`
