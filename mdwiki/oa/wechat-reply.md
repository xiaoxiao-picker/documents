#微信回复接口说明文档:

####获取系统关键词回复列表
>/wechat/reply/system/list:GET

>返回:系统关键词回复列表

####激活回复
>/wechat/reply/{replyId}/activate:POST

####关闭回复
>/wechat/reply/{replyId}/close:POST

####激活并关闭其他同类型(replyType)回复
>/wechat/reply/{replyId}/activate-and-close-others:POST

####新增回复绑定
>/wechat/reply/relation/add:POST

参数
publicId:公众号标识
keywords:关键词(非必填),分割
matchType:关键词匹配类型(非必填), EQUAL | LIKE
replyType:回复类型, KEYWORD | SUBSCRIBE | DEFAULT
relationJsonStr:绑定json [{"sourceId":"1", "sourceType":"*SOURCE_TYPE"}]

>返回:回复标识

####更新绑定信息
>/wechat/reply/{replyId}/relation/update:POST

参数
keywords(非必填),分割
matchType:关键词匹配类型(非必填), EQUAL | LIKE
replyType:回复类型, KEYWORD | SUBSCRIBE | DEFAULT
relationJsonStr:绑定json [{"sourceId":"1", "sourceType":"*SOURCE_TYPE"}]

####获取公众号的回复列表
>/wechat/reply/list-by-public:GET

参数
publicId:公众号标识
replyType:回复类型 KEYWORD | SUBSCRIBE | DEFAULT
messageType: 消息类型 TEXT | SINGLE_ARTICLE | MULTIPLE_ARTICLE | PICTURE
skip,limit:分页

####获取回复
>/wechat/reply/{replyId}/get:GET

####获取回复详情
>/wechat/reply/{replyId}/detail/get:GET

>返回: 详情会是以下之一, String:text, String:imageUrl, JSON:articles

####获取文章详情
>/wechat/reply/article/{articleId}/detail/get:GET

####删除回复
>/wechat/reply/{replyId}/remove:POST

####添加文字回复
>/wechat/reply/text/add:POST

参数
publicId:公众号标识
replyType:回复类型KEYWORD, SUBSCRIBE, DEFAULT
matchType:如果replyType为KEYWORD传入, EQUAL, LIKE
keywords:如果replyType为KEYWORD传入, 逗号分割
text:回复文字内容人

>返回:回复标识

####更新文字回复
>/wechat/reply/{replyId}/text/update:POST

参数:
text:文字
matchType:非必传, 仅在replyType为KEYWORD时传入, EQUAL, LIKE
keywords: 非必传, 仅在replyType为KEYWORD时传入, 逗号分割

####更新图片回复
>/wechat/reply/{replyId}/image/update:POST

参数:
keywords:非必传, 仅在replyType为KEYWORD时传入, 逗号分割
matchType:非必传, 仅在replyType为KEYWORD时传入, EQUAL, LIKE
imageUrl:图片地址

####更新文章回复
>/wechat/reply/{replyId}/article/update:POST

参数:
keywords:非必传, 仅在replyType为KEYWORD时传入, 逗号分割
matchType:非必传, 仅在replyType为KEYWORD时传入, EQUAL, LIKE
articleJsonStr: 图文json数据, [{title:"标题", description:"描述", picUrl:"缩略图",author:"作者", articleType:"ARTICLE, CUSTOMIZE",content:"内容(自定义链接也放在其中)"},{..}..]

####添加图片回复
>/wechat/reply/image/add:POST

参数
publicId:公众号标识
replyType:回复类型KEYWORD, SUBSCRIBE, DEFAULT
matchType:如果replyType为KEYWORD传入, EQUAL, LIKE
keywords: 如果replyType为KEYWORD传入, 逗号分割
imageUrl:图片地址

>返回回复标识

####添加文章回复
>/wechat/reply/article/add:POST

参数:
publicId 公众号标识
replyType:回复类型KEYWORD, SUBSCRIBE, DEFAULT
matchType:如果replyType为KEYWORD传入, EQUAL, LIKE
keywords:如果replyType为KEYWORD传入, 逗号分割
articleJsonStr:图文json数据, [{title:"标题", description:"描述", picUrl:"缩略图",author:"作者", articleType:"ARTICLE, CUSTOMIZE",content:"内容(自定义链接也放在其中)"},{..}..]


####词典:
*SOURCE_TYPE
ARTICLE, EVENT, PROPOSAL, VOTE, FORM, POLL