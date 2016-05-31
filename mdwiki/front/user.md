#User接口说明文档:front
####获取userInfo
>/user/{userId}/update:POST

参数:
userInfo:用户信息

>返回 OK, 没有权限

####获取用户信息
>/user/{userId}/get:GET

参数:userId 用户标识

>返回 用户信息

####获取用户参加活动信息
>/user/{userId}/track/get: GET


>/user/{userId}/track/event/list
>/user/{userId}/track/event/count

type: EVENT, VOTE, TICKET

####同步用户微信信息
>/user/{userId}/wechat/synchronize:POST
code


/组织评价
>/user/{userId}/comment/list
>organizatinId

####获取用户配置信息
/user/{userId/config/get:GET

####更新用户配置信息
/user/{userId}/config/update:POST
showSynchronization:boolean //是否提示用户同步微信信息
