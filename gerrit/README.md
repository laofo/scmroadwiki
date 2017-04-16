# Gerrit

标签（空格分隔）： gerrit

#简介

Gerrit，一种免费、开放源代码的代码审查软件，使用网页界面。利用网页浏览器，同一个团队的软件程序员，可以相互审阅彼此修改后的程序代码，决定是否能够提交，退回或者继续修改。它使用Git作为底层版本控制系统。它分支自Rietveld，作者为Google公司的Shawn Pearce，原先是为了管理Android计划而产生。（摘自百度百科）

本章节，将从gerrit的搭建开始详细介绍gerrit应用，包括：gerrit安装、登陆与配置……

#安装
##服务器
gerrit服务器同时支持Linux和windows，这里只研究Linux下的安装。由于gerrit为war包安装，需要jdk环境；此外，由于gerrit自带的web服务不能鉴权，所以还需要单独安装web服务，本文采用nginx。
gerrit war包下载地址：
`http://gerrit-releases.storage.googleapis.com/`
目前最新版本为gerrit-2.13.7
##客户端
gerrit底层是git，所以客户端安装Git Bash。
#使用建议

#实用的gerrit命令

#相关资料