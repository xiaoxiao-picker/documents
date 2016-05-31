代码规范描述
============
## 网页开发注意事项
http://www.alloyteam.com/2015/05/wang-ye-xing-neng-zhi-html-css-javascript/
1 在head里面尽量不要引入javascript.
2 如果要引入js 尽量将js内嵌.
3 把内嵌js放在所有css的前面.

## 插件类
> 1、插件一律以对象的模式创建，其中实例化对象需要的方法以prototype方式向外暴露。不需要暴露的方法一律采用闭包模式编写。
> 2、大部分对象只需向外提供destroy方法即可。
> 3、如init等方法尽量以闭包形式编写，防止新声明的对象多次初始化。

## 变量命名
> ###service 
> 以VoteService为例，接口尽量简单易懂
> VoteService
>               VoteService.getList/add/remove/update/get
> 
> VoteService.option
>               VoteService.option.getList/add/remove/update/get
> 