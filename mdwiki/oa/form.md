#表单接口

####添加表单
>api/form/add:POST
>orgId
>title
>terse
>registerJson
>返回 OK

####删除表单
>api/form/{formId}/remove:POST
>orgId
>返回OK

####更新表单
>api/form/{formId}/update:POST
>orgId
>title
>terse
>regiserJson
>返回 OK

####获取表单列表
>api/form/list:GET
>orgId
>skip
>limit
>返回表单列表

####获取表单
>api/form/{formId}/get:GET
>formId
>返回 表单

####提交表单
>api/form/{formId}/fill:POST
>formId
>fillFormInfo
>返回 OK

####开启表单
>api/form/{formId}/open:POST
>formId
>返回 OK

####关闭表单
>api/form/{formId}/close:POST
>formId
返回 OK

####表单结果取得
>api/form/{formId}/result/get:GET
>formId
>返回 表单结果

####表单结果集
>api/form/{formId}/result/list:GET
>formId
>返回 表单结果集

####删除指定表单结果
>api/form/{formId}/result/remove:POST
>formId
>返回 OK

####清除表单结果集
>formId
>返回 OK

