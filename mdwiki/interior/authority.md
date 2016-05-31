####权限管理接口
######操作码列表
>/authority/operation/list:GET

####更新操作码
>/authority/{code}update
>name
>remark

####获取操作码
>/authority/{code}/get


######添加操作码
>/authority/operation/add:POST
code
name
remark

######添加角色
>/authority/role/add:POST
name
remark

####获取角色
>/authority/role/{roleId}/get : get

####更新角色
>/authority/role/{roleId}/update: post
name
remark

######角色列表
>/authority/role/list:GET

######角色对应操作
>/authority/role/{roleId}/operation/list:GET

######角色添加操作
>/authority/role/{roleId}/operation/add:POST
operationCode

######角色删除操作
>/authority/role/{roleId}/operation/remove:POST
operationCode

######用户对应角色
>/authority/user/{userId}/role/list:GET

######用户添加角色
>/authority/user/{userId}/role/add:POST
roleId

######用户删除角色
>/authority/user/{userId}/role/remove:POST
roleId
