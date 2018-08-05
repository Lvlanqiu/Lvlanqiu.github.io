

> 很高心在github上搭建自己的博客并发布这第一篇文章。虽然只是平常工作的一点小结，但还是希望能养成总结归纳的思考习惯。


开发基于mui和H5+

## 添加全屏的mask遮罩
```
plus.webview.currentWebview().setStyle({
	mask: "rgba(0,0,0,0.4)"
});

// 动态修改Webview窗口的遮罩层
var ws=plus.webview.currentWebview();
ws.setStyle({mask:"rgba(0,0,0,0.5)"});
// 用户点击Webview窗口后不显示遮罩层
ws.addEventListener("maskClick",function(){
    ws.setStyle({mask:"none"});
},false);
```
## mui创建当前webview的mask遮罩
```
var mask = mui.createMask(callback);//callback为用户点击蒙版时自动执行的回调，可以缺省，默认点击关闭；关闭不会销毁遮罩。
mask.show();//显示遮罩
mask.close();//关闭遮罩
```
## 设置webview的上下左右边距
```
plus.webview.currentWebview().setStyle({bottom:0});
```
## 双页面下拉刷新的文字定位自定义
在父页面添加下样式
```
.mui-bar-nav ~ .mui-content .mui-pull-top-pocket {top: 205px!important;}
```
## picker控件监听按钮和点击遮罩事件
需要在控件初始化后添加下代码
```
mui(".mui-dtpicker-header ").on('tap','.mui-btn',function(){
  plus.webview.currentWebview().setStyle({top:190,bottom:110});
}) ;
mui("body").on('tap',".mui-backdrop",function(){
  plus.webview.currentWebview().setStyle({top:190,bottom:110});
})
```
## mui上下拉控件
注意需要预先初始化上下拉控件否则报错
```
//禁用上下拉：
mui("#pullrefresh").pullRefresh().setStopped(true)
//启用上下拉：
mui("#pullrefresh").pullRefresh().setStopped(false)
//隐藏更多数据提示文字
document.querySelector('.mui-pull-caption').style.display=''
```

---

结束语：感谢黄玄Hux的博客框架，受益良多。
