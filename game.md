## 游戏 js 调用Android 方法

js方法
```
var game={
    "action":1,
    "jumpUrl":"",
    "msg":"",
    "actionType":0,
    "adType":1
}
game为String类型,其中actionType：播放视频要分 离线  扭蛋 免费鱼干 打卡 加速做区分
window.android.callAndroid(game);
action==1时，全屏视频广告播放,action==2时， 触发底部banner广告,
action==3时分享调起，action==4时网页调起，
action==5时，收益的dialog，
action==6时，红包列表dialog
action==7时，2小时更新的金鱼干
action==8时，撸猫指南
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
    "adId":""
}
adType:{
0=视频广告观看完毕，
1= 未看完，
}
game字符串，游戏返回什么，执行完成以后，直接返回回调给游戏，增加广告观看状态
```
