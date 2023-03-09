---
description: Mora Api 캡챠 입니다.
---

# 캡챠

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/captcha

| Field    | Type   | Description    |
| -------- | ------ | -------------- |
| img\_url | String | 반환된 캡챠 이미지 URL |
| code     | String | 반환된 캡챠 코드      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "Description": "캡챠가 정상적으로 호출되었습니다.",
    "img_url": "http://api.mora-bot.kr/v2/captcha/IuVRKhvw6v",
    "code": "680747"
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/captcha`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/captcha`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`반환값 : ${json}`);
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

response = requests.get("https://api.mora-bot.kr/v2/captcha")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
