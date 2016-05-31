#####抽奖大转盘

####list抽奖
>/api/lottery/list
>organizatioId
>skip
>limit

####奖品中奖结果
>/api/lottery/{id}/award/result
>get
>

#####奖品结果下载
>/api/lottery/{id}/result/export


####add抽奖
>/api/lottery/add
>name
>organizatioId
>state : OPEN CLOSED
>forceAttention 
>description
>createDate
>startDate
>endDate
>frequency 时间段抽几次
>registerJson

####update抽奖
>/api/lottery/{id}/update

####开关切换
>/api/lottery/{id}/state/update
state:OPEN CLOSED

####删除抽奖
>/api/lottery/{id}/remove
>


####get抽奖
>/api/lottery/{id}/get


####抽奖时间段list
>/api/lottery/{id}/time/list


####抽奖时间段添加
>/api/lottery/{id}/time/add
>startDate
>endDate
>frequency

####抽奖时间段更新
>/api/lottery/{id}/time/{timeId}/update


####抽奖时间段删除
>/api/lottery/{id}/time/{timeId}/remove


####抽奖时间段get
>/api/lottery/{id}/time/{timeId}/get

####奖品list
>/api/lottery/{id}/award/list

####奖品添加
>/api/lottery/{id}//award/add
>name>
portraitUrl
portraitLotteryUrl
description
max
probability


####奖品更新
>/api/lottery/{id}/award/{awardId}/update


####奖品删除
>/api/lottery/{id}/award/{awardId}/remove

####获取奖品设置
>/api/lottery/{id}/award/{award}/get
