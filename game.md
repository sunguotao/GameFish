## 游戏 js 调用Android 方法

js方法
```
var game={
    "action":1,
    "jumpUrl":"",
    "msg":"",
    "prizeType":1
}
game为String类型
window.android.callAndroid(game);
action==1时，全屏视频广告播放,action==2时， 触发底部banner广告,
action==3时分享调起，action==4时网页调起，
action==5时，收益的dialog，
action==6时，红包列表dialog
待定
```
```js
