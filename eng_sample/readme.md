
# API Usage Guide (Sample)
This is a description of how to use the recommendation API.

Base EndPoint URL:
~~~
https://xxx.bitdle.kr/
~~~

## 1. Post Recommendation API
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
  'https://recomm-givv-atms.bitdle.kr/givv/recomm-post' \
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
Collects user event logs.

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
  'https://recomm-givv-atms.bitdle.kr/givv/log-event' \
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
