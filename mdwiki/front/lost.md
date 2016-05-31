#失物招领接口:front

####添加失物
>/lost/add
>title
>location
>eventDate
>contactInfo
>text
>type
>picUrls
>organizationId

####更新失物
>/lost/{id}/update
 
####列出属于自己的失物
>/lost/list-own
>keyword
>type
>skip
>limit

####count自己的失物
>/lost/count-own
>keyword
>type



 ####列出组织失物
 >/lost/list
 >organizationId
 >keyword
 >type
 >skip
 >limit

###count 
 >/lost/count
>organizationId
>keyword
>type



 ####切换失物状态
 >/lost/{id}/change-status
 status

 ####获取失物信息
 >/lost/{id}/get

#####删除失物
>/lost/{id}/remove

