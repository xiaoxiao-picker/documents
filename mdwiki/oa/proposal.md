#表单接口

####添加提案
>api/proposal/add:POST
>orgId
>title
>text
>thumbnailUrl
>categoryId
>返回 OK

####删除提案
>api/proposal/{proposalId}/remove:POST
>proposal
>返回 OK

####更新提案
>api/proposal/{proposalId}/update:POST
>proposal
>title
>text
>thumbnailUrl
>categoryId
>返回 OK

####获取提案
>api/proposal/{proposalId}/get:GET
>proposalId
>返回 提案

####提案列表
>api/proposal/list:GET
>orgId
>reported true/false  可不传
>state UNSOLVED/SOLVED
>skip
>limit
>返回 提案列表

####改变提案状态
>api/proposal/{proposalId}/state/change:POST
>proposalId
>state {UNSOLVED, SOLVED}
>返回 OK

####提那家提案回复
>api/proposal/{proposalId}/reply/add:POST
>proposalId
>text
>返回OK

####置顶
>api/proposal/{proposalId}/top POST

####取消置顶
>api/proposal/{proposalId}/untop POST

####删除提案回复
>api/proposal/{proposalId}/reply/remove:POST
>replyId
>返回 OK

####更新提案
>api/proposal/{proposalId}/reply/{replyId}/update:POST
>replyId
>text
>返回 OK

####获取回复
>api/proposal/{proposalId}/reply/{id}/list:GET
>proposalId
>返回 提案回复

####评论开关
>/api/proposal/{proposalId}/comment/state/change:POST
CommentState:OPEN, CLOSE



>/api/proposal/category/add
>name
>organizationId

>/api/proposal/category/{id}/update
>name

>/api/proposal/category/list
>organizationId

>/api/proposal/category/{id}/remove
































