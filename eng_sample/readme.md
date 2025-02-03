
# API Usage Guide (Sample)
This is a description of how to use the recommendation API.

Generally, we provide our own REST API and integrate with clients through the API endpoints. Typically, we communicate with the client's server and use the HTTPS protocol and X-API-KEY for security

Here's a typical example of the API we provide:


## 1. Recommendation API
Returns a list of recommended posts for each user.

Request URL
~~~
https://xxx.bitdle.kr/xxx/recomm
~~~

Request Header
|No.|Header|Description|
|---|---|---|
|1|X-API-KEY|The key value will be specified later (temporary value: 1)|

Request Body
|No.|Content|Description|
|---|---|---|
|1|userId|User ID to receive recommendations|

```
curl -X 'POST' \
  'https://xxx.bitdle.kr/xxx/recomm-post' \
  -H 'accept: */*' \
  -H 'X-API-KEY: 1' \
  -H 'Content-Type: application/json' \
  -d '{
  "UserId": 51
}'
```

Response

Returns a list of product IDs
~~~
{
    "errcode": 200000,
    "data": [
        2,
        1,
        3,
        5,
        4,
        6,
        7
    ]
}
~~~

## 2. Event Log
It collects user event logs such as clicks, adding items to the cart, or purchases.

If you want to collect more data (e.g., the amount of purchases), additional fields can be added for customization.

Request URL
~~~
https://xxx.bitdle.kr/xxx/log-event
~~~

Request Header
|No.|Header|Description|
|---|---|---|
|1|X-API-KEY|The key value will be specified later (temporary value: 1)|

Request Body
|No.|Content|Description|
|---|---|---|
|1|userId|User ID|
|2|productId|Post ID|
|3|eventId|Event ID|

```
curl -X 'POST' \
  'https://xxx.bitdle.kr/xxx/log-event' \
  -H 'accept: */*' \
  -H 'X-API-KEY: 1' \
  -H 'Content-Type: application/json' \
  -d '{
  "userId": 2,
  "postId": 1,
  "eventId": 3
}'
```

Response
~~~
{
  "errcode": 200000,
  "data": "OK"
}
~~~

## 3. Remark
- The Event ID is configured according to the customer's client scenarios.
- All data types (e.g., user ID or product ID, whether in string or integer format) can be customized to client scenarios.
