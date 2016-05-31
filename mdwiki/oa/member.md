#member接口
####添加用户到组织
>/api/member/add
>userId
>organizationId
>rank
>remark

####添加用户到组织
>/api/member/add-by-phone-number
>phoneNumber
>organizationId
>rank
>remark


####更新用户备注
>/api/member/update-remark
>userId
>organizationId
>remark

####更新用户等级
>api/member/update-rank:POST
rank
ids


####更新用户备注
>/api/member/{id}/remark/update

####删除用户组织关联
>/api/member/{id}/remove
>userId
>organizationId

####列出组织下的用户成员--rank -1 rank 0 
>/api/member/list-user-by-organization
>organizationId
>rank 大于rank级别的人
>-1 所有的用户，所有的管理员
>return list(user)

####累出用户所参加的所有组织
>/api/member/list-organization-by-user
>userId
>rank &gt;-1 所有的参加的组织 &gt;0 所有管理的组织
>return list(organization)

####列出组织成员数
>/api/member/count POST
>organizationId
>return count

####列出组织分组
>/api/member/group/list GET
>organizationId
>skip
>limit
>return groupVo

####添加组织分组
>/api/member/group/add
>name
>organizationId

####获取组织分组和下面成员
>/api/member/{groupId}/get
>groupId
>return group  membervos

####更新组织分组
>/api/member/group/{groupId}/update
>name
>organizationId

####删除组织分组
>/api/member/group/{groupId}/remove POST
>return resultOK

####添加member到分组
>/api/member/add-to-group POST
>groupId
>memberIds
>return resultOK

####从分组删除member信息
>/api/member/remove-from-group POST
>groupId
>memberIds
>return resultOK

####列出没有分组的成员
>/api/member/list-member-by-no-group
>organizationId
>skip
>limit


####申请加入组织
>/api/member/apply
>organizationId

####组织未处理的加入申请
>/api/member/apply/count
>organizationId

####获取加入组织申请信息
>/api/member/apply/{id}/get
>

####申请列表
>/api/member/apply/list
>organizationId

####同意申请
>/api/member/apply/{id}/agree
>organizationId
>id

####拒绝申请
>/api/member/apply/{id}/refuse
>organizationId
>id


####组织管理员评价成员
>/api/member/comment/add
>userId
>organizationId
>text

####获取某成员组织下的评论
>/api/member/comment/list
>userId
>organizationId


####删除评论
>/api/member/comment/{id}/remove

####获取评论
>/api/member/comment/{id}/get


