#front 项目部署

>1、app/scripts/seajs-config.js中版本递增
>2、执行`grunt build`命令生成发布文件至dist文件夹
>3、执行`tar -zcvf packages/release-front-v2.1.15.tar.gz dist/`将dist文件夹压缩至packages/release-front-v2.1.15.tar.gz（其中文件名与版本号保持一致）
>4、执行`scp packages/release-front-v2.1.15.tar.gz front.test:packages`命令将压缩文件上传至对应服务器
>5、`ssh front.test` 登陆至对应服务器
>6、front.test服务器有两个文件夹 `bin`  `packages` 。其中`bin`中放部署脚本，`packages`中放压缩文件
>7、`rvim bin/deploy` 修改对应部署文件
>8、`./bin/deploy ` 执行部署脚本