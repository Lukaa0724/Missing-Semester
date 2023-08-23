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
