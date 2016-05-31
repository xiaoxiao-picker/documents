#Account接口说明文档:front
####使用微信code登录
>/account/login-by-code:POST
code:code

####使用wechatId登录
>/account/login-by-wechat-id:POST
wechatId:微信标识

返回:用户标识

####使用微信号登录
>/account/login-by-wechat-id:POST

wechatId:微信标识

####使用手机号登录
>/account/login-by-phone-number:POST

phoneNumber:手机号
token:验证码

####微信用户绑定手机号
>/account/account/bind-phone-number:POST

phoneNumber:手机号
token:验证码

####请求登录或绑定手机验证码
>/account/request-login-token:POST

phoneNumber:手机号

####请求绑定邮箱
>/account/request-bind-email:POST

email:邮箱

####绑定邮箱
>/account/bind-email:POST

####发送语音验证码
>/account/request-voice-login-token:POST
phoneNumber
captcha

userId:
email:
token:
