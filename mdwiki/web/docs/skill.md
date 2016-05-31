# web开发

## ios系统safari浏览器div不支持click解决方案
>事件绑定时使用如下方法可将所有事件绑定在body中，能在一定程度上减少内存的开支，也更方便做监听
>`$(document.body).on("click",".btn-div",function(evt){/* do something /})`
>这种方法在PC端浏览器均能完美得到我们想要的结果，但是在IOS设置的safari浏览器中有时候却不能执行click事件
>解决方案是为对应div添加css属性 cursor:pointer; 此属性会为该div注册click事件。

## 部分安卓手机上传图片时页面会自动刷新
>原因是`input file`标签在选中文件后导致手机内存不足，webview被自动清理之后网页刷新。
