---
description: Mora Api 깃허브 입니다.
---

# 깃허브

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v1/github?username=\[닉네임]

| Field        | Type   | Description       |
| ------------ | ------ | ----------------- |
| name         | String | 호출된 계정의 이름        |
| nickname     | String | 호출된 계정의 닉네임       |
| url          | String | 호출된 계정의 링크        |
| introduction | String | 호출된 계정의 소개        |
| avatarurl    | String | 호출된 계정의 아바타 URL   |
| creation     | String | 호출된 계정의 계정생성일     |
| update       | String | 호출된 계정의 마지막 업데이트일 |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "message":"Return succeeded.",
    "status":200,
    "name":"MORA-Team",
    "nickname":"모라 Team",
    "url":"https://github.com/MORA-Team",
    "introduction":null,
    "avatarurl":"https://avatars.githubusercontent.com/u/104973461?v=4",
    "creation":"2022-05-05T08:00:35Z",
    "update":"2022-08-23T23:18:26Z",
    "success":true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch('https://api.mora-bot.kr/v1/github?username=[닉네임]')
    .then(res => res.json())
    .then(json => {
        let imgurl = json.url;
        let code = json.code;
        console.log(json)
    });

// request
let api_url = 'https://api.mora-bot.kr/v1/github?username=[닉네임]'
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

response = requests.get("https://api.mora-bot.kr/v1/github?username=[닉네임]")
result = response.json()

if response.status == 200:
  print(result)
else:
  print(f"Error Code: {response.errorcode}")
```
{% endcode %}
