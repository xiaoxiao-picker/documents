#活动绑定接口说明文档
####绑定
>/event/{eventId}/relation/bind:POST

参数:
targetId 绑定对象标识
targetType 绑定对象类型 VOTE | TICKET

>返回 OK, 不存在该活动, 没有权限

####解绑
>/event/{eventId}/relation/unbind:POST

参数:
targetId 绑定对象标识
targetType 绑定对象类型 VOTE | TICKET

>返回 OK, 不存在该活动, 没有权限

####获取绑定对象列表
>/event/{eventId}/relation/list:GET

参数:
targetType 绑定对象类型 VOTE | TICKET

>返回 投票或电子票列表, 不存在该活动, 没有权限