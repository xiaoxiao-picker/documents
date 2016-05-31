#投票接口说明文档(OA)
####创建投票
>/vote/add:POST

String name
Date startDate
Date endDate
VoteState state
String terse;
String thumbnailUrl;
String organizationId;
VoteOptionsSortType sortType;
Boolean repeatable;
Boolean compulsory;
String description;
Integer tickets;
Integer cycle;
Boolean permitComment;
Boolean permitAttentionComment;

>返回:voteId

####更新投票
>/vote/{voteId}/update:POST

String name
Date startDate
Date endDate
VoteState state
String terse;
String thumbnailUrl;
String organizationId;
VoteOptionsSortType sortType;
Boolean repeatable;
Boolean compulsory;
String description;
Integer tickets;
Integer cycle;

>返回:OK


####/vote/{voteId}/comment-open

####/{voteId}/comment-close

####/{voteId}/comment-attention-open


####/{voteId}/comment-attention-close

####获取投票信息
>/vote/{voteId}/get:GET

>返回:voteVo

####添加投票选项
>/vote/{voteId}/option/add:POST

String name;
String imgUrl;
String videoUrl;
String description;

>返回:optionId

####删除投票选项
>/vote/option/{optionId}/remove:POST

>返回:OK

####获取组织下的投票列表
>/vote/list-by-organization:GET

String keyword 非必填
int skip
int limit

>返回:voteVos

####获取投票选项
>/vote/{voteId}/option/list:GET

String keyword
int skip
int limit

>返回:optionVos

####获取投票的所有选项标识
/vote/{voteId}/option/list-all:GET

>返回:optionIds

####根据标识获取投票选项
/vote/option/list-by-ids:GET

String optionIds

>返回:optionVos

####开启投票
>/vote/{voteId}/open:POST

####关闭投票
>/vote/{voteId}/close:POST

####删除投票
>/vote/{voteId}/remove:POST

####开启导出任务
>/vote/{voteId}/export:POST

####获取报名列表
>/vote/{voteId}/sign-up/list:GET
voteId, state, skip, limit

####更新报名状态
>/vote/sign-up/{signUpId}/update-state:POST
signUpId, state, response

####更新报名信息
>/vote/sign-up/{signUpId}/update:POST

####获取报名数
>/vote/sign-up/count:GET
state 可以为null
