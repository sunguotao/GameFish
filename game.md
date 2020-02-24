## 游戏 js 调用Android 方法

js方法
```
var game={
    "action":1,
    "jumpUrl":"",
    "msg":"",
    "actionType":0,
    "adType":1,
    "fishDried":12,
    "data":{
        "redpackageUrl":"https://xiao.11478.com/appgame/redpackage.png",
        "taskName":"猫咪升级红包",
        "desc":"随机5-50元红包",
        "type":0
        "score":6.48,
        "id":""
    },
    "ad_data":{
        "id":0,
        "title":"离线奖励",
        "leftBtn":"立即领取",
        "rightBtn":"观看视频翻倍",
        "updateVideoCountInfo":"每天晚上20点整重置视频次数(剩余15次)",
        "addCoins":"+36.0m",
        "offline":"离线奖励上线为两个小时，当前已经离线36分钟"
    }
}
game为String类型,其中actionType：播放视频要分 离线  扭蛋 免费鱼干 打卡 加速做区分
window.android.callAndroid(game);
action==1时，全屏视频广告播放,action==2时， 触发底部banner广告,
action==3时分享调起，action==4时网页调起，
action==5时，收益的dialog，
action==6时，红包列表dialog
action==7时，2小时更新的金鱼干
action==8时，撸猫指南
action==9时，合成红包，data需要数据(type==0是常规领取红包，type==1时，用户分享成功后，领取红包，type==2时，用户看广告视频，领取红包)
action==10时，公告
action==11时，获取分辨率
action==12时，跳转到我的资产（金鱼干界面）
action==13时，打开广告模式（led模式）需要传递ad_data数据(addCoins,updateVideoCountInfo,rightBtn)
action==14时，打开广告模式(离线 ,打卡 ,免费银鱼干) 对应显示的数据需要显示
action==15时，是幸运转盘之后获得奖励的界面，显示内容有 银鱼干，金鱼干，和喵力，对应数据显示
待定
```
```js
## Android 调用 js  方法

js方法
```
  function callByAndroidInteraction(msg){
    
  }
```
```js
var game={
    "action":1,
    "jumpUrl":"",
    "msg":"",
    "actionType":0,
    "adType":1,
    "adId":"",
    "screenWidth":720,
    "screenHeight":1980
}
adType:{
0=视频广告观看完毕，
1= 未看完，
}
action:{
101=分辨率上传，
102=金鱼干收取成功，
103=红包领取成功，
104=游戏界面显示，
105=游戏界面隐藏，
106=离线 打卡 免费银鱼干有这种广告类型，按钮点击领取奖励回调
}
game字符串，游戏返回什么，执行完成以后，直接返回回调给游戏，增加广告观看状态
```
