# Gerrit

标签（空格分隔）： gerrit

# 简介

Gerrit，一种免费、开放源代码的代码审查软件，使用网页界面。利用网页浏览器，同一个团队的软件程序员，可以相互审阅彼此修改后的程序代码，决定是否能够提交，退回或者继续修改。它使用Git作为底层版本控制系统。它分支自Rietveld，作者为Google公司的Shawn Pearce，原先是为了管理Android计划而产生。（摘自百度百科）

本章节，将从gerrit的搭建开始详细介绍gerrit应用，包括：gerrit安装、登陆与配置……

# 安装
## 服务器
gerrit服务器同时支持Linux和windows，这里只研究Linux下的安装。由于gerrit为war包安装，需要jdk环境；此外，由于gerrit自带的web服务不能鉴权，所以还需要单独安装web服务，本文采用nginx。
gerrit war包下载地址：
`http://gerrit-releases.storage.googleapis.com/`
目前最新版本为gerrit-2.13.7
## 客户端
gerrit底层是git，所以客户端安装Git Bash。
# 使用建议

# 实用的gerrit命令
其实就是git命令：
1、git克隆库
git clone <远程库路径> -origin <本地库名>

2、git 创建本地分支，并提交，push
git branch <本地分支名> origin/master  --------------从master创建本地分支
git checkout <本地分支名>  ------------------切换到新建分支
git push origin <本地分支名> -u ---------------提交到远程库，-u 是把本地分支的upstream由原来的origin/master 改为跟本地分支同名的远程分支

3、设置提交分支
git branch --set-upstream-to=origin/master master

4、分支合并及冲突解决（例如将分支b1合回主线master）
先进入主线：git checkout master；
合并分支：git merge b1；
查看冲突：git status；
找到冲突文件，手动修改冲突，修改完成后保存；
将修改后的文件缓存（即标记为resolved）：git add  <fileName>;  ##git没有标记解决的功能，因此只要把修改缓存即git add之后，就相当于标记冲突为已解决状态。
提交本地仓库：git commit -am "log";
提交远程仓库：git push；
# 相关资料
以下均为百度出来的参考：
[git常用命令][1]
[gerrit安装手册][2]
[gerrit升级注意事项][3]


  [1]: http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html
  [2]: http://blog.csdn.net/benkaoya/article/details/8680886
  [3]: http://www.qdfuns.com/notes/19519/360c5520093835754e3a2d15af3ee67e.html