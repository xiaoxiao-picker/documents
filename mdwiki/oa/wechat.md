#Wechat接口说明文档
####获取微信第三方预授权码
>/application/pre-auth-code:GET

>返回:OK

####获取微信第三方AppId
>/application/component-app-id:GET

>返回:OK

####微信第三方授权跳转页面
>https://mp.weixin.qq.com/cgi-bin/componentloginpage?component_appid=xxxx&pre_auth_code=xxxxx&redirect_uri=xxxx

component_appid:第三方AppId
pre_auth_code:第三方预授权码
redirect_uri:用户授权后跳转地址

说明:跳转后会在redirect_uri的参数中加上auth_code与expires_in
auth_code:授权码
expires_in:过期时间(单位:秒)
之后请调用微信第三方完成授权接口

####微信第三方完成授权
>/wechat/public/finish-auth:POST

authCode:用户授权码
organizationId:组织标识

>返回:OK

####获取公众号信息
>/wechat/public/get-by-organization:GET

organizationId:组织标识

>返回:公众号相关信息

####同步公众号粉丝
>/wechat/public/{publicId}/attention/synchronize:POST

####强制解除绑定
>/wechat/public/unbind:POST
organizationId

####验证公众号是否是通过微信第三方绑定
>/wechat/public/{publicId}/is-authorizer:GET
如果返回false则需要公众号进行微信第三方绑定

####验证公众号是否绑定
>/wechat/public/{publicId}/check-bind:GET

####相关词典
######service_type_info:授权方公众号类型
>0代表订阅号，1代表由历史老帐号升级后的订阅号，2代表服务号
######verify_type_info:授权方认证类型
>-1代表未认证，0代表微信认证，1代表新浪微博认证，2代表腾讯微博认证，3代表已资质认证通过但还未通过名称认证，4代表已资质认证通过、还未通过名称认证，但通过了新浪微博认证，5代表已资质认证通过、还未通过名称认证，但通过了腾讯微博认证
