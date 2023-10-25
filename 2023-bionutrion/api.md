# API 사용설명서

음식 인식 API와 음식 추천 API 사용에 대한 설명입니다.

Base EndPoint URL : 
~~~
base url: https://bionutrion.azurewebsites.net 
~~~

## 음식인식

### request 
URL : 
~~~
https://bionutrion.azurewebsites.net/api/foodimg/recognize
~~~

|변수명|설명|
|:-|:-|
media|이미지파일, 바이너리 형식으로 읽은 이미지
client_id|클라이언트 ID, 사전에 협의된 클라이언트 ID 입력
client_secret| 클라이언트 secret, 사전에 협의된 클라이언트 secret 입력

__이미지 파일__
- 사이즈
  - kakao: 800px * 800px 이상
  - KT: 최소(1080px * 720px 또는 720px * 1080px), 최대(2560px * 1440px 또는 1440px * 2550px)
- 확장자
  - jpg
  - png

~~~
curl -X 'POST' \
  'https://bionutrion.azurewebsites.net/api/foodimg/recognize' \
  -H 'accept: */*' \
  -H 'Content-Type: multipart/form-data' \
  -F 'media=@Img_008_0000.jpg;type=image/jpeg' \
  -F 'client_id=1' \
  -F 'client_secret=1'
~~~
### response
|변수명|설명|
|:-|:-|
company|API 제공 회사
code|API 호출 결과 코드
message|API 호출 결과 메시지
foodRecognitions|API 호출 결과(인식 음식, 위치, 영양정보 등)

