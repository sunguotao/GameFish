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
        "catForce":3000,
        "fishDried ":"800.2",
        "wealthCatProgress":"23.6%",
        "wealthCatInfo":"限量10万只招财猫进度完成100%必得一只",
        "targetEarn":200,
        "activityEarn":50,
        "wealthCatEarn":70,
        "wealthCatTitle":"一星挑战",
        "targetProgress":"73%",
        "speedUp":"x1.1倍加速中",
        "catLevel":1
    },
    "msg":"修改成功",
    "success":true
}
```
### 我的钱包{# user/wallet}

后端需要根据请求头中的`token`鉴权
```
POST user/wallet
```
```js
{
    "code":200,
    "data":{
        "walletMoney":0,
        "cashType":"weChat",
        "walletList":[
            "0.3",
            "20",
            "30",
            "40",
            "50",
            "100",
            "200"
        ]
    },
    "msg":"请求成功",
    "success":true
}
```
### 零钱记录{# user/extractCash}

后端需要根据请求头中的`token`鉴权
```
POST user/extractCash
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| pageSize          | int   | pageSize                   | 否（默认20）               |
| pageNum          | int   | pageNum                | 否（默认1）               |

```js
{
    "code":200,
    "data":[
        {
            "time":64565757765,
            "cash":12,
            "info":"现金提取"
        }
    ],
    "msg":"修改成功",
    "success":true
}
```
### 提取现金 {# user/putForwardCash}

后端需要根据请求头中的`token`鉴权
```
POST user/putForwardCash
```

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| cashType          | string   | 微信weChat                     | 是               |
| cash          | string   | 现金                    | 是               |
```js
{
    "code":200,
    "data":null,
    "msg":"提取成功",
    "success":true
}
```
### 我的邀请码界面{# user/invitationInfo}

后端需要根据请求头中的`token`鉴权
```
POST user/invitationInfo
```
```js
{
    "code":200,
    "data":{
        "allForce":20,
        "childNum":10,
        "grandsonNum":10,
        "childForce":10,
        "grandsonForce":10,
        "invitationUrl":"http://url.com"
    },
    "msg":"请求成功",
    "success":true
}
```
### 我的资产{# user/myAssetsList}

后端需要根据请求头中的`token`鉴权
```
POST user/myAssetsList
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| pageSize          | int   | pageSize                   | 否（默认20）               |
| pageNum          | int   | pageNum                | 否（默认1）               |
| type          | int   | 3：金鱼干；4：瞄力；5:招财猫               | 是               |

```js
{
    "code":200,
    "data":[
        {
            "score":10,
            "info":"title",
            "time":65655656
        }
    ],
    "msg":"请求成功",
    "success":true
}

```
### 我的瞄友圈（徒弟，徒孙，待激活）{# user/myCatCircle}

后端需要根据请求头中的`token`鉴权
```
POST user/myCatCircle
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| pageSize          | int   | pageSize                   | 否（默认20）               |
| pageNum          | int   | pageNum                | 否（默认1）               |
| type          | int   | 0：徒弟；1：徒孙；2:待激活               | 是               |
```js
{
    "code":200,
    "data":[
        {
            "userName":"userName",
            "level":"title",
            "time":65655656,
            "stateType":0
        }
    ],
    "msg":"请求成功",
    "success":true
}
stateType 0:待激活，1:已激活
```

### 我的师傅{# user/myTeacher}

后端需要根据请求头中的`token`鉴权
```
POST /funcSwitch/getAll.json
```
```js
{
    "code":200,
    "data":{
        "id":124343,
        "mobile":18653076099,
        "nickname":"nickname",
        "avatar":"http://4teyrtytry.com",
        "level":"24",
        "isLike":false
    },
    "msg":"请求成功",
    "success":true
}
```
### 给师傅点赞，取消点赞{# user/myTeacherIsLike}

后端需要根据请求头中的`token`鉴权
```
POST /funcSwitch/getAll.json
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| id          | string   | 师傅id                   | 是             |
| isLike          | boolean   | true,false                | 是               |
```js
{
    "code":200,
    "data":null,
    "msg":"点赞成功",
    "success":true
}
```
### 实名认证数据提交{# user/authRealName}

后端需要根据请求头中的`token`鉴权
```
POST user/authRealName
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| userName          | string   | userName                | 是             |
| userID          | string   | userID               | 是               |
```js
{
    "code":200,
    "data":null,
    "msg":"提交成功",
    "success":true
}
```
### 获取实名认证信息{# user/getAuthRealName}

后端需要根据请求头中的`token`鉴权
```
POST user/getAuthRealName
```
```js
{
    "code":200,
    "data":{
        "userName":"孙国涛",
        "userID":"329687874535946946"
    },
    "msg":"返回成功",
    "success":true
}
```
### 我的收益{# user/earnList}

