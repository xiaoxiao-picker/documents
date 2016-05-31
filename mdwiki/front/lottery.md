####抽奖

####get
>/api/lottery/{id}/get


###抽奖
>/api/lottery/{id}/draw


###某一天某个抽奖的抽奖结果
>/api/lottery/{id}/award
>date

###中奖轨迹
>/api/lottery/track
>skip
>limit
>userId

###获取报名结果
>/api/lottery/{id}/register/result get

####中奖轨迹总数
>/api/lottery/track/count
>userId



####获取中奖所需信息
>/api/lottery/{id}/register/get

####填写中奖所需信息
>/api/lottery/{id}/register/sign-up
>signUpInfo

####列出参加过的抽奖
>/api/lottery/track
>skip
>limit
