---
description: Mora Api 깃허브 입니다.
---

# 깃허브

### Templates

* API는 모두 GET 메서드를 사용합니다
* GET URL : https://api.mora-bot.kr/v2/github/\[조회할유저 닉네임]

| Field        | Type   | Description       |
| ------------ | ------ | ----------------- |
| name         | String | 호출된 계정의 이름        |
| nickname     | String | 호출된 계정의 닉네임       |
| url          | String | 호출된 계정의 링크        |
| company      | String | 호출된 계정의 소속회사      |
| area         | String | 호출된 계정의 지역        |
| email        | String | 호출된 계정의 이메일       |
| introduction | String | 호출된 계정의 소개        |
| id           | Number | 호출된 계정의 생성시간      |
| node         | String | 호출된 계정의 고유코드      |
| gravatar     | String | 호출된 계정의 아바타       |
| followers    | String | 호출된 계정을 팔로우한 수    |
| following    | String | 호출된 계정의 팔로윙한 수    |
| twitter      | String | 호출된 계정의 트위터       |
| avatarurl    | String | 호출된 계정의 아바타 URL   |
| type         | String | 호출된 계정의 계정타입      |
| creation     | String | 호출된 계정의 계정생성일     |
| update       | String | 호출된 계정의 마지막 업데이트일 |

{% code lineNumbers="true" %}
```json
// 응답 내용
{
    "message": "Return succeeded.",
    "status": 200,
    "name": "erukim",
    "nickname": "이루",
    "url": "https://github.com/erukim",
    "company": "@hiplaygit ",
    "area": null,
    "email": null,
    "introduction": "방송을 하면서 개발과 온라인사업을 하는 이루입니다.\r\n@Dev-Korea-Server @MORA-Team @Team-Laon @Team-Social-Dev ",
    "info": {
        "id": 100296449,
        "node": "U_kgDOBfpnAQ",
        "gravatar": ""
    },
    "followers": 5,
    "following": 6,
    "twitter": null,
    "avatarurl": "https://avatars.githubusercontent.com/u/100296449?v=4",
    "type": "User",
    "creation": "2022-02-23T14:46:16Z",
    "update": "2022-11-09T14:29:24Z",
    "success": true
}
```
{% endcode %}

### NodeJS

{% code lineNumbers="true" %}
```javascript
// node-fetch
const fetch = require('node-fetch')
fetch(`https://api.mora-bot.kr/v2/github/[조회할유저 닉네임]`)
    .then(res => res.json())
    .then(json => {
        console.log(json)
    });

// request
const request = require('request');
let options = {
    url: `https://api.mora-bot.kr/v2/github/[조회할유저 닉네임]`
}
request.get(options, function (error, response, body) {
    if (!error && response.status == 200) {
        let json = JSON.parse(body)
        console.log(`조회값 : ${json}`);
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

response = requests.get("https://api.mora-bot.kr/v2/github/[조회할유저 닉네임]")
result = response.json()

if response.status_code == 200:
  print(result)
else:
  print(f"Error Code: {result['status']}")
```
{% endcode %}
