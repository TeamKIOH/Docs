---
description: Mora Api 캡챠 입니다.
---

# 🔒 캡챠

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/captcha

| Field | Type   | Description     |
| ----- | ------ | --------------- |
| url   | String | 이미지 주소를 반환한 URL |
| code  | String | 캡챠코드를 반환        |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "message":"captcha image and code was returned",
    "status":200,
    "url":"https://dummyimage.com/2000x500/ffffff/33363c&text=snZojQ",
    "code":"snZojQ",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch('https://api.mora-bot.kr/v1/captcha')
    .then(res => res.json())
    .then(json => {
        let imgurl = json.url;
        let code = json.code;
        console.log(json)
    });

// request
let api_url = 'https://api.mora-bot.kr/v1/captcha'
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let imgurl = JSON.parse(body).url;
        let code = JSON.parse(body).code;
        console.log(imgurl, code)
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

response = requests.get("https://api.mora-bot.kr/v1/captcha")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
