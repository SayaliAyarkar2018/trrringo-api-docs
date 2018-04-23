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
  -d instrumented_device_id=152763ABdjdkga32342
  -d location_x=18.8269788
  -d location_y=73.2045857
  -d location_accuracy=0.5
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
instrumented_device_id | Tractor chassis number
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

### URL Parameters

Parameter | Description
--------- | -----------
order_id   | Tractor chassis number.
order_stop_time | Order end time.

### HTTP Request (PUT end_time)

`PUT http://<BASE_URL>/oder-stopped/`



# Tractor

## Register

> The data will be posted to the Trringo API in the following JSON format:
```json
{
  "instrumented_device_id": "152763ABdjdkga32342",
  "iot_device_id": 23,
  }
```
### HTTP Request (POST alertData)

`POST https://agg.trringology.com/iot/v2/register`

### URL Parameters

Parameter | Description
--------- | -----------
instrumented_device_id | Tractor chassis number
iot_device_id | IOT device number

## Alerts

> The data will be posted to the Trringo API in the following JSON format:

```json
{
  "instrumented_device_id": "152763ABdjdkga32342",
  "category": "Unauthorised Work - 1",
  "data": {
    "start_time": 1521115763,
    "end_time": 1521115763,
    "location_x": 18.8269788,
    "localtion_y": 73.2045857
  }
```


```json
{
  "instrumented_device_id": "152763ABdjdkga32342",
  "category": "Unauthorised Work",
  "alert_type": 1,
  "data": {
    "start_time": 1521115763,
    "end_time": 1521115763,
    "location_x": 18.8269788,
    "localtion_y": 73.2045857
  }

}
```

This endpoint sends data to Trringo for Alerts to be registered.

### HTTP Request (POST alertData)

`POST https://agg.trringology.com/iot/v2/alerts`

### URL Parameters

Parameter | Description
--------- | -----------
category  | Alert categories(Idling/Unauthorised_Work/Geofence) - (Alert Type) A subtype of the above category. (Will be defined when needed. Currenltly 1 will be sent) 
data | Data related to the alert. (Will vary but the fields below will be there for all of type. But there will be additional data for all of them.)
instrumented_device_id | Tractor chassis number
end_time   | Alert activity end time.
start_time | Alert activity start time.
location_x  | Alert localtion Latitude.
location_y  | Alert localtion Longitude.


## Reports

> The data will be posted to the Trringo API in the following JSON format.  This is the End of Journey Report: 

```json
{
  "order_id": 123456,
  "authorized": 1,
  "authorized": "ORDER_COMPLETE",
  "instrumented_device_id": "152763ABdjdkga32342",
  "iot_device_id": 9,
  "report_data": {
    "eoa": 1.22,
    "start_time": 1521115763,
    "end_time": 1521115763,
    "duration": 1521,
    "location_x": 18.8269788,
    "location_y": 73.2045857,
    "map_x": [18.8269788, 18.8269789, 18.8269790],
    "map_y": [73.2045857, 73.2045858, 73.2045859]
   }
}
```

### HTTP Request (POST reports)

`POST https://agg.trringology.com/iot/v2/reports`

### URL Parameters

Parameter | Description
--------- | -----------
instrumented_device_id | Tractor chassis number
order_id | Order ID for the report
report_data | JSON object javing key value pairs for report
end_time   | Alert activity end time.
start_time | Alert activity start time.
location_x  | Alert localtion Latitude.
location_y  | Alert localtion Longitude.
iot_device_id | IOT Device ID sent during registeration.
map_x | Location x co ordinates list
map_y | Location y co ordinates list


## Odyssey

> The data will be posted to the Trringo API in the following JSON format.  This is the End of Odyssey Report: 

```json
{
  "odyssey_id": 123456,
  "instrumented_device_id": "152763ABdjdkga32342",
  "iot_device_id": 9,
  "report_data": {
    "distance": 23.4,
    "time": 5798,
    "authorised orders": 2,
    "unauthorised orders": 4,
    "area_ploughed": 2.1,
    "start_time": 1521115763,
    "end_time": 1521115763
   }
}
```

### HTTP Request (POST reports)

`POST https://agg.trringology.com/iot/v2/odyssey`

### URL Parameters

Parameter | Description
--------- | -----------
instrumented_device_id | Tractor chassis number
odyssey_id | Odyssey ID for the report
report_data | JSON object javing key value pairs for report
end_time   | Odyssey end time.
start_time | Odyssey start time.
area_ploughed  | Total area (acres) ploughed in the odyssey
authorised_orders  | Total count of authorised orders in the Odyssey
unauthorised_orders | Total count of unauthorised orders in the Odyssey
time | Total time (seconds) for the Odysser
distance | Distance travelled (Kms) by tractor in between farms and and between Hub and farm
