####用户操作日志
>/log/rank/list:GET
organizationIds:逗号分割
targetType:EVENT, ARTICLE, POLL, PROPOSAL, MEMBER, WALL, TICKET, VOTE, FEEDBACK, LOST, HOME, SENATE, RELATION, ORGANIZATION,WECHAT_ARTICLE, HISTORY, NOTICE, NOTIFICATION, RESUME, USER, COMMENT

targetSubType:EVENT, EVENT_SIGNUP, ARTICLE, POLL, PROPOSAL, MEMBER, WALL, TICKET, VOTE, FEEDBACK,
        LOST, FIND, HOME, BIND, ROUTE, SCORE, TIMETABLE, UNSOLVED, SOLVED, USER,
        POLL_SIGNUP, POLL_STATISTICS, ORGANIZATION, ZONE, JOIN,
        WECHAT_ARTICLE, WALL_INFO, WALL_LOTTERY, WALL_MESSAGE,
        VOTE_PLAYER, VOTE_STATISTICS, HISTORY, NOTICE, NOTIFICATION, RESUME, COMMENT


operationType:LIST, GET, GET_EDIT, ADD, UPDATE, REMOVE, SIGNUP, CANCEL_SIGNUP, PRAISE, CANCEL_PRAISE
startDate
endDate
skip
limit
sortBy: targetType
除skip,limit其他都是选填

>/log/{organizationId}/detail:GET
startDate
endDate

>/log/list:GET 获取列表
organizationIds:逗号分割
userIds:逗号分割
targetType:targetType:EVENT, ARTICLE, POLL, PROPOSAL, MEMBER, WALL, TICKET,VOTE,FEEDBACK
operationType:ADD, UPDATE, REMOVE, SIGNUP, CANCEL_SIGNUP, PRAISE, CANCEL_PRAISE
startDate
endDate
skip
limit
除skip,limit其他都是选填

####根据组织集合统计用户操作数
>/log/count-by-organizations:GET
organizationIds:组织标识
userIds
targetType
operationType
startDate
endDate
