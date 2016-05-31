#微首页

####添加微首页
>/api/template/add
>organizationId
>name
>isActive
>json

###更新微首页
>/api/template/{id}/update
>organizationId
>name
>isActive
>json

####删除微首页
>/api/template/{id}/remove

####设置为启用微首页
>/api/template/{templateId}/active
>resultOK


####获取微首页
>/api/template/{id}/get
>resultOk(template)
>resultError(没有权限)

####获取获取开启的微首页
>/api/template/get-active-template
>resultOk(template)
>resultError()

####列出微首页
>/api/template/list
>organizationId
>skip
>limit
>list(OrgTemplateVo)