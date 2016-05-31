#广告

####list classes
>/api/advertisement/classes/list
>keyword

####list favourite classes
>/api/advertisement/classes/list-favourite	
>limit;


####get advertisement
>/api/advertisement/{sourceType}/{sourceId}/get


####open advertisement
>/api/advertisement/{advertisementId}/open

####close advertisement
>/api/advertisement/{advertisementId}/close


####某个广告收益list
>/api/advertisement/{advertisementId}/statistics/list
>startDate
>endDate
>skip
>limit

####某个分类＋分类id的收益list
>/api/{sourceType}/{sourceId}/statistics/list
>startDate
>endDatee
>skip
>limit

>/api/{sourceType}/{sourceId}/statistics/get-sum
>startDate
>endDate

####列出组织的按天的广告数据
>/api/advertisement/statistics/list-group-by-date
>organizationId
>startDate
>endDate

####某个组织下面广告收益记录
>/api/advertisement/statistics/list
>organizationId
>startDate
>endDate
>skip
>limit


####列出广告
>/api/advertisement/list
>organizationId
>skip
>limit


####添加广告
>/api/advertisement/add
>organizationId
>classes
>sourceId
>sourceType


####更新广告
>/api/advertisement/update
>sourceId
>sourceType
>classes


####删除广告
>/api/advertisement/remove
>sourceId
>sourceType

