#消息接口文档

####列出组织下收到的消息
>/api/org/{orgId}/message/list GET
>type SYSTEM_ANNOUNCEMENT 或空，不填，不传
>skip
>limit
>return resultOK

####标记组织下的消息
>/api/org/{orgId}/message/mark
>ids
>resultOk

####批量未标记组织下的消息
>/api/org/{orgId}/message/unmark
>ids
>resultOk

####批量删除组织消息
>/api/org/{orgId}/message/remove
>ids


>/api/org/{orgId}/message/remove-all

####设置已读
/api/org/{orgId}/message/read
>ids

/api/org/{orgId}/message/read-all

####设置未读
/api/org/{orgId}/message/unread
>ids


####组织未读消息
>/api/org/{orgId}/message/count
>resultOk(announce:数量，other:数量)



####列出用户下面的消息
>/api/message/list GET
>skip
>limit
>return resultOK

####批量标记用户消息
>/api/message/mark POST
>ids
>return resultOK

####批量未标记用户消息
>/api/message/unmark POST
>ids
>return resultOK

####get用户消息
>/api/message/{messageId}/get GET
>return resultOK

####用户未读消息数量
>/api/message/count 
>resultOK(数量)

####删除用户消息
>/api/message/remove POST
>ids
>return resultOK

####获取最新系统公告
>api-oa/sys-announce/get-latest