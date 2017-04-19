# Gerrit安装

标签（空格分隔）： gerrit

---目录---

## 服务端（Linux）
由于gerrit为war包安装，需要jdk环境；此外，由于gerrit自带的web服务不能建权，所以还需要单独安装web服务，本文采用nginx。笔者曾尝试过用apache，但是由于apache不能外部鉴权（如ctx），而且不能登出，所以最终选择nginx（openresty），这里需要Lua的知识，来编写nginx需要的脚本。
### 下载安装包
笔者安装的是gerrit-2.13.4.war

    wget http://gerrit-releases.storage.googleapis.com/gerrit-2.13.4.war
### 安装依赖
由于gerrit安装包为war包，必须安装jdk

    yum install -y java-1.8.0-openjdk.x86_64
root用户下安装git

    yum install git
本文gerrit用的是mysql数据库，因此需要提前创建gerrit所需的数据库

    create database gerrit_db;
    grant all privileges on gerrit_db.* to reviewdb_new@'%' identified by 'reviewdb_new'

### 安装gerrit

    java -jar /opt/gerrit-2.13.4.war init -d /opt/gerrit_site/
安装gerrit过程会有几个问题，例如：
•Git代码库的位置 [git]
•导入现有代码库 [Y/n]
•数据库服务器类型 [H2/?]
•身份验证方法 [OPENID/?]
•SMTP服务器主机名 [localhost]
•SMTP服务器端口 [(default)]
•SMTP加密 [NONE/?]
•SMTP用户名
•以何种身份运行 [root]
•Java运行时 [/path/to/jvm]
•将gerrit.war复制到/path/to/location/bin/gerrit.war [Y/n]
•监听地址 [\*]
•监听端口 [29418]
•下载并安装Bouncy Castle[Y/n]
•位于HTTP反向代理之后 [y/N]
•使用SSL [y/N]
•监听地址 [*]
•监听端口 [8080]
•访问地址url [http://CDCS-213057230/]
由于安装时数据库选择mysql（即 数据库服务器类型 [H2/?] 输入mysql），所以需要下载相应的mysql jar包（如：https://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.21/mysql-connector-java-5.1.21.jar），gerrit会自动下载，但是需要安装的服务器能上网哦~~
选择数据库类型为mysql，就需要输入以下参数：

    Server hostname                [localhost]: mysql服务器IP
    Server port                    [(mysql default)]: mysql服务器端口
    Database name                  [reviewdb]: 数据库名称
    Database username              [root]: username
    reviewdb_new's password        : 
                  confirm password : 

当出现“Initialized <your gerrit_path>”（对照本文为 “Initialized /opt/gerrit_site/”）时，说明初始化完成。
### 启动gerrit服务

    /opt/gerrit_site/bin/gerrit.sh start
    Starting Gerrit Code Review: OK
启动成功，可以web访问啦！地址为你初始化时填写的url。