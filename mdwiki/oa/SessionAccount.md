#Session与Account接口说明文档(OA)
####创建Session
>/api/session/create:GET

>返回:OK

####根据Session获取当前登录的用户信息
>/api/session/get-user:GET

>返回:OK

####销毁当前Session
>/api/session/logout:POST

>返回:OK

####使用手机与密码登录
>/api/account/mobile-login-with-password:POST
phoneNumber:手机号
password:密码

6602ms

>返回:OK, 验证码错误, 验证码过期

####使用手机号码及验证码登录
>/api/account/mobile-login:POST
phoneNumber:手机号
token:验证码

>返回:OK, 验证码错误, 验证码过期


当验证成功后，如果未发现该手机号对应的用户则新增用户并登录

####请求发送手机登录验证码
>/api/account/request-login-token:POST
phoneNumber:手机号

>返回:OK, 请求过于频繁

####请求重置密码
>/api/account/request-reset-password:POST
phoneNumber:手机号

>返回:OK, 请求过于频繁

####重置密码
>/api/account/reset-password
phoneNumber:手机号
token:验证码
newPassword:新的密码

>返回:OK, 密码格式错误, 验证码过期, 验证码错误

>/account/request-voice-login-token
phoneNumber
captcha

>/account/request-reset-password-voice:POST

>/account/request-reset-phone-number-voice:POST
