#User接口说明文档
####获取userInfo
>/user/{userId}/get:GET

参数:userId 用户标识

>返回 用户信息

####获取用户设置
>/user/{userId}/config/get :GET
>返回 用户设置信息

####更新用户设置
>/user/{userId}/config/update :POST
>needOrgInfoEditGuide
>needWechatSettingGuide
>needFuncManageGuide
>needAutoReplyGuide
>needRelateOrgGuide
>resultOK()


####更新用户信息
>/user/{userId}/update :POST
name
nickname
gender
portraitUrl
studentId
address
hometown
grade
school
campus