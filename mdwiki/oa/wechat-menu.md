#公众号菜单说明文档(OA)
####创建或更新菜单
>/wechat/menu/set:POST
publicId:
menus:菜单,示例如下
[
	{"name":"m1",
		"content":"ctn",
		"menuType":"VIEW | CLICK", 
		"info":"",//前台自定义信息
		"subMenus":[
			{name,content,menuType,info},
			{..}
		]
	},

	{..}
]

####获取公众号菜单
>/wechat/menu/get:GET
publicId