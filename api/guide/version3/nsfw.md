---
description: Mora Api NSFW 입니다.
---

# NSFW

### Templates

* API는 모두 GET 메서드를 사용합니다
* waifu 에 nsfw가 사용되었습니다.
* GET URL : https://api.mora-bot.kr/v3/nsfw

| Field | Type   | Description |
| ----- | ------ | ----------- |
| img   | String | 반환된 이미지     |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "img": "https://i.waifu.pics/"
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v3/nsfw`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v3/nsfw`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`이미지 : ${json.img}`);
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

response = requests.get("https://api.mora-bot.kr/v3/nsfw")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
