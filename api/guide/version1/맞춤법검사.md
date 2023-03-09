---
description: Mora Api 맞춤법검사 입니다.
---

# 맞춤법검사

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/grammar?string={검사할 문장}

| Field       | Type   | Description  |
| ----------- | ------ | ------------ |
| original    | String | 호출된 문장       |
| wrong       | String | 호출된 문장의 틀린부분 |
| suggestions | String | 호출된 문장의 추천문장 |
| more        | String | 호출된 문장의 해설   |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "message":"there is nothing wrong",
    "license":"hanspell module used https://www.npmjs.com/package/hanspell",
    "status":200,
    "original":"안녕하세요",
    "errnum":0,
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
let text = '검사할 문장'
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/grammar?string=${encodeURI(text)}`)
    .then(res => res.json())
    .then(json => {
        console.log(`라이선스 : ${json.license}`)
        console.log(`원래 문장 : ${json.original}`)
        console.log(`틀린 부분 : ${json.wrong}`)
        console.log(`추천 : ${json.suggestions}`)
        console.log(`해설 : ${json.more}`)
    });

// request
let text = '검사할 문장'
let api_url = `https://api.mora-bot.kr/v1/grammar?string=${encodeURI(text)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`라이선스 : ${json.license}`)
        console.log(`원래 문장 : ${json.original}`)
        console.log(`틀린 부분 : ${json.wrong || 0}`)
        console.log(`추천 : ${json.suggestions || '틀린 부분 없음'}`)
        console.log(`해설 : ${json.more || '틀린 부분 없음'}`)
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

response = requests.get("https:/api.mora-bot.kr/v1/grammar?string=검사할문장")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
