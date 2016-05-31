#学校接口

####添加学校
>api/school/add:POST
>name
>shortName
>country
>province
>返回 id

####更新学校
>api/school/{id}/update:POST
>name
>shortName
>country
>province
>返回 

####删除学校
>api/school/{id}/remove

####获取学校
>/api/school/{id}/get


####列出学校
>/api/school/list
>province 非
>name     非,模糊匹配

