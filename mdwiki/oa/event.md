#Event接口文档
####创建Event
>/api/event/add
>name
>startDate
>endData
>organizationId 必
>sponsor
>thumbnailUrl
>address
>category.id
>allowToSignUp
>onlyAllowMembersToSignUp
>detail
>registerJson
>{
	id: ,
	texts:[{..}],
	choices:[{..}],
	images:[{..}]
}
>return id

####获取活动基础信息
>/api/event/{id}/get GET
>return 

####更新活动基础信息
>/api/event/{id}/update
>name
>startDate
>endData
>organizationId 必
>sponsor
>thumbnailUrl
>address
>category.id
>allowToSignUp
>onlyAllowMembersToSignUp
>detail
>registerJson
>return resultOK

####设置活动状态
>/api/event/{id}/state/update
>state

####删除活动
>/api/event/remove
>ids 必传
>organizationId 必传
>return resultOK

####添加活动报名时间
>/api/event/{eventId}/sign-up-time/add
>eventId
>startDate
>endDate
>numberOfLimit
>numberOfRemaining

####获取活动报名时间段
>/api/event/{eventId}/sign-up-time/list
>


####更新报名时间
>/api/event/{eventId}/sign-up-time/{signUpId}/update
>eventId
>startDate
>endDate
>numberOfLimit
>numberOfRemaining
>id=signUpId

####删除报名时间
>/api/event/{eventId}/sign-up-time/{signUpId}/remove

return resultOK()



####列出组织下活动
>/api/event/list
>organizationId 必
>keyword not required
>state
>categoryId 非必传
>skip 必
>limit 必
>return resultOK(list);

####添加活动分类
>/api/event/category/add
>name
>organizationId 必
>return id

####删除活动分类
>/api/event/category/{categoryId}/remove
>return resultOK();

####列出组织活动分类
>/api/event/category/list
>organizationId 必
>return resultOK(list)

####列出活动报名人数
>/api/event/{id}/sign-up-count
>return 报名人数


####列出某个活动的报名人员
>/api/event/{id}/sign-up-users/list 
>skip
>limit


