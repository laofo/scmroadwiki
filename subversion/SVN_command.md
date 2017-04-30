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
