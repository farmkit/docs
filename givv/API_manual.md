# API 사용설명서
givv 추천 API 사용에 대한 설명입니다.

Base EndPoint URL:
~~~
https://recomm-givv-atms.bitdle.kr/
~~~

## 1. 포스트 추천 API
사용자별 추천 포스트 리스트를 반환

Request URL
~~~
https://recomm-givv-atms.bitdle.kr/givv/recomm-post
~~~


Request Header
|번호|헤더|설명|
|------|---|---|
|1|X-API-KEY|키 값은 추후 지정 예정(임시값: 1)|


Request Body
|번호|내용|설명|
|------|---|---|
|1|userId|포스트 추천 받을 유저 ID|


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

postId 리스트 전달
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



## 2. 이벤트 로그
사용자의 이벤트 로그 수집

Request URL
~~~
https://recomm-givv-atms.bitdle.kr/givv/log-event
~~~

Request Header
|번호|헤더|설명|
|------|---|---|
|1|X-API-KEY|키 값은 추후 지정 예정(임시값: 1)|


Request Body
|번호|내용|설명|
|------|---|---|
|1|userId|유저 ID|
|2|postId|포스트 ID|
|3|eventId|이벤트 ID|


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