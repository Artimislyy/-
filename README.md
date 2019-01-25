**微信小程序第一周总结**  
总结人：陈曦  

**wx.getImageInfo(Object object)获取图片信息**  
在小程序/小游戏中使用网络相关的 API 时，每个微信小程序需要事先设置一个通讯域名，小程序只可以跟指定的域名与进行网络通信。包括普通 HTTPS 请求（wx.request）、上传文件（wx.uploadFile）、下载文件（wx.downloadFile) 和 WebSocket 通信（wx.connectSocket）。这里是下载图片的请求，所以需要对wx.downloadFile进行配置。  
```
Index.js文件代码如下：  
const app = getApp()  

Page({  

data: {  
src: 'https://mmbiz.qpic.cn/mmbiz_png/icTdbqWNOwNTTiaKet81gQJDXYnPiaJFSzRlp9frTTX2hSN01xhiackVLHHrG7ZQI3XQsbM7Gr9USZdN4f26SO5xjg/0?wx_fmt=png',
info: '',  
},  

getImageInfo() {
wx.getImageInfo({
src: this.data.src,
complete: (res) => {
this.setData({
info: this.format(res)
})
}
})
},
format(obj) {
return '{\n' +
Object.keys(obj).map(function (key) { return ' ' + key + ': ' + obj[key] + ',' }).join('\n') + '\n' +
'}'
}
})
```
