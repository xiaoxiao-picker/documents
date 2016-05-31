#comment接口

####添加评论
>api/comment/add:POST
>commentSubject 评论类别名称{ORG, TICKET, EVENT, WALL, VOTE, ARTICLE, PROPOSAL, VOTE_OPTION }
>subjectId 分类的Id
>targetUserId 对目标用户评论
>text 
>返回 OK

####删除评论
>api/comment/{commentId}/remove:POST
>commentId
>orgId
>返回 OK

####评论列表
>api/comment/list:GET
>subjectComment
>sujectId
>skip
>limit
>返回  评论列表

####统计评论总数
>api/comment/count:GET
>subjectComment
>subjectId
>返回 评论总数