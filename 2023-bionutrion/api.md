# API 사용설명서

음식 인식 API와 음식 추천 API 사용에 대한 설명입니다.

Base EndPoint URL : 
~~~
base url: https://bionutrion.azurewebsites.net 
~~~

## 음식인식
URL : 
~~~
https://bionutrion.azurewebsites.net/api/foodimg/recognize
~~~

~~~
curl -X 'POST' \
  'https://bionutrion.azurewebsites.net/api/foodimg/recognize' \
  -H 'accept: */*' \
  -H 'Content-Type: multipart/form-data' \
  -F 'media=@02.png;type=image/png' \
  -F 'client_id=aa' \
  -F 'client_secret=bb'
~~~