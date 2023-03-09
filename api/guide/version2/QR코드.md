---
description: Mora Api QR코드 입니다.
---

# QR코드

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/qr?url=\[링크]

| Field | Type   | Description |
| ----- | ------ | ----------- |
| Image | String | 반환된 QR URL  |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "Image": "https://chart.googleapis.com/chart?cht=qr&chl=https%3A%2F%2Fmora-bot.kr&chs=480x480&choe=UTF-8&chld=L|1",
    "success": true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/qr?url=[링크]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/qr?url=[링크]`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`QRLINK : ${json.Image}`);
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

response = requests.get("https://api.mora-bot.kr/v2/qr?url=[링크]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
