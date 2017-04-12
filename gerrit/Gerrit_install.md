# Gerrit安装

标签（空格分隔）： gerrit

---目录---

##服务端（Linux）
由于gerrit为war包安装，需要jdk环境；此外，由于gerrit自带的web服务不能建权，所以还需要单独安装web服务，本文采用nginx。笔者曾尝试过用apache，但是由于apache不能外部鉴权（如ctx），而且不能登出，所以最终选择nginx（openresty），这里需要Lua的知识，来编写nginx需要的脚本。
###下载安装包
笔者安装的是gerrit-2.13.4.war
`wget http://gerrit-releases.storage.googleapis.com/gerrit-2.13.4.war`
###安装依赖
由于gerrit安装包为war包，必须安装jdk
`yum install -y java-1.8.0-openjdk.x86_64`