---
description: Mora Api 글자뒤집기 입니다.
---

# 글자뒤집기

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/reverse?text={뒤집을 글자}

| Field    | Type   | Description |
| -------- | ------ | ----------- |
| original | String | 호출된 문장      |
| result   | String | 반환된 문장      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status":200,
    "original":"안녕",
    "result":"녕안",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
let text = '뒤집을 텍스트';
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/reverse?text=${encodeURI(text)}`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
        console.log(`뒤집기 전 : ${json.original}`);
        console.log(`뒤집은 후 : ${json.result}`);
    });

// request
let text = '뒤집을 텍스트'
let api_url = `https://api.mora-bot.kr/v1/reverse?text=${encodeURI(text)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`뒤집기 전 : ${json.original}`);
        console.log(`뒤집은 후 : ${json.result}`);
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

response = requests.get("https://api.mora-bot.kr/v1/reverse?text=ThankYou")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
