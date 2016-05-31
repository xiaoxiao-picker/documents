#user  nobody;
worker_processes  4;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  10240;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    client_max_body_size 30m;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    gzip  on;

    upstream xx-backends {
        server 10.173.160.208:8080;
        server 10.173.161.200:8080;
    }

    server {
        listen       80;
        server_name  oa.xiaoxiao.la;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;


        location / {
            alias web/;
            index  index.html index.htm;
        }

        location /api {
            proxy_pass http://localhost/api-oa;
        }

        location /api-oa {
            proxy_pass http://xx-backends;
            proxy_set_header X-Real-IP $remote_addr;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}

        #微首页
        rewrite organization/index.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/index&pid=$arg_pid? permanent;
        #组织信息
        rewrite organization/zone.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/zone? permanent;
        #组织申请加入
        rewrite organization/join.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/join? permanent;
        #组织风采
        rewrite organization/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/list/school? permanent;
        #手动添加组织的信息
        rewrite organization/info.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/exhibition/$arg_relateId/info/school&isManual=$arg_isManual? permanent;
        #电子票检票
        rewrite organization/checkticket.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/ticket/$arg_sid/check? permanent;
        #组织申请成员列表
        rewrite organization/applyList.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/apply/list? permanent;
        #组织风采
        rewrite organization/applyInfo.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/apply/$arg_aid/info? permanent;

        #用户信息
        rewrite account/setting.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/user/zone? permanent;
        #图文回复信息页面
        rewrite autoReply/info.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/wechat/article/$arg_id/info? permanent;

        #评论
        rewrite comment/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/$arg_stype/$arg_sid/comments? permanent;

        #活动列表classification
        rewrite events.html(.*)classification=(.+) http://front.xiaoxiao.la/index.html#organization/$arg_oid/events&categoryId=$arg_classification? permanent;
        rewrite events.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/events&categoryId=$arg_category? permanent;
        #活动信息
        rewrite event.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/event/$arg_eid/info? permanent;
        #活动报名
        rewrite event/register.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/event/$arg_eid/signup? permanent;

        #投票列表
        rewrite votes.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/votes? permanent;
        #投票信息
        rewrite vote.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/vote/$arg_vid/info? permanent;


        #文章列表
        rewrite articles.html(.*)classification=(.+) http://front.xiaoxiao.la/index.html#organization/$arg_oid/articles&categoryId=$arg_classification? permanent;
        rewrite articles.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/articles&categoryId=$arg_category? permanent;
        #文章信息
        rewrite article.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/article/$arg_aid/info? permanent;


        #投票信息
        rewrite event/vote.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/vote/$arg_vid/info? permanent;
        #文章信息
        rewrite event/voteplayer.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/vote/$arg_vid/option/$arg_pid/info? permanent;

        #电子票信息
        rewrite event/robticket.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/ticket/$arg_tid/info? permanent;


        #问卷列表
        rewrite questionnaire/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/questionnaires? permanent;

        #表单列表
        rewrite form/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/questionnaires? permanent;
        #表单信息
        rewrite form/info.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/questionnaire/$arg_rid/info? permanent;

        #失物招领
        rewrite lost/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/lost/list? permanent;

        #提案列表
        rewrite proposal/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/proposals? permanent;

        #上墙展示
        rewrite wall/show.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/wall/$arg_wid/info? permanent;
        #消息上墙
        rewrite wall/add-message.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/wall/$arg_wid/message? permanent;

        # 消息反馈
        rewrite feedback/list.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/user/feedback? permanent;
        # 通知中心
        rewrite user/notices.html(.*) http://front.xiaoxiao.la/index.html#organization/$arg_oid/user/notices? permanent;


        if ($host = 'xiaoxiao.la') {
                rewrite /oa/(.*) http://oa.xiaoxiao.la/$1? permanent;
                rewrite /(.*) http://oa.xiaoxiao.la/$1? permanent;
        }

        if ($host = 'www.xiaoxiao.la') {
                rewrite /oa/(.*) http://oa.xiaoxiao.la/$1? permanent;
                rewrite /(.*) http://oa.xiaoxiao.la/$1? permanent;
        }

    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

}