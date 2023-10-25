~~~
curl -X 'POST' \
  'https://bionutrion.azurewebsites.net/api/foodimg/recognize' \
  -H 'accept: */*' \
  -H 'Content-Type: multipart/form-data' \
  -F 'media=@02.png;type=image/png' \
  -F 'client_id=aa' \
  -F 'client_secret=bb'
~~~