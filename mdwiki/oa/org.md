#org接口
####创建组织
>/api/org/add
>name
>description
director.user.id;
school.id;
orgType: 
        MANAGER, DEPARTMENT, OTHER, STUDENT_UNION, ART, PUBLIC_SERVICE, ORGANIZATION
isSchool;
email;
logoUrl;
permit;

####搜索组织
/api/org/list
>keyword
>orgType
>schoolId
>skip 必
>limit 必

####获取组织信息
>/api/org/{orgId}/get

####获取组织拓展信息
>/api/org/{orgId}/extend/get

####删除组织
>/api/org/{orgId}/remove

####更新组织
>/api/org/{orgId}/update
>name
>description
directorId;
school.id;
orgType;
isSchool;
email;
logoUrl;
permit;

####添加关联组织
>/api/org/{organizationId}/relate/add
>relateOrgId
>return resultOK

####添加加入组织条件
>/api/org/{organizationId}/register/add
>registerJson


####更新加入组织条件
>/api/org/{organizationId}/register/upate
>registerJson ＝{
    "texts": [
        {
            "id": "",
            "title": "name",
            "type": "TEXT",
            "required": true,
            "rank": 1
        },
        {
            "id": "",
            "title": "tel",
            "type": "TEXT",
            "required": true,
            "rank": 2
        },
        {
            "id": "",
            "title": "gender",
            "type": "TEXT",
            "required": true,
            "rank": 3
        },
        {
            "id": "",
            "title": "ewr",
            "required": true,
            "rank": 7,
            "type": "TEXT"
        }
    ],
    "dates": [],
    "choices": [
        {
            "id": "",
            "title": "gfhfgh",
            "required": true,
            "rank": 8,
            "type": "MULTIPLE",
            "options": [
                {
                    "id": "",
                    "name": "sdfg",
                    "rank": 1
                },
                {
                    "id": "",
                    "name": "sdfg",
                    "rank": 2
                }
            ]
        }
    ],
    "images": []
}

####获取加入组织条件
>/api/org/{organizationId}/register/get


####删除关联组织
>/api/org/{organizationId}/relate/remove
>relateOrgId
>return resultOk




####获取关联组织
>/api/org/{organizationId}/relate/list
>skip
>limit
>return resultList(OrganizationVo

####更新组织设置
>/api/org/{organizationId}/config/update
>isFirstSetHomePage
>relateOrgsArticleDisplayName
>relateOrgsEventDisplayName
>organizationId
>advAvailable

####获取组织设置
>/api/org/{organizationId}/config/get
>resultOK()

####组织分类添加
>/api/org/{organizationId}/class/add
>name
>resultOK(id)

####获取组织分类
>/api/org/{organizationId}/class/list
>skip
>limit

####组织分类更新
>/api/org/{organizationId}/class/{classId}/update
>name
>resultOK

####删除组织分类
>/api/org/{organizationId}/class/{classId}/remove
>resultOk

####get组织分类
>/api/org/{organizationId}/class/{classId}/get
>resultOK


