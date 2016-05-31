#活动接口说明文档:front
####获取活动列表
>/event/list:GET
organizationId
state
categoryId
keyword
skip
limit

####获取活动总数
>/event/count : GET
organizationId
state
categoryId
keyword

####获取活动
>/event/{eventId}/get:GET

####获取活动分类
>/event/category/list:GET
获取组织的活动分类

####报名活动
>/api/event/{eventId}/sign-up-time/{signUpId}/sign-up
>operatorUser
>signUpInfo-报名信息
>{
	userDates:[{}],
	userTexts:[{}],
	userTexts:[{}],
	userOptions:[{}],
}
>return resultOk()

####取消报名活动
>/api/event/{eventId}/unsign-up
>operatoruser
>return resultOk()

####获取活动的电子票列表
>/event/{eventId}/ticket/list:GET

####获取活动的投票列表
>/event/{eventId}/vote/list:GET

####赞
>/event/{eventId}/praise/add:POST

####取消赞
>/event/{eventId}/praise/remove:POST

####获取报名时间
>/event/{eventId}/time/list:GET

####获取关联活动信息
>/event/list-related:GET
organizationid
keyword
skip
limit

####获取关联活动总数
>/event/count-related:GET
organizationId
keyword
