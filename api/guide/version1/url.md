---
description: Mora Api URL단축 입니다.
---

# URL단축

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/shorten?url={단축할 URL}

| Field    | Type   | Description |
| -------- | ------ | ----------- |
| url      | String | 반환된 단축 URL  |
| code     | String | 반환된 단축 코드   |
| original | String | 호출된 URL     |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "message":"successfully registered link",
    "status":200,
    "url":"https://mora-bot.kr/u/Qjadtj3",
    "code":"Qjadtj3",
    "original":"https://mora-bot.kr",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
let link = '단축할 URL'
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/shorten?url=${encodeURI(link)}`)
    .then(res => res.json())
    .then(json => {
        console.log(`원래 링크 : ${json.original}`)
        console.log(`변환된 링크 : ${json.url}`)
        console.log(`URL 해시 : ${json.code}`)
    });

// request
let link = '단축할 URL'
let api_url = `https://api.mora-bot.kr/v1/shorten?url=${encodeURI(link)}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`원래 링크 : ${json.original}`)
        console.log(`변환된 링크 : ${json.url}`)
        console.log(`URL 해시 : ${json.code}`)
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

response = requests.get("https://api.mora-bot.kr/v1/shorten?url=https://mora-bot.kr")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
