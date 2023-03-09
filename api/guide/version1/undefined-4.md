---
description: Mora Api 발음번역 입니다.
---

# 발음번역

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/hangulify?text={검사할 문장}

| Field    | Type   | Description |
| -------- | ------ | ----------- |
| original | String | 호출된 문장      |
| result   | String | 반환된 내용      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "license":"kpop module used https://www.npmjs.com/package/kpop",
    "status":200,
    "original":"annyeong",
    "result":"안녕",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
let text = '한국어로 발음 번역할 말';
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/hangulify?text=${encodeURI(text)}`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
        console.log(`원래 값 : ${json.original}`);
        console.log(`한글 발음화 : ${json.result}`);
    });

// request
let text = '한국어로 발음 번역할 말'
let api_url = `https://api.mora-bot.kr/v1/hangulify?text=${encodeURI(text)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`원래 값 : ${json.original}`);
        console.log(`한글 발음화 : ${json.result}`);
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

response = requests.get("https://api.mora-bot.kr/v1/hangulify?text=Juan")
result = response.json()

if response.status_code == 200:
  print(result)
  print(result['status'])
  print(result['original'])
  print(result['success'])
  print(result['result'])
  print(result['license'])
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
