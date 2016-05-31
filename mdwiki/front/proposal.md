#提案

####列出组织提案
>/api/proposal/list
organizationId
skip
limit
state SOLVED UNSOLVED

###count proposal
>/api/proposal/count
organizationId
state SOLVED UNSOLVED


####get proposal
>/api/proposal/{proposal}/get


####添加赞	
>/api/proposal/{id}/praise/add


####取消赞
>/api/proposal/{id}/praise/remove

####添加有用
>/api/proposal/{id}/useful/add

####添加无用
>/api/proposal/{id}/useless/add


####举报
>/api/proposal/{id}/report/add
 >text


####list-own-proposal
>/api/proposal/list-own
>skip
>limit

####count-own-proposal
>/api/proposal/count-own
>

####add proposal
>/api/proposal/add
>orgId
>text
>title
>thumbnailUrls

####upate proposal
>/api/proposal/{proposalId}/update

####remove proposal
>/api/proposal/{proposal}/remove

####reply-add
>/api/proposal/{proposalId}/reply/add
>text

####remove-reply
>/api/proposal/reply/{reply}/remove


####update-reply
>/api/proposal/reply/{replyId}/update








