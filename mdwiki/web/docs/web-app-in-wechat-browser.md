#微信浏览器开发实战经验

## 项目介绍：

我先简单介绍一下项目前景吧。

公司之前做APP 后来觉得app迭代太麻烦就改做webapp。

因为产品面向高校社团，主要为社团组织提供微信公众号服务，所以主要流量都来自于微信。

这个项目主要是基于微信浏览器，里面有用到很多微信提供的api，调用微信原生功能，提供更好的用户体验。

以下介绍均基于移动端微信浏览器。

首先，系统利用微信授权替代传统的用户登录步骤，确保App在初始化之前用户已登录，并且尽可能减少用户繁杂的手动操作。

了解过微信api的应该都知道微信提供了一个获取用户信息的接口：

https://open.weixin.qq.com/connect/oauth2/authorize?appid=appid&redirect_uri=redirectUrl&response_type=code&scope=snsapi_base&state=123#wechat_redirect

1.当scope参数的值为snsapi_base时，可以返回当前微信用户的基础信息，该接口不需要用户授权

2.当scope参数的值为snsapi_userinfo时，获取当前微信用户的详细信息，该信息包括头像、昵称等，但是该接口需要用户手动授权。

通过以上接口，我们实现了系统利用微信无缝登录，并且提供方法同步微信用户基础信息数据。

微信浏览器也属于移动端浏览器，所以它也一样有许多移动端浏览器需要注意的地方。

为方便调试，开发过程中基本上都是使用chrome浏览器，必要时候需要设置一下user agent为微信浏览器环境，页面开发完成后需要在微信和其他浏览器中查看效果。

微信网页开发的难点就在于调试的难度较高，很多情况下微信浏览器跟系统自带浏览器会有很多表现上的差异，这取决于浏览器的内核，也取决于微信本身对浏览器的控制（阉割）。

而且ios版和android版之间的表现都不一样。


## 目前的使用当中的细节问题：

有兴趣可以查看[JSSDK](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html)接口文档。


####1、cookie-based-session存储

我们现在的session是用localstorage本地存储的，使用的是[store.js](https://github.com/marcuswestin/store.js)，该插件会自动识别当前浏览器是否支持localstorage而去判断使用localstorage或cookie实现本地缓存。

该功能在ios设备上一切正常，但是android版微信浏中缓存时间非常短（几分钟的样子），因此安卓手机经常需要重新创建session并登陆。

好在项目采用的是单页webapp模式，用户session在app初始化后会常驻内存中。

####2、文件上传

高版本微信还好，有些低版本微信文件上传会导致程序崩溃，至今我也没解决这个问题，之后有时间可以使用微信原生的上传图片api来做。

####3、图片查看解决方案

项目里面有用到微信的图片查看器，接口为[previewImage](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html#.E9.A2.84.E8.A7.88.E5.9B.BE.E7.89.87.E6.8E.A5.E5.8F.A3)

提供两套方案，优先使用微信自带的查看器。如果检测到不是微信浏览器或者由于其他原因调用不了微信API的话，则使用方案二。

方案二是自己写的图片预览插件。

####4、微信分享

微信分享是一个比较重要的功能，也是页面pv主要来源之一。用户可以分享页面到朋友圈，微信好友，qq等。

为了公众号运营者推广和吸粉，项目之后会做一个分享设置的功能。该功能主要实现分享A（我们的）页面时打开的是B（微信的）页面，在通过B页面回流至A页面。这样运营者就可以将流量引导到他们需要引导的页面去。

具体实现请查看微信[分享接口](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html#.E5.88.86.E4.BA.AB.E6.8E.A5.E5.8F.A3)。

当然，有个隐藏属性：如果页面没有做微信分享设置，默认会取页面中第一张高宽为300px的图片当做分享的图标。


####5、样式的问题

当页面的滚动条不在最上面的时候，`position:fixed;`的元素在微信浏览器中里面经常会串位。而且 css3 动画效果也不流畅（应该是手机性能问题）。

建议在写移动端`animation`时尽量采用css3提供的方法，开启GPU提高渲染速度。

####6、click问题

移动端浏览器中有一个click延迟问题，大约是300ms，网上也有不少解决方案。我们项目中用的是 [fastclick](https://github.com/ftlabs/fastclick) 插件，感觉挺不错的，使用方法如下：

        seajs.use("plugins/fastclick", function() {
            if ('addEventListener' in document) {
                FastClick.attach(document.body);
            }
        });

以前尝试自己使用touch事件封装替代click，但很多时候都不尽人意。

还有一个click事件的问题，在微信浏览器中div绑定的click事件有时候会触发不到。解决办法是 css中必须给 div添加 `cursor:pointer;才能使浏览器为div注册click事件

####7、测试方法

暂时没有使用腾讯X5的调试工具。

## 其他相关

### 加载速度优化

很多用户反映网站加载慢，毕竟手机很多时候会没有wifi，代码结构还有待继续优化。使app在初始化时加载的文件体积和数量尽可能小。

项目打包上线时压缩代码文件，目前有很多压缩工具可供选择，具体使用说明工具看个人喜好。压缩工具其实都差不多，相同文件压缩比例相差不大。

合理处理项目文件依赖，比如通过action触发时需要加载的文件尽量用使用require.async请求。

不要过分依赖第三方插件，第三方库越多，项目越庞大，加载就越慢。

比如jquery，之前打算换成zepto，但是zepto的ajax方法并没有jquery的好用，因为jquery本身支持promise写法，不需要引入其他promise类库。

这个版本css文件有做一些分离，公用样式写在main.css里面，其他各页面模块样式分别在各页面模块样式文件里面，在controller中使用seajs-css.js引入样式文件。seajs3.0.0已经把seajs-css单独抽离。

目前正在尝试把template分离。因为项目时间越长template文件就越大，以后模块多了之后肯定会很庞大。

前端模板使用的是artTemplate，渲染速度快。

项目中很多模块都使用单例模式，数据会尽量缓存在内存里面。

### 开发框架的选型

angular做移动端如何？

感觉市面上的框架都好大

之前看到个 observe.js 可以做object对象变化监听  还蛮不错的

可以模拟 angular 的  scope change

OA我准备用angular2.0框架开发了