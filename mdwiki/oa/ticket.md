#Ticket接口说明文档(OA)

####创建TicketSource
>/api/ticket-source/add:post
>name
>terse
>organizationId
>registerJson

>返回:id

####获取TicketSource
>/api/ticket-source/{ticketSourceId}/get:GET

>返回:ticketSourceVo

####更新ticketsource 状态
>/api/ticket-source/{ticketSourceId}/state/update:POST
>state = CLOSED || OPENED

####ticktSource列表
>/api/ticket-source/list :GET
>organizationId required
>state not required
>keyword not required
>skip required
>limit required
>返回：resultList



####移除电子票
>/api/ticket-source/{ticketSourceId}/remove:POST

>返回:OK

####更新电子票
>/api/ticket-source/{ticketSourceId}/update:POST 
id, name ,terse , organizationId, state--状态不必传
>registerJson

>返回:OK

####添加电子票发票时间，票数
>/api/ticket-source/{ticketSourceId}/open-time/add:POST
startDate:起始时间
endDate:结束时间
ticketSourceId:对应票源信息id
numberOfLimit：电子票最大数量

>返回:OK

####获取电子票源下面的抢票时段
>/api/ticket-source/{ticketSourceId}/open-time/list : GET
>resultOK(list)

####更新电子票发票时间，票数上线
>/api/ticket-source/{ticketSourceId}/open-time/{ticketOpenTimeId}update: POST
startDate:起始时间
endDate:结束时间
ticketSourceId:对应票源信息id
numberOfLimit：电子票最大数量

>返回:OK

####移除电子票发票时间段
>/api/ticket-source/{ticketSourceId}/open-time/{ticketOpenTimeId}/remove:POST

>返回:OK

####申请，抢电子票
>/api/ticket-source/{ticketSourceId}/open-time/{ticketOpenTimeId}/request
>

####放弃电子票
>/api/ticket-source/{ticketSourceId}/open-time/{ticketOpenTimeId}/abandon POST
>

####绑定电子票到活动
>/api/ticket-source/{ticketSourceId}/bind POST
>eventId

####检票
>/api/ticket-source/{ticketSourceId}/check POST
>captcha
>resultOk resultError("检票失败")

