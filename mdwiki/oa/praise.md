#praise接口

####点赞
>api/praise/add:POST
>praiseSubject  {ORG, TICKET, EVENT, WALL, VOTE, ARTICLE, PROPOSAL, VOTE_OPTION, COMMENT}
>subjectId
>返回 OK

####取消点赞
>api/praise/cancel:POST
>praiseSubject
>subjectId
>返回 OK

####统计赞总数
>api/praise/count:GET
>praiseSubject
>subjectId
>返回 点赞总数

####获取点赞状态：是否已赞
>api/praise/state/get:GET
>praiseSubject
>subjectId
>useId
返回  是否已赞<true/false>





