#Wechat接口说明文档
####获取微信素材
>/wechat/material/list:GET
>int skip
>int limit
>organizationId
>type image voice video thumb
>返回:OK


####获取素材信息
>/wechat/material/{id}/get 

####移出素材
>/wechat/material/remove
>ids .


####同步素材
>/wechat/material/synchronize
>organizationId
>type image voice video 


####图文list
>/wechat/material/news/list
>organizationId
>skip
>limit

####获取
>/wechat/material/news/{id}/get


####图文
>/wechat/material/synchronize 
>organizationId
>type NEWS

####删除图文
>/wechat/material/news/remove
>ids


####添加图文
>/wechat/material/news/add
>articles [
 {   "title":,
    "xiaoxiaoUrl":
    "author":
    "digest":
    "show_cover_pic":true,false
    "content":""
    "content_source_url":
 }
 ]

####添加素材
>/wechat/material/add
>fileName
>url
>type :

>return resultOK(materialId)
