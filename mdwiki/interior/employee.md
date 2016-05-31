#员工API
####添加员工
>/employee/add:POST

####删除员工
>/employee/{employeeId}/remove:POST

####查询员工
>/employee/{employeeId}/get:GET

####查询员工列表
>/employee/list:GET
keyword
skip
limit

####查询员工组织列表
/employee/{employeeId}/list-organizations:GET

####添加员工组织
/employee/{employeeId}/add-organization:POST
organizationId

####删除员工组织
/employee/{employeeId}/remove-organization:POST
organizationId

####员工信息
id
name
entryDate 入职时间
contactInfo 联系方式
organizationsOfManagement 管理的组织
userId 校校用户标识
