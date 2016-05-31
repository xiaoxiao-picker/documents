#DeBian7.5安装Java环境
##### 1: 新建/usr/lib/jvm目录
##### 2: 将jdk解压至/usr/lib/jvm
##### 3: 编辑/etc/profile, 在文件末尾添加
>export JAVA_HOME=/usr/lib/jvm/jdk1.8.0 
export JRE_HOME=${JAVA_HOME}/jre 
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib 
export PATH=${JAVA_HOME}/bin:$PATH

##### 4: 使用命令更新配置
> source /etc/profile

##### 5: 使用命令配置java, javac
> update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0/bin/java 300 
update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0/bin/javac 300

##### 6: 修改默认配置(第一次安装请跳过)
> update-alternatives --config java 
update-alternatives --config javac