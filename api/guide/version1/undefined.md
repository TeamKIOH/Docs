---
description: Mora Api 타자번역 입니다.
---

# ⌨️ 타자번역

## 타자번역 <a href="#undefined" id="undefined"></a>

* 출처 : https://npmjs.com/package/inko

### Templates

* API는 모두 GET 메서드를 사용합니다

## 영어 타자 → 한글 타자 <a href="#undefined" id="undefined"></a>

* GET URL : https://api.mora-bot.kr/v1/en2ko?text={한글 타자로 변환할 문장}

| Field  | Type   | Description |
| ------ | ------ | ----------- |
| origin | String | 호출된 문장      |
| result | String | 변환된 문장      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "license":"inko module used https://www.npmjs.com/package/inko",
    "status":200,
    "origin":"ahfk",
    "result":"모라",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/en2ko?text=${encodeURI(`택스트`)}`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
        console.log(`입력된 값 : ${json.origin}`);
        console.log(`한글 타자로 : ${json.result}`);
    });

// request
let api_url = `https://api.mora-bot.kr/v1/en2ko?text=${encodeURI(`텍스트`)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`입력된 값 : ${json.origin}`);
        console.log(`한글 타자로 : ${json.result}`);
    } else {
        console.log('error = ' + response.errorcode);
    }
});
```
{% endcode %}

### Python

{% code lineNumbers="true" %}
```python
import requests

response = requests.get("http://api.mora-bot.kr/v1/en2ko?text=[텍스트]")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}

## 한글 발음 → 영어 발음 <a href="#undefined" id="undefined"></a>

* GET URL : https://api.mora-bot.kr/v1/ko2en?text={영어 타자로 변환할 문장}

| Field  | Type   | Description |
| ------ | ------ | ----------- |
| origin | String | 호출된 문장      |
| result | String | 변환된 문장      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "license":"inko module used https://www.npmjs.com/package/inko",
    "status":200,
    "origin":"모라",
    "result":"ahfk",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/ko2en?text=${encodeURI(`텍스트`)}`)
    .then(res => res.json())
    .then(json => {
        console.log(json
        console.log(`입력된 값 : ${json.origin}`);
        console.log(`한글 타자로 : ${json.result}`);
    });

// request
let api_url = `https://api.mora-bot.kr/v1/ko2en?text=${encodeURI(`텍스트`)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`입력된 값 : ${json.origin}`);
        console.log(`한글 타자로 : ${json.result}`);
    } else {
        console.log('error = ' + response.errorcode);
    }
});
```
{% endcode %}

### Python

{% code lineNumbers="true" %}
```python
import requests

response = requests.get("https://api.mora-bot.kr/v1/ko2en?text=[텍스트]")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
