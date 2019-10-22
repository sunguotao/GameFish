# GameFish
## 用户系统

### 微信登陆
```
POST /user/loginByWechat
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| code          | string   | 微信登录前端返回的校验码                     | 是               |

###返回数据
```js
{
    "code":0,
    "data":{
        "token":"ud129vsdf12efgfs102",
        "id":1,
        "nickname":"System",
        "sex":0,
        "avatar":"https://static.xxxxxx.com/avatar/avatar0.png",
        "hasInitPassword":false,
        "invitationCode":"R8Gkd",
        "phone":"13800000000",
        "qq":"13023120",
        "wechat":"",
        "isPrivacyVisibleToChild":false,
        "isPrivacyVisibleToFather":false,
        "isPrivacyVisibleToGrandfather":false,
        "isIsVerified":false
    },
    "msg":"请求成功",
    "success":true
}
```


