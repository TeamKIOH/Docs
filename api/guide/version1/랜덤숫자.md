---
description: Mora Api 랜덤숫자 입니다.
---

# 랜덤숫자

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/randomnumber?min={최소값}\&max=${최대값}

| Field   | Type   | Description |
| ------- | ------ | ----------- |
| minimum | String | 입력한 최소 수    |
| maximum | String | 입력한 최대 수    |
| result  | Number | 반환된 랜덤숫자    |
| code    | String | 숫자 지원코드     |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "status":200,
    "minimum":"1",
    "maximum":"5",
    "result":2,
    "code":"9fcbd626-eb8c-4daf-b927-f3913d19f17b",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
let min = 0;
let max = 10;
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v1/randomnumber?min=${min}&max=${max}`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
        console.log(`최소값 : ${json.minimum}`);
        console.log(`최대값 : ${json.maximum}`);
        console.log(`결과 : ${json.result}`);
    });

// request
let min = 0;
let max = 10;
let api_url = `https://api.mora-bot.kr/v1/randomnumber?min=${min}&max=${max}`
const request = require('request');
let options = {
    url: api_url
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`최소값 : ${json.minimum}`);
        console.log(`최대값 : ${json.maximum}`);
        console.log(`결과 : ${json.result}`);
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

response = requests.get("https://api.mora-bot.kr/v1/randomnumber?min=0&max=10")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
