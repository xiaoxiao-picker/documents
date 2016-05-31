#feedback接口

####添加回馈
>api/feedback/add:POST
>orgId
>text
>返回 OK

####添加回馈回复
>api/feedback/{feedbackId}/add-reply:POST
>feedbackId
>text
>返回 OK

####获取回馈
>api/feedback/{feedbackId}/get:GET
>feedbackId
>返回 回馈

####获取回馈回复
>api/feedback/feedback-reply/{feedbackReplyId}/get:GET
>feedbackReplyId
>返回 回馈回复

####获取回馈列表
>api/feedback/list:GET
>orgId
>skip
>limit
>返回 回馈列表

####获取回馈回复列表
>api/feedback/{feedbackId}/feedback-reply/list:GET
>feedbackId
>skip
>limit
>返回 回馈回复列表

####删除回馈
>api/feedback/{feedbackId}/remove:POST
>feedback
>返回 OK

####删除回馈回复
>api/feedback/feedback-reply/{feedbackReplyId}/remove:POST
>返回 OK

