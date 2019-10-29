# 通用接口说明

####  所有请求需要校验，详⻅校验请求头说明，校验失败的请求返回 401 的HTTP状态码，所有POST 请求数据只支持 JSON 格式，请求数据需要经过 DES 加密处理，加密密钥需要在请求时生成，
#### 参考:加密解密，参考趣钱进加密方式，所有接口响应中都含有基础响应数据。 如果用户登录成功，需要在使用 token 字段在 Header 带上 token 值

## 校验请求头说明
### 字段说明

 sign 加密方式参考趣钱进方式
 
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| sign          | string   | 加密数据                    | 是               |
| timestamp          | string   | 时间戳                  | 是               |
| randomNum          | string   | 随机数，32位                    | 是               |

## 基础数据说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| code          | int   | 状态码，0:数据返回成功，401 校验失败，402，token失效重新登陆                   | 是               |
| data          | object   | 返回的数据                 | 是               |
| msg          | string   | 详细相应描述                    | 是               |
| success          | boolean   | 请求是否成功，true/false                   | 是               |
| encrydata          | string   | 加密的数据                   | 是               |
| timestamp          | string   | 时间戳                   | 是               |
| nonce          | string   | 随机数                  | 是               |

```js
{
    "code":0,
    "data":{
        "encrydata":"ud129vsdf12efgfs102",
        "timestamp":4343434343434343,
        "nonce":"54545454"
    },
    "msg":"请求成功",
    "success":true
}
```

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
### 修改昵称{# user/updateNickName}

后端需要根据请求头中的`token`鉴权

### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| nickname          | string   |  昵称                     | 是               |
```
POST user/updateNickNam
```
```js
{
    "code":0,
    "data":null,
    "msg":"修改成功",
    "success":true
}

```

###  瞄圈主页{# user/index}

后端需要根据请求头中的`token`鉴权
```
POST user/index
```
```js
{
    "code":0,
    "data":{
        "catForce":1000,
        "wealthCarProgress":"23.6%",
        "wealthCarInfo":"限量10万只招财猫进度完成100%必得一只",
        "targetEarn":200,
        "activityEarn":50,
        "wealthCarEarn":70,
        "wealthCarTitle":"一星挑战"
    },
    "msg":"修改成功",
    "success":true
}
```


### test{#test.json}

后端需要根据请求头中的`token`鉴权
```
POST /funcSwitch/getAll.json
```
```js
```

