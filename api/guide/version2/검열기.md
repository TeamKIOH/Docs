---
description: Mora Api 검열기 입니다.
---

# 검열기

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/korcen?text=\[조회할 단어]

| Field   | Type    | Description |
| ------- | ------- | ----------- |
| success | Boolean | 검열여부        |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status":200,
    "success":false
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/korcen?text=[조회할 단어]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/korcen?text=[조회할 단어]`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`검열여부 : ${json.success}`);
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

response = requests.get("https://api.mora-bot.kr/v2/korcen?text=[조회할 단어]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
