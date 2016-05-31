##失物招领

####添加失物招领
>/api/lost/add
>organizationId
>title
>location
>eventDate
>contactInfo
>text
>type 	LOST FIND
>picUrls ,
>userId  
>orgId
>isCompleted

####更新失物招领
>/api/lost/{id}/update


####列出失物招领
>/api/lost/list
>organizationId
>type
>limit
>skip


####删除失物招领
>/api/lost/{id}/remove
删除失物招领

####获取失物招领
>/api/lost/{id}/get

####置顶失物
>/api/lost/{id}/top

####不置顶失物
>/api/lost/{id}/untop

####修改状态,是否完成
>/api/lost/{id}/change-status
status true false
