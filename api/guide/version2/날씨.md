---
description: Mora Api 날씨 입니다.
---

# 날씨

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/weather?area=\[지역]

| Field                | Type   | Description |
| -------------------- | ------ | ----------- |
| time                 | String | 조회된 지역 시간   |
| Temperature          | String | 조회된 지역 온도   |
| windchilltemperature | String | 조회된 지역 체감온도 |
| wind                 | String | 조회된 지역 풍향   |
| Humidity             | String | 조회된 지역 습도   |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "time": "GMT-9",
    "Temperature": "5°",
    "windchilltemperature": "2°",
    "wind": "18 km/h Northwest",
    "Humidity": "75%",
    "success": true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/weather?area=[지역]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/weather?area=[지역]`
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

response = requests.get("https://api.mora-bot.kr/v2/weather?area=[지역]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