后端需要根据请求头中的`token`鉴权
```
POST  user/earnList
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| pageSize          | int   | pageSize                   | 否（默认20）               |
| pageNum          | int   | pageNum                | 否（默认1）               |
```js
{
    "code":200,
    "data":[
        {
            "time":54544546464,
            "activityEarn":1.3,
            "wealthCatEarn":2.3
        }
    ],
    "msg":"返回成功",
    "success":true
}
```
### 版本更新{# user/versionUpdate}

后端需要根据请求头中的`token`鉴权
```
POST user/versionUpdate
```
```js
{
    "code":200,
    "data":{
        "downloadUrl":"",
        "downloadMsg":"1:fix bug\n2:  用户数据修改",
        "downloadFileSize":"100M",
        "forcedUpdate":true,
        "versionName":1,
        "versionCode":1
    },
    "msg":"返回成功",
    "success":true
}
```
### 收益记录详情{# user/earnHistoryInfo}

后端需要根据请求头中的`token`鉴权
```
POST user/earnHistoryInfo
```
```js
{
    "code":0,
    "data":{
        "catEarthYesterdayEarn":1243,
        "catEarthYesterdayHistoryEarn":1243,
        "yesterdayWealthCatNum":10,
        "allWealthCatNum":100,
        "nowWealthCatNum":2,
        "futureWealthCatNum":10,
        "list":[
            {
                "nickname":"nickname",
                "info":"info",
                "time":124243433
            }
        ]
    },
    "msg":"success",
    "success":true
}
```
### 发送验证码{# sendSms}

后端需要根据请求头中的`token`鉴权
```
POST sendSms
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| type          | int   | 0:绑定手机号码                   | 是               |
| phoneNum          | int   | 手机号码                   | 是               |
```js
{
    "code":200,
    "data":null,
    "msg":"发送成功",
    "success":true
}
```
### 绑定手机号码{# bindPhone}

后端需要根据请求头中的`token`鉴权
```
POST bindPhone
```
| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| code          | int   | 验证码                   | 是               |
| phoneNum          | int   | 手机号码                   | 是               |
```js
userInfo 返回的数据
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
### 红包列表{# user/redPacketList}

后端需要根据请求头中的`token`鉴权
```
POST user/redPacketList
```
```js
{
    "code":0,
    "data":[
        {
            "redPackketId":12,
            "redPackketImgUrl":"",
            "redPacketTitle":"title",
            "redPacketInfo":"info",
            "fromRedPacket":"喵咪星球的红包",
            "redRedPacketintroduce":"随机红包（最高8元）",
            "redPacket":2
        }
    ],
    "msg":"请求成功",
    "success":true
}
```
### 打开红包放入钱包{# user/getRedPacket}

后端需要根据请求头中的`token`鉴权
```
POST user/getRedPacket
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| redPacketId          | String   | 红包id                | 是               |
| redPacket          | double   |  红包金额                | 是               |
```js
{
    "code":0,
    "data":null,
    "msg":"红包下发成功",
    "success":true
}
```
### 绑定邀请码（选填）{# user/bindInvitationCode}

后端需要根据请求头中的`token`鉴权
```
POST user/bindInvitationCode
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| invitationCode          | String   |邀请码                | 是               |
| phoneNum          | String   |手机号码                | 是               |
```js
{
    "code":0,
    "data":null,
    "msg":"绑定成功",
    "success":true
}
```
### 广告状态播放成功记录{# user/setAdState}

后端需要根据请求头中的`token`鉴权
```
POST user/setADstate
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| adId   | String   | 广告id| 是|
| actionType   | int   | actionType=1 离线广告 ；actionType=2 加速广告；actionType=3 扭蛋广告；actionType=4 打卡广告；actionType=5 免费鱼干广告；actionType=6 鱼篮视频奖励；actionType=7  红包视频;action==8 分享红包| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"提交成功",
    "success":true
}
``` 
### 获取广告状态{# user/getAdState}

后端需要根据请求头中的`token`鉴权
```
POST user/getADstate
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| adId   | String   | 广告id| 是|
| actionType   | int   | actionType=1 离线广告 actionType=2 加速广告actionType=3 扭蛋广告actionType=4 打卡广告actionType=5 免费鱼干广告| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"获取成功",
    "success":true
}
``` 
### 领取金鱼干{# user/takeFishDried}

后端需要根据请求头中的`token`鉴权
```
POST user/takeFishDried
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| fishDried   | int   |金鱼干| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"领取成功",
    "success":true
}
``` 
### app信息配置接口{# user/appConfig}

后端需要根据请求头中的`token`鉴权
```
POST user/appConfig
```
```js
{
    "code":0,
    "data":{
        "gameUrl":"http://192.168.2.27:7456/build/"
    },
    "msg":"领取成功",
    "success":true
}
```
### 公告{# user/noticeMsg}

后端需要根据请求头中的`token`鉴权
```
POST user/noticeMsg
```
```js
{
    "code":0,
    "data":[
        {
            "noticeId":"",
            "title":"喵咪星球更新啦",
            "info":"亲爱的猫友们：bug修复，bug修复，bug修复，bug修复，",
            "time":35354545454545454,
            "author":"猫咪星球运营团队"
        }
    ],
    "msg":"领取成功",
    "success":true
}
```
### 意见反馈{# feedBack}

后端需要根据请求头中的`token`鉴权
```
POST feedBack
```


### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| feedBackMsg   | String   |意见| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"感谢收到您的意见",
    "success":true
}
```
### 广告记录{# adRecord}

后端需要根据请求头中的`token`鉴权
```
POST adRecord
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| scene   | int   |0:穿山甲；1:广点通| 是|
| type   | int   |0:激励视频；1:大图展示；2:banner；3:开屏页| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"提交成功",
    "success":true
}
```
### 注销账号{# logout}

后端需要根据请求头中的`token`鉴权
```
POST logout
```
```js
{
    "code":0,
    "data":null,
    "msg":"注销成功",
    "success":true
}
```
### 玩家补填邀请码功能{# submitTeacherCode}

后端需要根据请求头中的`token`鉴权
```
POST /submitTeacherCode
```
### 字段说明

| 参数名         | 类型            | 描述                          | 是否必须            |
| ----------- | ------------- | --------------------------- | --------------- |
| code   | String   |师傅的邀请码| 是|
```js
{
    "code":0,
    "data":null,
    "msg":"绑定成功",
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

