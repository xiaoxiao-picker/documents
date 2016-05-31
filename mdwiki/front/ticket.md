#ticket说明文档:front
####获取电子票
>/ticket/{ticketId}/get:GET

####电子票源
>/ticket-source/{id}/get:get


####获取电子票
>/ticket-source/{id}/ticket/get:

####检票
>/ticket/check:POST
ticketId
captcha
verificationToken


####抢票
>/ticket-source/open-time/{ticketOpenTimeId}/request
>signUpInfo
>电子票被抢完
>电子票未到开启时间

####获取检票token
>/ticket-source/{sourceId}/verification-code:GET

