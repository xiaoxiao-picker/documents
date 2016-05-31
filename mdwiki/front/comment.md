#评论接口说明:front
####添加评论
>/comment/{subjectType}/{subjectId}/add:POST

####删除评论
>/comment/{commentId}/remove:POST

####统计评论数
>/comment/{subjectType}/{subjectId}/count:GET

####获取评论列表
>/comment/{subjectType}/{subjectId}/list:GET
skip
limit

####根据热度获取评论列表
>/comment/{subjectType}/{subjectId}/list-by-heat:GET
skip
limit

####评论点赞
>/comment/{commentId}/praise/add:POST

####评论取消赞
>/comment/{commentId}/praise/remove:POST

####获取评论
>/comment/{commentId}/get:GET

