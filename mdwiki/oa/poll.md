#poll接口文档
####创建poll
>/api/poll/add
>id;
>title;
>thumbnail;
>terse;
>text;
>state;
>organizationId;
>startDate;
>endDate;
registerJson;
>return id

####更新poll
>/api/poll/{pollId}/update
>id;
>title;
>thumbnail;
>terse;
>text;
>state;
>organizationId;
>startDate;
>endDate;
registerJson;
>return resultOk

####删除poll
>/api/poll/{pollId}/remove
>return resultOk

####列表poll
>/api/poll/list
>organizationId
>keyword
>state
>skip
>limit
>return resultOk

####提交答案
>/api/poll/{pollId}/sign-up
>signUpInfo

####开启问卷状态
>/api/poll/{pollId}/open
>return resultOK()

###关闭问卷状态
>/api/poll/{pollId}/close
>return resultOK()

####列出报名人员
>/api/poll/{pollId}/list-sign-up-users
>skip
>limit
>

####获取问卷答案
>/api/poll/{pollId}/result/{resultId}/get
>resultId 上面id
>return resultOK()


####获取问卷统计信息
>/api/poll/{pollId}/statistics
>问卷总数
>各选项数量