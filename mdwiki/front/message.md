#用户消息

####列出用户消息
>/api/message/list

APPLY_REFUSE, APPLY_AGREE, COMMENT_REPLY, FEEDBACK_REPLY

####列出消息总数
>/api/message/count

####列出未读消息总数
>/api/message/count-unreaded

####获取消息
>/api/message/{id}/get

####消息标记
>/api/message/mark
>ids

####消息未标记
>/api/message/unmark
>ids

####删除消息
>/api/message/remove
>ids

####标记已读
>/api/message/read