这篇笔记参考了廖雪峰的git教程，这本书同时放在仓库中，有需要的可以自行下载

# git diff (file)
即git difference 查看文件的不同（修改）

# git reset --hard (commit id)
HEAD 指向的版本的就是当前版本，通过上面的指令就可以回到指令版本，但是有一个问题，回退到上一个版本后发现**git log**后没有没有了最新的版本，这时候就需要**git reflog**指令来展示所有的提交，这时候就会展现出所有的commit id

当然，也有一些**其他**的写法，例如

    $ git reset --hard HEAD^  //回退到上一个版本
    $ git reset --hard HEAD~100 //回退到前一百个版本

# git checkout -- (file)
简单来说就是将文件回到最近一次的git add或者git commit的状态
- ⼀种是README.md⾃修改后还没有被放到暂存区，现在，撤销修改就回到和版本库⼀模⼀
样的状态；
- ⼀种是README.md已经添加到暂存区后，⼜作了修改，现在，撤销修改就回到添加到暂存
区后的状态。

# git reset HEAD file
撤销（unstaged）暂存区中的东西，即在git add后删除暂存区中的东西。git reset命令既可以回退版本，也可以把暂存区的修改回退到⼯作区。当我们⽤HEAD时，表⽰最新的版本。接着可以丢弃工作区的修改，即回到上一次commit的状态，使用**git checkout -- file** 指令。

# git rm file 
删去git 文件，easy，然后配合git commit 

# 远程仓库
在github设置ssh密匙后，使用两个指令即可同步本地库和远程仓库

    git remote add origin git@githubcom:michaelliao/（file address)

    git push -u origin master

在第一次关联master分支后，后面只需git push即可同步远程仓库。

# 克隆仓库
很简单 直接

    git clone (项目地址)

就ok了，非常easy

# 分支管理（）
在版本回退中，我们已经知道，每次提交，Git把他们穿成一条时间线，这条时间线就是一个分支。

一开始的时候，master分支是一条线，Git用master指向最新的提交，然后再用HEAD指向master，就能够确认分支以及当前分支的提交点。

如果新建一个新的分支，dev，指向与master相同的提交然后再把HEAD指向dev，就表示当前分支在dev上。接下来对于工作区的提交和修改就是针对dev分支了，比如新一次提交后，dev指针向前移动一步而master指针不变。

加入我们把dev分支上的任务完成了并且想要把dev合并到master上，很简单，只需要将master指针指向dev的当前提交，就完成了合并。

# git checkout -b dev
新建一个dev分支 -b很明显是branch的意思

checkout 后面 + -b 表示创建并且切换，相当于两条指令
```shell
    git branch dev //创建分支
    git checkout dev //切换到分支
```
# git branch 
列出所有分支，当前分支前面会加上*

# git merge (branch)
合并制定分支到当前分支

# git branch -d (branch)
删除指令分支

# 分支管理策略（pdf 44-60 学的不够深入）
通常合并分支我们希望使用Fast forward模式，但是这样删除分支可能会丢掉分支信息。可以尝试no ff方式的merge，目前很少用到，暂且不展开，有时间继续。

# 多人协作
当从远程仓库进行clone时，git实际上是把master分支和远程的master分支对应起来，并且远程仓库的名字默认是origin。
# git remote
查看远程仓库信息
```bash
    git remote -v 
```
查看更加详细的远程仓库的信息。
# 推送分支
把本地的分支推送到远程仓库，比如
```bash
    git push origin master
    git push origin dev
```
分别推送master分支和dev分支

