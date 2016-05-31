#安装Redis集群
##### 1: 将Redis解压至/usr/local/
##### 2: cd至/usr/local/redis/执行命令
>make
make install

##### 3: 创建工作目录
>mkdir /server/redis

##### 4: 修改redis.conf文件
>daemonize yes
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
appendonly yes
dir /server/redis

##### 5: 安装ruby,gem,redis-ruby接口
>apt-get install ruby
apt-get install rubygems
gem install redis

##### 6:创建集群命令
>.到src 执行集群命令
--replicas 1 salve数量
/redis-trib.rb  create --replicas 1 hostname:port(example:127.0.0.1:7000)

#### 7:redis-cli命令进入集群环境
>redis-cli -c -h host -p port