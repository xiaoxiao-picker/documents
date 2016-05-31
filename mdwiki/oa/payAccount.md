####支付账号

###添加帐号
>/api/pay-account/add
>name 交通银行，建设银行
>account 账号，支付宝账号
>orgId
>type ALIPAY,BANK
>photos ，

###list账号
>/api/pay-account/list
>orgId
>state UNDEALED, APPROVED, REJECTED
>skip
>limit

####激活账号
>/api/pay-account/{id}/active
>

###更新账号
>/api/pay-account/{id}/update
>name
>account
>photos

###获取账号
>/api/pay-account/{id}/get


###删除账号
>/api/pay-account/{id}/remove


