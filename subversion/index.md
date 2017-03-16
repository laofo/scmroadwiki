# 简介
Subversion是一个自由开源的版本控制系统。在Subversion管理下，文件和目录可以超越时空。Subversion将文件存放在中心版本库里，这个版本库很像一个普通的文件服务器，不同的是，它可以记录每一次文件和目录的修改情况，这样就可以借此将数据恢复到以前的版本，并可以查看数据的更改细节。正因为如此，许多人将版本控制系统当作一种神奇的“时间机器”。

# 安装
### 客户端
Subversion的客户端有两类，一类是WebSVN等基于Web的，一种是以TortoiseSVN为代表的客户端软件。前者需要Web服务器的支持，后者需要用户在本地安装客户端，两种都有免费开源软件供使用。
### 服务端
Subversion支持Linux和Windows，更多是安装在Linux下。   
SVN服务器有2种运行方式：独立服务器和借助Apache。2种方式各有利弊。   
SVN存储版本数据也有2种方式：Berkeley DB和FSFS。因为Berkeley DB方式在服务器中断时，有可能锁住数据，所以还是FSFS方式更安全一点。

# 使用建议

1. 养成良好的记录日志的习惯。   
  svn ci提交，最好在日志中记下清晰明确的信息,这个非常重要,对以后的维护(包括合并)都有很大帮助。

2. 格式统一。   
  开发人员提交的文件格式要保持一致,统一为DOS格式或者UNIX格式,同时提交前对源代码采用统一的风格格式化（比如jalopy）,这样对以后的合并、查看修改信息会更加方便。

3. 如何把分支合并到主干上。   
  只需要比较分支的初始状态与最终状态，然后将这些分支的修改应用到主干目录的工作拷贝。步骤：   
  (1)、在本地将最新的主干取出   
    svn co http://svn.example.com/repos/example/trunk example   
  (2)、到当前的example目录下合并分支,4889,4906分别表示分支的最初版本号和最终版本号   
    svn merge -r 4889:4906 http://svn.example.com/repos/example/branches/branches_test

# 典型的svn目录结构
project/branches/   
project/tags/   
project/trunk/   


# 实用的SVN命令
* svn copy 创建分支或者标签   
  svn copy http://svn.example.com/repos/calc/trunk http://svn.example.com/repos/calc/tags/release-1.0 -m "Tagging the 1.0 release of the 'calc' project."

* svn switch 切换工作拷贝到指定的分支或者返回主干   
  svn switch http://svn.example.com/repos/calc/branches/my-calc-branch

* svn diff 版本比较   
  svn diff rules.txt           比较本地修改   
  svn diff --r 3 rules.txt    比较工作拷贝和版本库   
  svn diff --r 2:3 rules.txt  比较版本库与版本库   

* svn revert  删除你的本地修改,恢复到修改前的状态.

* 查一个过去的版本,重定向输出到一个文件   
  svn cat -r 2 rules.txt > rules.txt.v2

* svn info  查看当前工作拷贝是在主干还是在哪个分支上。


# 相关资料
[Subversion官网](http://subversion.apache.org/)   
[Subversion与版本控制(在线图书)](http://svnbook.red-bean.com/)