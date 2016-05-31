#wall接口

####添加微信墙
>api/wall/add:POST
>orgId  
>userId
>title 
>startDate 
>endDate 
>wallState [OPEN, CLOSED]  
>backgroundColor 
>backgroundImagUrl 
>fontColor 
>boolean needCheck
>返回 墙Id

####微信墙列表
>api/wall/list:GET
>orgId
>wallState [OPEN, CLOSED] 不传：所有状态 
>skip
>limit
>返回 微信墙列表

####获取微信墙
>api/wall/{wallId}/get:GET
>wallId
>返回 微信墙

####更新微信墙
>api/wall/{wallId}/update:POST
>wallId
>orgId  
>userId
>title 
>startDate 
>endDate 
>wallState [OPEN, CLOSED]  
>backgroundColor 
>backgroundImagUrl 
>fontColor 
>boolean needCheck
>返回 OK

####删除微信墙
>api/wall/{wallId}/remove:POST
>wallId
>orgId
>userId
>返回 OK

####微信墙开启
>api/wall/{wallId}/open:POST
>wallId
>orgId
>userId
>返回 OK

####微信墙关闭
>api/wall/{wallId}/close:POST
>wallId
>orgId
>userId
>返回 OK

####消息是否需要验证设定
>api/wall/{wallId}/is-need-check:POST
>wallId
>orgId
>userId
>isNeedCheck
>返回 OK

####消息添加
>api/wall/{wallId}/text/add:POST
>wallId
>userId
>text
>返回 OK

####消息列表
>api/wall/{wallId}/text/list:GET
>wallId
>userId
>skip
>limit
返回 消息列表

####用户消息列表
>api/wall/{wallId}/user/text/list:GET
>wallId
>userId
>skip
>limit
返回 用户消息列表

####消息删除
>api/wall/text/{textId}/remove:POST
>textId
>userId
>orgId
返回 OK

####上墙
>api/wall/{wallId}/text/add-to-wall:POST
>wallId
>userId
>textId
返回 OK

####墙上消息列表
>api/wall/{wallId}/wall-text/list:GET
>wallId
>skip
>limit
>userId
返回 墙上消息列表

####初始化上墙消息
>api/wall/{wallId}/wall-text/iniList:GET
>wallId
>limit
返回 初始化上墙消息

####参加抽奖的用户滚轮
>api/wall/{wallId}/lottery/user/initiate/list:GET
>wallId
>howmany
>返回 参加用户抽奖的抽样列表

####抽奖
>api/wall/{wallId}/lottery/draw:POST
>wallId
>luckyGuy
>返回 中奖用户

####人生赢家
>api/wall/{/wallId}/lottery/winner/list:GET
>wallId
>返回 对应墙中奖用户列表