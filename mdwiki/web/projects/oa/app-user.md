### AppUser 对象
    该对象为window全局对象，对象结构为：
    AppUser:{
        //属性
        userInfo://Object：用户信息
        organization://Object：当前组织信息
        organizations://Array：当前用户所能管理的组织列表
        
        //方法
        setSession://手动设置当前会话
        getSession://读取当前会话
        clearSession://清除会话

        init://初始化用户
        auth://请求登录
        logout://退出登录，清除会话
    }