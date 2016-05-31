# 校校项目交接文档

## 概述

校校web端有三套系统：分别为OA系统、Front系统、内部管理系统。

1. OA系统：组织管理者编辑发、布内容的平台。<br/>
    
    测服地址为`root@121.41.120.109`，正服地址为`root@120.55.137.227`，正服内网地址为`root@10.168.103.57`。<br/>
    
    git地址为`ssh://git@121.41.75.25:/develop/git/web/xiaoxiao-oa.git`
    
    
2. front：C端用户操作页面，主要入口为各组织公众号，主要使用环境为微信浏览器。<br/>
    
    测服地址为`root@121.41.75.25`，正服地址为`root@120.55.179.248`，正服内网地址为`root@10.171.199.172`。<br/>
    
    git地址为`ssh://git@121.41.75.25:/develop/git/web/xiaoxiao-front.git`
    
    *其中Front系统中存在一个扩展系统，部署在`posters`目录下，由nginx配置路径转发。*
    扩展项目主要包含一些与系统主业务无关的页面，包括H5小游戏、节假日定制活动页、第三方跳转页、音乐播放页等。该项目有独立的开发环境和部署脚本，但是部署地址为front项目中的`posters `文件夹下。<br/>
    git地址为`ssh://git@121.41.75.25:/develop/git/web/xiaoxiao-front-expand.git`
    
3. 内部管理系统：主要负责校校系统基础数据的维护以及系统运行状态的监视（内部人员使用）。<br/>
    该项目测服地址，正服地址为`root@120.55.80.21`，正服内网地址为`root@10.251.240.212`。<br/>
    git地址为`git@121.41.75.25:/develop/git/web/xx-management.git`。
    
