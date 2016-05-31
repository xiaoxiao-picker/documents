#exhibition接口

####添加学习风采
>api/exhibition/add:POST
>city;
>schoolId;
>terse;
>desc;
>type;
>schoolQrUrl;
>schoolLogo;
>schoolPost
>返回 OK

####添加二维码
>api/exhibition/school/{exhibitionId}/qr-code/add:POST
>exhibitionId;
>qrUrl;
>name;
>category;
>返回 OK

####删除二维码
>api/exhibition/school/qr-code/{qrId}/remove:POST
>qrId
>返回 OK

####删除风采
>api/exhibition/{exhibitionId}/remove:POST
>exhibitionId
>返回 OK

####修改二维码
>api/exhibition/school/qr-code/{qrId}/update:POST
>qrUrl
>category
>name

####修改风采
>api/exhibition/{exhibitionId}/update:POST
>city;
>schoolId;
>terse;
>desc;
>type;
>schoolQrUrl;
>schoolLogo;
>schoolPost
>返回 OK

####获取二维码
>api/exhibition/school/qr-code/{qrId}/get:GET
>qrId
>返回组织二维码信息

####获取风采
>api/exhibition/{exhibitionId}/get:GET
>exhibitionId
>组织风采

####风采列表
>api/exhibition/list:GET
>city
>skip,limit

####二维码列表
>api/exhibition/school/{exhibitionId}/qr-code/list:GET
>skip,limit
