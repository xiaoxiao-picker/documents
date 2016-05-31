####组织附件&&图片库

####添加附件
>/api/attach/{type}/upload
>organizationId
>uploadfile
>classId 图片库分组id
>type IMAGE, MUSIC, FILE
>return resultOK(id)

####切图片
>/api/attach/IMAGE/cut
>key
>x
>y
>w
>h
>scale
>resultOK(url)

####列出附件
>/api/attach/{type}/list
>organizationId
>skip
>limit

####获取附件信息
>/api/attach/{id}/get
获取图片，附件信息
>

####更新附件别名
>/api/attach/{id}/udpate
>name
>result OK

####删除附件
>/api/attach/remove
>organizationId
>ids

####图片库分组添加
>/api/picture-class/add
>organizationId
>name
>code

####图片库分组更新
>/api/picture-class/{id}/update
>name
>code

####获得图片库信息
>/api/picture-class/{id}/get
>resultOK


####图片库分组删除
>/api/picture-class/{id}/remove

####列出图片库分组
>/api/picture-class/list
>organizationId

####列出图片库分组下的图片
>/api/picture-class/{id}/picture/list
>skip
>limit

####切换图片所在分组
>/api/picture-class/picture/switch
>organizationId
>classId
>ids(图片id)
>return resultOk