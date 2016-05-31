#Vote接口说明文档:front
####投票
>/vote/{voteId}/cast:POST

参数:
optionIds:选项标识,以,分割

####获取投票信息
>/vote/{voteId}/get:GET

####获取组织下的活动列表
>/vote/list-by-organization:GET

参数
organizationId:组织标识
keyword: 关键词(非必填)
skip,limit:分页信息

####获取投票下的选项
>/vote/{voteId}/option/list:GET

参数:
keyword:关键词(非必填)
skip,limit:分业信息

####获取投票下的所有选项标识
>/vote/{voteId}/option/list-all:GET

####根据选项标识获取选项
>/vote/{voteId}/option/list-by-ids:GET

参数
optionIds:选项标识,以,分割

####获取组织投票数
>/vote/count-votes:GET
organizationId:组织标识
keyword:关键词

####获取选项详情
>/vote/option/{optionId}/get:GET

###获取当前周期内已选择的选项
>/vote/{voteId}/option/list-casted:GET

###获取排名与参与人数信息
>/vote/{voteId}/live-info:GET
voteId
skip
limit

####添加投票报名
>/vote/{voteId}/sign-up/add:POST
signUp 详见报名信息

####更新投票报名
>/vote/{voteId}/sign-up/{signUpId}/update:POST
signUp 详见报名信息

####获取报名列表
>/vote/{voteId}/sign-up/list:GET

####报名信息
id, voteId, name, description, phoneNumber, realName, createDate, userId, state(UNCHECKED, REFUSE, APPROVE), optionId, imageUrls, response(管理员回复)

####获取报名状态
>/vote/{voteId}/sign-up/state:GET

####获取用户排名信息
>/vote/{voteId}/ugc/live-info:GET

####获取用户报名状态
>/vote/{voteId}/sign-up/state:GET

####获取报名总数
>/vote/{voteId}/sign-up/count:GET

