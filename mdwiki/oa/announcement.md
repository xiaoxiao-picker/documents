#announcement接口

####添加公告
>api/announcement/add:POST
>orgId  
>title 标题
>text 文本
>返回 公告Id

####发送并用短信通知
>api/announcement/sent-with-sms:POST
>announceId
返回 OK


####发送并不用短信通知
>api/announcement/sent-without-sms:POST
>announceId
返回 OK

####获取公告
>api/announcement/{announceId}/get:GET
>announceId
>返回 公告详情

####保存公告
>api/announcement/save:POST
>announceId
>orgId
>title
>text
>registerJson
>userIds
>返回 OK

####删除公告
>api/announcement/{announceId}/remove:POST
>announceId
>返回 OK

####公告回复
>api/announcement/{announceId}/reply:POST
>announceId
>replyInfo
>返回 OK

####公告结果详情取得
>api/announcement/{announceId}/detail/get:GET
>anounceId
>返回 公告结果详情

####剩余短信条数取得
>api/announcement/sms-remain/get:GET
>orgId
>返回 剩余短信条数

####公告列表
>api/announcement/list:GET
>orgId
>status
>skip
>limit



























