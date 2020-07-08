# Git中的基本操作
## 			通过Http进行连接

### 					普通的文件上传至github

1.先在github上创建repository库
2.然后在本地创建一个文件夹repository，并使用命令  git init  创建一个本地仓库
3.通过使用命令  git add .  将文件添加到本地仓库的缓存中，再使用  git commit -m “提交时的备注”
4.通过使用命令  git config --global user.name "你的github用户名" 输入用户名，通过
git config --global user.email "你的github邮箱"
5.然后要连接github上的repository，使用  
git remote add origin https://github.com/在github用户名/github上创建的repository库名.git
6.再使用  git push -u origin master命令进行提交

注意：出现fatal: remote origin already exists时使用  git remote rm origin 将之前的连接进行移除



git add [file name] 可以是 .  将工作区的“新建/修改”添加到暂存区

git status 可以查看工作区、暂存区中存在的文件

git commit -m "commit message" [file name] 是将文件添加到本地仓库

git rm --cached <file,文件名称> ... 将暂存区的文件删除



### 查看历史记录

git log

git log --pretty=oneline

git log --oneline

git reflog 查看历史记录

​	基于索引值操作：前进后退版本操作

​		git reset --hard [局部索引值]

​	使用^符号：只能后腿

​		git reset --hard HEAD^

​		一个^符号表示后退一步，n个表示后退n步

​	使用~符号：只能后退

​		git reset --hard HEAD~n

​		表示后退n步



### reset命令的三个参数对比

​	--soft参数

​		仅仅只是移动一下head指针

​	--mixed参数

​		在本地库移动head指针

​		重置暂存区

​	--hard参数

​		在本地库移动head指针

​		重置暂存区

​		重置工作区

### 文件添加到本地库之后删除及取回

​	前提：删除前，问价你存在时的状态提交到了本地库

​		git reset --hard [局部索引值]

### 文件添加到缓存中之后删除及取回

​		git reset --hard HEAD

### 比较稳健差异

​		git diff [文件名]

​	将工作区中的文件与暂存区进行比较



​		git diff [本地库中历史版本] [文件名]

​	将工作区中的文件和本地库历史记录比较



​	不带文件名的时候比较多个文件

​		gif diff HEAD

### 将远端的文件clone下来

​	1.使用  git clone 文件夹路径



# Git的分支

## 什么是分支

​	在版本控制过程中，使用多条线同时推进多个任务。

master 主干

feature_blue 分支

## 分支的好处

​	同时并行推进多个功能开发，提高开发效率

​	各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响，失败的分支删除重新开始即可。

## 分支操作

创建分支

​	git branch [分支名]

查看分支

​	git branch -v

切换分支

​	git checkout [分支名]

合并分支

​	第一步：切换到接受修改的分支上（被合并，增加的新内容）上

​		git checkout [被合并分支名]

​	第二步：执行merge命令

​		git merge [有新内容分支名]

解决冲突