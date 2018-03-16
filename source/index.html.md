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

curl -X PUT "http://<BASE_URL>/order_started/"
  -d order_id=1
  -d start_time=1521115763
  -d device_id=152763ABdjdkga32342
  -d location_x=18.8269788,
  -d localtion_y=73.2045857
  -d localtion_accuracy=0.5
  -d implement_type=thresher
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

### HTTP Request (PUT start_time)

`PUT http://<BASE_URL>/order-started/`

### URL Parameters

Parameter | Description
--------- | -----------
order_id   | Tractor chassis number.
device_id  | The ID of the order whose startTime is to be posted.
start_time | Order start time.
location_x  | Order localtion Latitude 
location_y  | Order localtion Longitude
location_accuracy | Order location accuracy in KMs
implement_type | Implement type identifier


## End of Order

```shell

Send Start Time.

curl -X PUT "http://<BASE_URL>/order-stopped/"
  -d order_id=1
  -d order_stop_time=1521115763
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

### HTTP Request (PUT end_time)

`PUT http://<BASE_URL>/oder-stopped/`



# Tractor

## Alerts

> The data will be posted to the Trringo API in the following JSON format:

```json
{
  "device_id": "152763ABdjdkga32342",
  "alert_type": "Idling",
  "start_time": 1521115763,
  "end_time": 1521115763,
  "location_x": 18.8269788,
  "localtion_y": 73.2045857
}
```


```json
{
  "device_id": "152763ABdjdkga32342",
  "alert": "Unauthorised Work",
  "start_time": 1521115763,
  "end_time": 1521115763,
  "location_x": 18.8269788,
  "localtion_y": 73.2045857
}
```

This endpoint sends data to Trringo for Alerts to be registered.

### HTTP Request (POST alertData)

`POST URL Yet to be finalised.`

### URL Parameters

Parameter | Description
--------- | -----------
alert_type     | Type of Alert - (Idling/Unauthorised Work)
end_time   | Alert activity end time.
start_time | Alert activity start time.
device_id | Tractor chassis number
location_x  | Alert localtion Latitude 
location_y  | Alert localtion Longitude


## Reports

> The data will be posted to the Trringo API in the following JSON format.  This is the End of Journey Report: 

```json
{
  "device_id": "152763ABdjdkga32342",
  "report_data": {
    "KPI-1": 23,
    "KPI-2": 103
  }
}
```

### HTTP Request (POST reports)

`POST URL Yet to be finalised.`

### URL Parameters

Parameter | Description
--------- | -----------
device_id | Tractor chassis number
report_data | JSON object javing key value pairs for report
KPI-1  | Sample KPI data point
KPI-2  | Sampel KPI data point
