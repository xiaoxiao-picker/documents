#Wechat接口说明文档:front
####校校公众号AppId
>/application/public-app-id:GET

####第三方平台AppId
>/application/component-app-id:GET

####微信网页授权签名
>/application/js-api-signature:GET

####检查用户是否关注公众号
>/wechat/attention/check:GET
publicId

####生成关注后输入的token
>/wechat/attention/token/get:GET
publicId

####获取组织的公众号信息
>/wechat/public/get-by-organization:GET
organizationId