__response sample__
~~~
{
  "errcode": 200000,
  "data": [
    {
      "company": "KT",
      "code": 500,
      "message": "{\"status_code\":400,\"detail\":\"Image is too small\",\"custom_code\":\"ERR03\"}",
      "foodRecognitions": []
    },
    {
      "company": "kakao",
      "code": 0,
      "message": "",
      "foodRecognitions": [
        {
          "position": {
            "x": 8,
            "y": 88,
            "width": 212,
            "height": 389
          },
          "foodPredictions": [
            {
              "name": "생선구이",
              "accurancy": 0.7231,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 109,
                "carbohydrate": 0.28,
                "sugar": 0.08,
                "dietaryFiber": 0,
                "protein": 22.6,
                "fat": 1.18,
                "transFat": 0,
                "saturatedFat": 0.256,
                "cholesterol": 75,
                "natrium": 605
              }
            },
            {
              "name": "고등어구이",
              "accurancy": 0.0762,
              "nutrition": {
                "oneTimeOffer": 200,
                "calrorie": 379,
                "carbohydrate": 0.7,
                "sugar": 0.18,
                "dietaryFiber": 0,
                "protein": 35.18,
                "fat": 25.19,
                "transFat": 0,
                "saturatedFat": 5.809,
                "cholesterol": 120,
                "natrium": 1210
              }
            },
            {
              "name": "삼겹살구이",
              "accurancy": 0.066,
              "nutrition": {
                "oneTimeOffer": 200,
                "calrorie": 699,
                "carbohydrate": 1.25,
                "sugar": 0,
                "dietaryFiber": 0,
                "protein": 36.43,
                "fat": 59.64,
                "transFat": 0,
                "saturatedFat": 20.44,
                "cholesterol": 128,
                "natrium": 2033
              }
            },
            {
              "name": "닭가슴살스테이크",
              "accurancy": 0.0498,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 142,
                "carbohydrate": 8.17,
                "sugar": 0.54,
                "dietaryFiber": 0,
                "protein": 22.45,
                "fat": 2.2,
                "transFat": 0,
                "saturatedFat": 0.6,
                "cholesterol": 20,
                "natrium": 294
              }
            },
            {
              "name": "연어구이(홍연어구운것)",
              "accurancy": 0.0359,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 171,
                "carbohydrate": 0.49,
                "sugar": 0.11,
                "dietaryFiber": 0,
                "protein": 23.97,
                "fat": 7.56,
                "transFat": 0,
                "saturatedFat": 1.312,
                "cholesterol": 62,
                "natrium": 467
              }
            }
          ]
        },
        {
          "position": {
            "x": 196,
            "y": 101,
            "width": 299,
            "height": 342
          },
          "foodPredictions": [
            {
              "name": "돼지껍데기",
              "accurancy": 0.858,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 234.5,
                "carbohydrate": 16.3,
                "sugar": 3.7,
                "dietaryFiber": 0,
                "protein": 17.2,
                "fat": 11.2,
                "transFat": 0.1,
                "saturatedFat": 3.3,
                "cholesterol": 31.8,
                "natrium": 519.9
              }
            },
            {
              "name": "꼼장어구이",
              "accurancy": 0.0603,
              "nutrition": {
                "oneTimeOffer": 200,
                "calrorie": 326,
                "carbohydrate": 2.3,
                "sugar": 1.2,
                "dietaryFiber": 0,
                "protein": 42.7,
                "fat": 16.2,
                "transFat": 0.1,
                "saturatedFat": 2.8,
                "cholesterol": 341.83,
                "natrium": 826.79
              }
            },
            {
              "name": "막창구이",
              "accurancy": 0.0364,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 250,
                "carbohydrate": 2,
                "sugar": 0,
                "dietaryFiber": 0,
                "protein": 12,
                "fat": 20,
                "transFat": 0,
                "saturatedFat": 0,
                "cholesterol": 211,
                "natrium": 518
              }
            },
            {
              "name": "꼼장어_생것",
              "accurancy": 0.0143,
              "nutrition": {
                "oneTimeOffer": 60,
                "calrorie": 77,
                "carbohydrate": 0,
                "sugar": 0,
                "dietaryFiber": 0,
                "protein": 10,
                "fat": 3,
                "transFat": 0,
                "saturatedFat": 0,
                "cholesterol": 0,
                "natrium": 88
              }
            },
            {
              "name": "장어구이(뱀장어,조미)",
              "accurancy": 0.0047,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 224,
                "carbohydrate": 5.95,
                "sugar": 1.21,
                "dietaryFiber": 0.9,
                "protein": 19.59,
                "fat": 13.09,
                "transFat": 0,
                "saturatedFat": 2.598,
                "cholesterol": 127,
                "natrium": 432
              }
            }
          ]
        },
        {
          "position": {
            "x": 432,
            "y": 84,
            "width": 206,
            "height": 298
          },
          "foodPredictions": [
            {
              "name": "삼겹살구이",
              "accurancy": 0.1995,
              "nutrition": {
                "oneTimeOffer": 200,
                "calrorie": 699,
                "carbohydrate": 1.25,
                "sugar": 0,
                "dietaryFiber": 0,
                "protein": 36.43,
                "fat": 59.64,
                "transFat": 0,
                "saturatedFat": 20.44,
                "cholesterol": 128,
                "natrium": 2033
              }
            },
            {
              "name": "돼지갈비구이",
              "accurancy": 0.118,
              "nutrition": {
                "oneTimeOffer": 85,
                "calrorie": 118,
                "carbohydrate": 0,
                "sugar": 0,
                "dietaryFiber": 0,
                "protein": 13.27,
                "fat": 6.76,
                "transFat": 0,
                "saturatedFat": 2.541,
                "cholesterol": 39,
                "natrium": 188
              }
            },
            {
              "name": "소갈비",
              "accurancy": 0.0471,
              "nutrition": {
                "oneTimeOffer": 200,
                "calrorie": 544.6,
                "carbohydrate": 3.9,
                "sugar": 0,
                "dietaryFiber": 0.179,
                "protein": 37.4,
                "fat": 39.6,
                "transFat": 0,
                "saturatedFat": 0,
                "cholesterol": 140,
                "natrium": 257.8
              }
            },
            {
              "name": "생선구이",
              "accurancy": 0.0424,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 109,
                "carbohydrate": 0.28,
                "sugar": 0.08,
                "dietaryFiber": 0,
                "protein": 22.6,
                "fat": 1.18,
                "transFat": 0,
                "saturatedFat": 0.256,
                "cholesterol": 75,
                "natrium": 605
              }
            },
            {
              "name": "박대구이",
              "accurancy": 0.0412,
              "nutrition": {
                "oneTimeOffer": 69,
                "calrorie": 106.17,
                "carbohydrate": 1.48,
                "sugar": 0,
                "dietaryFiber": 0.8216,
                "protein": 11.74,
                "fat": 5.5,
                "transFat": 0,
                "saturatedFat": 0,
                "cholesterol": 32.75,
                "natrium": 672.91
              }
            }
          ]
        },
        {
          "position": {
            "x": 40,
            "y": 447,
            "width": 344,
            "height": 113
          },
          "foodPredictions": [
            {
              "name": "마늘",
              "accurancy": 0.8809,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 123,
                "carbohydrate": 26.42,
                "sugar": 0.23,
                "dietaryFiber": 3.8,
                "protein": 7.45,
                "fat": 0.16,
                "transFat": 0,
                "saturatedFat": 0.06,
                "cholesterol": 0,
                "natrium": 3
              }
            },
            {
              "name": "가래떡",
              "accurancy": 0.0318,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 195,
                "carbohydrate": 43.7,
                "sugar": 0,
                "dietaryFiber": 0.6,
                "protein": 3.9,
                "fat": 0.5,
                "transFat": 0,
                "saturatedFat": 0.2,
                "cholesterol": 0,
                "natrium": 240.57
              }
            },
            {
              "name": "삶은감자",
              "accurancy": 0.0101,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 77,
                "carbohydrate": 17.39,
                "sugar": 0,
                "dietaryFiber": 1.6,
                "protein": 2.07,
                "fat": 0.08,
                "transFat": 0,
                "saturatedFat": 0.03,
                "cholesterol": 0,
                "natrium": 1
              }
            },
            {
              "name": "삶은계란",
              "accurancy": 0.0094,
              "nutrition": {
                "oneTimeOffer": 100,
                "calrorie": 143,
                "carbohydrate": 2.19,
                "sugar": 0.17,
                "dietaryFiber": 0,
                "protein": 13.94,
                "fat": 7.97,
                "transFat": 0.04,
                "saturatedFat": 2.72,
                "cholesterol": 305.56,
                "natrium": 140
              }
            },
            {
              "name": "바람떡",
              "accurancy": 0.0058,
              "nutrition": {
                "oneTimeOffer": 101,
                "calrorie": 311,
                "carbohydrate": 60,
                "sugar": 12,
                "dietaryFiber": 0,
                "protein": 7,
                "fat": 2,
                "transFat": 0,
                "saturatedFat": 0,
                "cholesterol": 0,
                "natrium": 228
              }
            }
          ]
        }
      ]
    }
  ]
}

