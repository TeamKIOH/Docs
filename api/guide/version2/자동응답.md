---
description: Mora Api 자동응답 입니다.
---

# 자동응답

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/ai?text=\[단어]

| Field   | Type   | Description |
| ------- | ------ | ----------- |
| message | String | 반환된 내용      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "message": "안녕안녕입니다🖐",
    "success": true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/ai?text=[단어]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/ai?text=[단어]`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`반환내용 : ${json.message}`);
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

response = requests.get("https://api.mora-bot.kr/v2/ai?text=[단어]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
