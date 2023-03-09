---
description: Mora Api 가사 입니다.
---

# 가사

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v3/lyrics/\[가수]/\[제목]

| Field  | Type   | Description |
| ------ | ------ | ----------- |
| singer | String | 반환된 가수      |
| title  | String | 반환된 제목      |
| lyrics | String | 반환된 가사      |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status": 200,
    "singer": "아이유",
    "title": "잔소리",
    "lyrics": "가사내용"
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v3/lyrics/[가수]/[제목]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v3/lyrics/[가수]/[제목]`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`가사 : ${json.lyrics}`);
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

response = requests.get("https://api.mora-bot.kr/v3/lyrics/[가수]/[제목]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
