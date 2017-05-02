# SVN常用命令整理

## 1.基本命令
### （1）查找帮助 svn help   
详细的 import 命令的用法。
```
svn help import
```
### （2）导入 svn import
将一个工程加入到svn中，eg
```
svn import testproject [ur | file path]
```
注：testproject 为工程目录路径
### （3）检出代码 svn co [url | path]
```
svn co http://test.com/svn/test_project/
```
### （4）增删改
#### 加入项目 svn add [file | floder]
将foo添加入工程，若foo为目录，所有文件都将加入
```
svn add foo
```
若只想加入目录本身
```
svn add foo --non-recursive
```
#### 删除 svn delete [file | floder]
```
svn delete foo
```
#### 改名 svn move old_name new_name
类似linux的mv
```
svn move foo foo1
```
#### 创建目录 svn mkdir floder_name
```
svn mkdir blort
```
### （5）检查修改
#### 查看状态 
```
svn status
```
#### 对比不同 
```
svn diff
```
#### 生成补丁包 svn patchfile
```
svn diff > pathfile
```
#### 同具体的版本进行diff
```
svn diff -r 3
```
#### 比较具体两个版本号的diff
```
svn diff -r 2:3
```
### （6）更新代码及解决冲突
```
svn up
```
or
```
svn update
```
### （7）提交修改
```
svn commit
```
### （8）检查历史
```
svn log
```
### （9）浏览版本库
```
svn list
svn cat
```
## 2.版本管理
### （1）svn的版本号是一类数字，也可以用特定的关键字表示版本
HEAD: 版本最新的版本号
BASE: 工作拷贝中一个条目的修订版本号
COMMITTED: 项目最近修改的修订版本，与BASE相同或更早
PREV: commit之前的一个版本
eg.看最新版本的修改
```
svn log -r HEAD
```
此时HEAD就会被解释为最新的版本号

### （2）用时间查找版本号
```
svn log -r {2017-04-01}:{2017-04-30}
```

## 3.分支与合并
在一个工程目录里都有一个主干trunk目录和一个分支branches目录。   
<br />
当一个项目很大，有多个人协作开发时，如果大家都在主干目录开发时容易造成混乱。当你一个人开发一个功能模块时，而开发周期可能比较长才能完成该功能，此时你不能将未完成的代码提交到主干，容易造成混乱。此时你可开一个分支，然后在你这个分支目录下工作。   
### （1）创建分支
- svn copy [ url ] [ url ]   

eg. 创建 test_branch 分支
```
svn copy http://test.com/svn/test/trunk http://test.com/svn/test/branches/test_branch
```

### （2）合并分支
当你开发周期较长时，而此时主干代码已经发生更交，若时间过长，很可能你的支支与主干脱节，此时要将主干更新的代码合并到你的分支上。   

- svn merge url

eg. 将主干部分更新代码合并到你的分支上。
```
svn merge http://test.com/svn/test/trunk
