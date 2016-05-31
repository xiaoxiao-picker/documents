# 校校OA系统

#### 介绍
>编辑微信前端展现内容以及微信公众号管理平台。

#### 开发环境
>项目开发时基于grunt环境，由grunt管理配置nodejs任务启动项目。
>项目发布由grunt负责打包。

#### 架构
> MVC架构：系统采用监听URI hash 的变化进而渲染页面。通过路由脚本分发任务，由任务决定controller和view层，由controller控制数据以及具体渲染过程。

#### 目录结构
>   仅描述主要目录
   
    app
        plugins:插件类，由第三方提供的脚本
        scripts:
            config://配置类脚本
            controllers://控制器
            dataModels://数据处理类
            lib://插件类
            models://UserModal.js
            public://通用脚本文件，发布时被打包压缩进同一个js文件
            services://api层
            application.js//项目入口文件
            baseController.js//controller.js基类
            router.js//路由表
            template.js//编译后模板文件
      
        styles://样式文件(.scss)，最终被编译为app/styles/**.css文件供html使用
        sui://sea.js+jquery.js+bootstrap.js
        templates://模板文件(.html)，最终被编译为app/template.js文件供controller使用

#### 相关技术
>   排名不分先后
>*  1、artTemplate：负责view模板编辑
>*  2、sass：负责css文件编辑
>*  3、seajs：负责管理文件依赖
>*  4、bootstrap：负责交互效果实现


##### docs map
*   1、[AppUser](web/projects/oa/app-user.md)