~~~

<hr>

## 음식 추천

### request
URL : 
~~~
https://bionutrion.azurewebsites.net/api/bionutrion/recomm-get
~~~

|변수명|설명|
|:-|:-|
client_id|클라이언트 ID, 사전에 협의된 클라이언트 ID 입력
client_secret| 클라이언트 secret, 사전에 협의된 클라이언트 secret 입력
gender|성별(남성 또는 여성)
age|나이
height|신장
weight|체중
activity|활동량(1단계, 2단계, 3단계, 4단계)
transFat|트랜스지방 최저값, 최대값
saturatedFat|포화지방 최저값, 최대값
sugar|당류 최저값, 최대값
calorie|칼로리 최저값, 최대값
natrium|나트륨  최저값, 최대값
protein|단백질  최저값, 최대값
nutritionBalance|탄수화물, 단백질, 지방 비율
foodPreferences|음식별 선호도


~~~
curl -X 'POST' \
  'https://bionutrion.azurewebsites.net/api/bionutrion/recomm-get' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "gender": "남성",
  "age": 30,
  "height": 180,
  "weight": 70,
  "activity": "3단계",
  "allergy": [
    "게"
  ],
  "transFat": {
    "min": -1,
    "max": 10
  },
  "saturatedFat": {
    "min": -1,
    "max": 30
  },
  "sugar": {
    "min": -1,
    "max": 20
  },
  "calorie": {
    "min": -1,
    "max": 1000
  },
  "natrium": {
    "min": -1,
    "max": 500
  },
  "protein": {
    "min": -1,
    "max": 50
  },
  "nutritionBalance": {
    "carbohydrate": 3,
    "fat": 2,
    "protein": 5
  },
  "foodPreferences": [
    {
      "id": "10576",
      "score": 0.7
    },
    {
      "id": "10575",
      "score": 1
    },
    {
      "id": "10156",
      "score": 0
    }
  ]
}'