## 开发环境及流程
### 开发环境依赖
以上三个系统在开发时均使用Grunt自动化构建工具，启动环境之前请确保完成以下操作：<br/>
1. 安装[Nodejs](https://nodejs.org/en/)环境；<br/>
2. 安装[Grunt](http://www.gruntjs.net/)工具；<br/>
3. 安装[bower](http://bower.io/)包管理器（建议全局安装`npm install bower -g`）；<br/>
4. 下载项目运行依赖文件，配置在package.json文件中，可通过执行`npm install`命令下载；<br/>
5. 下载bower依赖文件，配置在bower.json文件中，可通过执行`bower install`命令下载；<br/>

### 开发环境启动
运行`grunt serve`命令启动系统开发环境，运行`./bin/proxy`或`sudo node proxy.js`命令启动代理（因为在开发时需要需用ajax动态调用远程服务器的API，所以需要代理解决跨域数据请求的问题）。此时应用程序将运行在localhost的80端口上，可通过`http://localhost/`查看系统页面。<br/>
*如果项目环境在启动的过程中遇到tmod相关的错误，需要执行`./bin/pacth`补丁命令。*

### 项目结构介绍
项目具体文件结构请以实际项目为主，以下仅大致介绍主要目录。<br/>
1. `app/`文件夹：项目开发目录（包含js/sass/html/部分插件/images/font字体文件等），所有开发工作均在此目录中完成。<br/>
2. `dist/`文件夹：项目build时的目标目录，即部署至服务器的文件目录。<br/>
3. `bin/`文件夹：项目中使用的一些bash/nodejs脚本文件。<br/>
4. `bower_components/`文件夹：项目部分插件依赖文件，由bower进行管理，配置在bower.json文件中。<br/>
5. `node_modules/`文件夹：项目开发运行时依赖文件，由npm进行管理，配置在package.json文件中。<br/>
6. `Gruntfile.js`：Grunt任务的管理配置文件（具体任务请查看`Gruntfile.js`文件）。<br/>
7. `proxy.js`：代理任务的代码，负责将接口目标端口代理至本地localhost:80端口上。

### 相关预编译语言
1. 项目使用`sass`作为`css`的预编译语言，由`grunt`的`watch`任务监听文件变化、执行预编译操作、自动刷新样式等操作，使用`autoprefixer`完成各个浏览器的样式兼容。<br/>
2. 项目使用[artTemplate](https://github.com/aui/artTemplate)作为模板引擎，由`grunt`的`watch`任务监听文件变化、执行预编译操作、自动刷新页面，预编译后的文件为`app/scripts/template.js`。<br/>

### 项目框架&第三方脚本库
1. 项目使用自己搭建的轻量级`MVC`框架实现SPA单页应用（后面介绍框架具体实现及功能）。<br/>
2. 项目依赖jquery框架、store.js库（cookie/localstorage缓存管理）。<br/>
3. 项目遵循`CMD`规范，使用[seajs](https://github.com/seajs/seajs)作为模块依赖库。<br/>

### 项目运行流程介绍
以OA系统为例，项目以`app/scripts/application.js`作为入口函数，在该脚本文件中注册浏览器`URL`的`hashchange`事件。<br/>
1. 通过监听`hashchange`事件获取对应的`hash`；<br/>
2. 通过路由模块（`app/scripts/router.js`&`app/scripts/public/router.js`）得到具体的业务目标（即对应的`controller`和`template`）；<br/>
3. 流程进入到controller中，在controller中实现具体的业务（请求数据、包装数据、页面渲染）。

### MVC框架的具体实现
1. 路由匹配模块，由`app/scripts/public/router.js`模块实现，代码如下：

```js
    var route = function(url) {
        if (routerObj.hasOwnProperty(url)) {
            return routerObj[url];
        } else {
            for (route in routerObj) {
                if (routerObj[route].hasOwnProperty('regExp')) {
                    var routeRegExp = new RegExp(routerObj[route].regExp);
                    if (routeRegExp.test(url)) {
                        /**
                         * Fix Bug: 修复多个参数无法获取到的问题
                         */
                        var valueArr = url.match(routeRegExp),
                            paramArr = route.match(/:([\w]*)/g);
                        for (var i = 1, len = valueArr.length; i < len; i++) {
                            routerObj[route][paramArr[i - 1].slice(1)] = valueArr[i];
                        }
                        return routerObj[route];
                    }
                }
            }
            return null;
        }
    };
```
2. 路由配置模块`app/scripts/router.js`，代码形式如下：

```js
    "events": {
        controller: "event/listController",
        template: "event/list",
        menu: "Event"
    },
    "event/:eventId/info": {
        regExp: "event\\/([a-zA-Z0-9\\-]+)\\/info",
        controller: "event/infoController",
        template: "event/info",
        menu: "Event"
    }
```

路由配置模块存在两种格式（如上面代码），一种为固定`hash`格式、一种为动态参数格式（由正则表达式进行匹配）。其中KEY表示`hash`的格式，VALUE中的controller表示对应controller的路径，template表示模板的路径，menu指定页面菜单的`class`用来控制页面刷新后设置相应菜单的active状态，`regExp`为`hash`的正则。具体细节请以实际代码为准。

### 代码模块（规范）介绍
#### css/sass模块
项目使用sass作为css的预编译语言，所有样式文件目录为`app/styles/`，预编译工作由Grunt的`sass`任务实现，并执行autoprefixer操作，具体配置请在`Gruntfile.js`中查看。<br/>
1. 公用样式定义在`app/styles/global/`文件夹内，具体样式模块通过文件（名称）区分；<br/>
2. 各页面的样式定义在`app/styles/models/`文件夹中，具体页面的样式文件与业务URL相对应；<br/>
3. 插件类样式定义在`app/styles/lib/`文件夹中；

#### html/template模块
项目使用artTemplate作为html模板语言，模板文件定义在`app/templates/`文件夹中，模板路径与业务URL相对应，预编译工作由Grunt的`tmod`任务实现，最终模板会统一编译至`app/scripts/template.js`文件中。

#### javascript模块
1. 公用模块均定义在`app/scripts/public/`文件夹中，部分模块会由`app/scripts/public/helper.js`模块向外提供。<br/>
2. 非公用模块（插件模块）定义在`app/scripts/lib/`文件夹中，一般通过`require.async`函数动态调用。<br/>
3. `app/scripts/factory/application.js`定义项目的`Application`对象，采用单例模式。<br/>
4. `app/scripts/factory/organization.js`定义项目的`Application.organization`对象，采用单例模式。<br/>
5. `app/scripts/factory/user.js`定义项目的`Application.user`对象，采用单例模式。<br/>
6. service定义在`app/scripts/services/`文件夹中，service名称对应具体的业务，该模块负责统一控制接口API的调用，具体的AJAX调用模块封装在`app/scripts/public/ajaxHandle.js`模块中，该AJAX模块在jquery.ajax模块基础上进行封装，支持Promise/A+规范，支持失败重新请求。<br/>
7. controller模块定义在`app/scripts/controllers/`文件夹中，每个controller模块均继承自baseController模块(`app/scripts/baseController.js`)，该模块负责具体业务的实现。<br/>

#### 模板中事件的定义
系统事件监听在项目入口模块（`app/scripts/application.js`）中，在匹配到具体的路由后调用事件监听方法：<br/>

```js
// 绑定[data-xx-action]事件
Helper.globalEventListener("click." + namespace, "data-xx-action", controller.actions);
Helper.globalEventListener("change." + namespace, "data-xx-change-action", controller.actions, true);
Helper.globalEventListener("keyup." + namespace, "data-xx-keyup-action", controller.actions, true);
Helper.globalEventListener("focus." + namespace, "data-xx-focus-action", controller.actions, true);
```
所有事件均统一绑定在`document`上，由具体的controller定义事件行为`actions`，代码如下：<br/>

```js
    var Controller = function() {
        var controller = this;
        controller.namespace = "article.info";
        controller.actions = {
            save: function() {
                // do something
            }
        };
    };
```

开发时只需要在HTML模板的标签上定义`data-xx-action`属性即可，其中`data-xx-action`属性的值即为`controller.actions`中定义的函数，代码如下:<br/>

```html
<button class="btn btn-xx-green btn-save" data-xx-action="save" disabled title="保存修改">保存</button>
```

其中 `data-xx-action` 表示 `click` 事件，`data-xx-change-action` 表示 `change` 事件，`data-xx-keyup-action` 表示 `keyup` 事件，`data-xx-focus-action` 表示 `focus` 事件。



### 项目build及部署
#### build
项目使用Grunt进行打包工作，打包命令为`grunt build`，打包之前可使用命令`grunt serve:dist`启动本地服务查看项目在发布环境中的运行状态，可通过修改`proxy.js`中的接口路径控制数据服务器的请求。build时主要执行如下任务：<br />
1. 从工作目录`app/`复制代码至`dist/`发布目录。<br />
2. 静态资源（html/js/css/image）替换、md5去缓存、压缩、合并。<br />
3. seajs模块的`transport`，需要确保`transport`任务中的`alias`与`sea-config.js`中的`alias`一致。<br />
*每次打包时请手动更新版本，即`app/sui/sea-config.js`文件中中的`VERSION`变量*<br/>

项目build完成之后的代码在`dist/`文件夹中，之后将`dist`中的代码部署至服务器即可。

#### 部署流程

以下为Front系统的的部署流程（其他两个系统流程大致相同）：<br/>
1. 在`app/scripts/seajs-config.js`中版本递增；<br/>
2. 执行`grunt build`命令生成发布文件至dist文件夹；<br/>
3. 执行`tar -zcvf packages/release-front-v2.1.15.tar.gz dist/`将dist文件夹压缩至packages/release-front-v2.1.15.tar.gz（其中文件名与版本号保持一致）；<br/>
4. 执行`scp packages/release-front-v2.1.15.tar.gz front.test:packages`命令将压缩文件上传至对应服务器；<br/>
5. `ssh front.test` 登陆至对应服务器；<br/>
6. front.test服务器有两个文件夹 `bin`  `packages` 。其中`bin`中放部署脚本，`packages`中放压缩文件；<br/>
7. `rvim bin/deploy` 修改对应部署文件；<br/>
8. `./bin/deploy ` 执行部署脚本；<br/>

#### 服务器配置介绍

部署脚本均在 `bin/deploy` 脚本中。