~~~
※ transFat, saturatedFat, sugar, calorie, natrium, protein 필드의 최소값, 최대값에 -1 입력은 설정값 무시

### respnose
|변수명|설명|
|:-|:-|
errcode|API 호출 결과 코드
data|API 호출 결과

data 변수
|변수명|설명|
|:-|:-|
bodyInfo|ERR 계산값
recomms|추천결과 리스트(식품명, 영양정보, 알레르기, 밸런스 등)

~~~
{
  "errcode": 200000,
  "data": {
    "bodyInfo": {
      "eer": 2982
    },
    "recomms": [
      {
        "name": "순두부김치찌개",
        "imgLink": "",
        "calories": 70,
        "carbohydrate": 4.3,
        "sugar": 0.6,
        "protein": 6,
        "fat": 3.2,
        "saturatedFat": 0,
        "transFat": 0.9,
        "natrium": 302.02,
        "allergy": [],
        "balance": {
          "carbohydrate": 31.9,
          "fat": 23.7,
          "protein": 44.4
        }
      },
      {
        "name": "버섯샤브샤브",
        "imgLink": "",
        "calories": 105,
        "carbohydrate": 5.5,
        "sugar": 1.8,
        "protein": 13.6,
        "fat": 3.2,
        "saturatedFat": 0.1,
        "transFat": 2.2,
        "natrium": 177.59,
        "allergy": [],
        "balance": {
          "carbohydrate": 24.7,
          "fat": 14.3,
          "protein": 61
        }
      },
      {
        "name": "브로콜리볶음",
        "imgLink": "",
        "calories": 46,
        "carbohydrate": 5,
        "sugar": 1.3,
        "protein": 4,
        "fat": 1.1,
        "saturatedFat": 0,
        "transFat": 0.2,
        "natrium": 84.88,
        "allergy": [],
        "balance": {
          "carbohydrate": 49.5,
          "fat": 10.9,
          "protein": 39.6
        }
      },
      {
        "name": "버섯구이",
        "imgLink": "",
        "calories": 42,
        "carbohydrate": 3.8,
        "sugar": 0.1,
        "protein": 4.1,
        "fat": 1.1,
        "saturatedFat": 0,
        "transFat": 0.3,
        "natrium": 393.24,
        "allergy": [],
        "balance": {
          "carbohydrate": 42.2,
          "fat": 12.2,
          "protein": 45.6
        }
      },
      {
        "name": "사골국",
        "imgLink": "",
        "calories": 221,
        "carbohydrate": 11.2,
        "sugar": 0,
        "protein": 22.2,
        "fat": 9.7,
        "saturatedFat": 0.3,
        "transFat": 3.8,
        "natrium": 298.77,
        "allergy": [],
        "balance": {
          "carbohydrate": 26,
          "fat": 22.5,
          "protein": 51.5
        }
      },
      {
        "name": "유산슬",
        "imgLink": "",
        "calories": 189,
        "carbohydrate": 9,
        "sugar": 4.7,
        "protein": 16.6,
        "fat": 9.7,
        "saturatedFat": 0.1,
        "transFat": 1.7,
        "natrium": 463.88,
        "allergy": [],
        "balance": {
          "carbohydrate": 25.5,
          "fat": 27.5,
          "protein": 47
        }
      },
      {
        "name": "미트볼조림",
        "imgLink": "",
        "calories": 331,
        "carbohydrate": 19.4,
        "sugar": 15.8,
        "protein": 27.2,
        "fat": 16.1,
        "saturatedFat": 0.1,
        "transFat": 3.2,
        "natrium": 472.37,
        "allergy": [],
        "balance": {
          "carbohydrate": 30.9,
          "fat": 25.7,
          "protein": 43.4
        }
      },
      {
        "name": "버섯조림",
        "imgLink": "",
        "calories": 91,
        "carbohydrate": 9.3,
        "sugar": 2.9,
        "protein": 6.6,
        "fat": 3,
        "saturatedFat": 0.1,
        "transFat": 2.2,
        "natrium": 452.58,
        "allergy": [],
        "balance": {
          "carbohydrate": 49.2,
          "fat": 15.9,
          "protein": 34.9
        }
      },
      {
        "name": "빙그레 tft 더단백 마일드바 아몬드쿠키 9p, 1개, 450g",
        "imgLink": "https://thumbnail10.coupangcdn.com/thumbnails/remote/230x230ex/image/retail/images/2022/10/07/11/6/ff67434e-2116-4b0b-a886-09526cf4f15e.png",
        "calories": 220,
        "carbohydrate": 22,
        "sugar": 0.7,
        "protein": 15,
        "fat": 8,
        "saturatedFat": 3,
        "transFat": 0,
        "natrium": 170,
        "allergy": [
          "우유",
          "대두",
          "밀"
        ],
        "balance": {
          "carbohydrate": 48.9,
          "fat": 17.8,
          "protein": 33.3
        }
      },
      {
        "name": "대상웰라이프 마이밀 뉴프로틴 딥초코, 30p, 190ml",
        "imgLink": "https://thumbnail6.coupangcdn.com/thumbnails/remote/230x230ex/image/retail/images/5230369718431063-4274919b-a5cd-49d2-a0c9-c5a24d6b0825.jpg",
        "calories": 150,
        "carbohydrate": 15,
        "sugar": 8,
        "protein": 9,
        "fat": 6,
        "saturatedFat": 1,
        "transFat": 0,
        "natrium": 150,
        "allergy": [
          "우유",
          "대두"
        ],
        "balance": {
          "carbohydrate": 50,
          "fat": 20,
          "protein": 30
        }
      },
      {
        "name": "대상웰라이프 마이밀 뉴프로틴 오리지널, 190ml, 30개",
        "imgLink": "https://thumbnail10.coupangcdn.com/thumbnails/remote/230x230ex/image/retail/images/4277292443701791-480ec440-6f8a-4ee7-afff-029ad4287085.jpg",
        "calories": 150,
        "carbohydrate": 15,
        "sugar": 10,
        "protein": 9,
        "fat": 6,
        "saturatedFat": 1,
        "transFat": 0,
        "natrium": 150,
        "allergy": [
          "대두",
          "우유",
          "땅콩",
          "호두",
          "잣"
        ],
        "balance": {
          "carbohydrate": 50,
          "fat": 20,
          "protein": 30
        }
      },
      {
        "name": "베리오트리코타&치킨샐러드",
        "imgLink": "https://cdn.paris.spl.li/wp-content/uploads/2023/03/베리오트-리코타치킨샐러드_정방형-600x600.jpg",
        "calories": 170,
        "carbohydrate": 6,
        "sugar": 6,
        "protein": 11,
        "fat": 2.8,
        "saturatedFat": 2.8,
        "transFat": 0,
        "natrium": 250,
        "allergy": [
          "우유",
          "토마토",
          "계란",
          "대두",
          "닭고기"
        ],
        "balance": {
          "carbohydrate": 30.3,
          "fat": 14.1,
          "protein": 55.6
        }
      },
      {
        "name": "잇메이트 저염 스팀 닭가슴살 오리지널 100g",
        "imgLink": "https://file.rankingdak.com/image/RANK/PRODUCT/PRD001/20220325/4acc6d30867ae4fdd77fdf665c1d41f8_330_330.jpg",
        "calories": 155,
        "carbohydrate": 5,
        "sugar": 5,
        "protein": 20,
        "fat": 6,
        "saturatedFat": 1,
        "transFat": 0,
        "natrium": 80,
        "allergy": [
          "우유",
          "대두",
          "닭고기"
        ],
        "balance": {
          "carbohydrate": 16.1,
          "fat": 19.4,
          "protein": 64.5
        }
      },
      {
        "name": "베노프 20바 인절미 프로틴바 12p, 708g, 1개",
        "imgLink": "https://thumbnail10.coupangcdn.com/thumbnails/remote/230x230ex/image/rs_quotation_api/bc44ts45/65d1f44bb07242dfb1121a732fc693c6.jpg",
        "calories": 199,
        "carbohydrate": 23,
        "sugar": 4.2,
        "protein": 20,
        "fat": 6,
        "saturatedFat": 0.9,
        "transFat": 0,
        "natrium": 199,
        "allergy": [
          "대두",
          "우유",
          "난류"
        ],
        "balance": {
          "carbohydrate": 46.9,
          "fat": 12.2,
          "protein": 40.8
        }
      },
      {
        "name": "쉬림프 코코넛 샐러드 밀 박스",
        "imgLink": "https://image.istarbucks.co.kr/upload/store/skuimg/2021/04/[9300000002304]_20210421171643703.jpg",
        "calories": 147,
        "carbohydrate": 10,
        "sugar": 5,
        "protein": 11,
        "fat": 7,
        "saturatedFat": 5,
        "transFat": 0,
        "natrium": 330,
        "allergy": [
          "대두",
          "우유",
          "알류",
          "토마토",
          "새우"
        ],
        "balance": {
          "carbohydrate": 35.7,
          "fat": 25,
          "protein": 39.3
        }
      },
      {
        "name": "맛있닭 닭가슴살 스테이크 오리지널 100g",
        "imgLink": "https://file.rankingdak.com/image/RANK/PRODUCT/PRD001/20220510/IMG1652kJD147903763_330_330.jpg",
        "calories": 165,
        "carbohydrate": 8,
        "sugar": 6,
        "protein": 20,
        "fat": 6,
        "saturatedFat": 1,
        "transFat": 0,
        "natrium": 390,
        "allergy": [
          "우유",
          "대두",
          "밀",
          "토마토",
          "닭고기",
          "쇠고기"
        ],
        "balance": {
          "carbohydrate": 23.5,
          "fat": 17.6,
          "protein": 58.8
        }
      },
      {
        "name": "프로틴방앗간 블론디오트 하루 단백바, 1개, 45g",
        "imgLink": "https://thumbnail7.coupangcdn.com/thumbnails/remote/230x230ex/image/retail/images/2023/01/05/12/1/d1916d21-98f6-484b-8095-f31e2ef6bb3b.jpg",
        "calories": 142.6,
        "carbohydrate": 18,
        "sugar": 3,
        "protein": 12,
        "fat": 8,
        "saturatedFat": 1.7,
        "transFat": 0,
        "natrium": 70,
        "allergy": [
          "대두",
          "우유",
          "땅콩"
        ],
        "balance": {
          "carbohydrate": 47.4,
          "fat": 21.1,
          "protein": 31.6
        }
      },
      {
        "name": "myprotein 마이프로틴 단백질 초콜릿 와퍼 42g 10개 Protein Wafer Chocolate",
        "imgLink": "https://thumbnail9.coupangcdn.com/thumbnails/remote/230x230ex/image/vendor_inventory/4ba7/6538d714703be6f678ba1f5485a64e63574be8992a4addf4880476ddb525.jpg",
        "calories": 195,
        "carbohydrate": 13,
        "sugar": 5.5,
        "protein": 15,
        "fat": 9,
        "saturatedFat": 6,
        "transFat": 0,
        "natrium": 210,
        "allergy": [
          "우유",
          "밀",
          "대두"
        ],
        "balance": {
          "carbohydrate": 35.1,
          "fat": 24.3,
          "protein": 40.5
        }
      },
      {
        "name": "하림)닭가슴바오리지널80g",
        "imgLink": "https://tqklhszfkvzk6518638.cdn.ntruss.com/product/8801492375384.jpg",
        "calories": 120,
        "carbohydrate": 3,
        "sugar": 1,
        "protein": 15,
        "fat": 4.8,
        "saturatedFat": 1.8,
        "transFat": 0,
        "natrium": 470,
        "allergy": [
          "닭고기",
          "대두",
          "우유"
        ],
        "balance": {
          "carbohydrate": 13.2,
          "fat": 21.1,
          "protein": 65.8
        }
      },
      {
        "name": "이지푸드 [이지푸드] 한끼뚝닭 리얼 닭가슴살 쉐이크 혼합(16팩)(고소 새콤), 단일선택, 단일선택",
        "imgLink": "https://thumbnail6.coupangcdn.com/thumbnails/remote/230x230ex/image/vendor_inventory/24b3/a77214346ca91bb92915fcfe972a06f622281782cde227091b84d1a1c620.jpg",
        "calories": 200,
        "carbohydrate": 9.8,
        "sugar": 8.9,
        "protein": 23.5,
        "fat": 7.5,
        "saturatedFat": 1.2,
        "transFat": 0,
        "natrium": 137,
        "allergy": [
          "닭고기",
          "호두"
        ],
        "balance": {
          "carbohydrate": 24,
          "fat": 18.4,
          "protein": 57.6
        }
      }
    ]
  }
}
~~~