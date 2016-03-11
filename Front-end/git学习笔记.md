
```
git init  

git status  
git diff  
```

---

#版本回退

HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。

穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。

要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

```
git log --pretty=oneline  
git log --oneline // 简写  
git reflog  

git reset --hard HEAD^  
git reset --hard HEAD^^  
...  
git reset --hard HEAD~13  
```

---

#撤销修改

场景1: 当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

- `git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

场景2: 当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD file`，就回到了场景1，第二步按场景1操作。

---

#删除文件

$ git rm xxx.xx // 命令git rm用于删除一个文件

---

#添加远程库

详情见：[廖雪峰的这篇文章](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000)

要关联一个远程库，使用命令`git remote add origin git@github.com:zhaokang555/xxx.git`或者`git remote add origin https://github.com/michaelliao/gitskills.git`

关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容

- 我们第一次推送master分支时，加上了`-u`参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改

---

#从远程仓库克隆

`git clone git@github.com:michaelliao/gitskills.git`或者`git clone https://github.com/michaelliao/gitskills.git`

要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

GitHub给出的地址不止一个，还可以用`https://github.com/michaelliao/gitskills.git`这样的地址。实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。

---

#网上找的git常用命令总结

Git基本常用命令如下：

- mkdir：         XX (创建一个空目录 XX指目录名)
- pwd：          显示当前目录的路径。
- git init          把当前的目录变成可以管理的git仓库，生成隐藏.git文件。
- git add XX       把xx文件添加到暂存区去。
- git commit –m “XX”  提交文件 –m 后面的是注释。
- git status        查看仓库状态
- git diff  XX      查看XX文件修改了那些内容
- git log          查看历史记录
- git reset  –hard HEAD^ 或者 git reset  –hard HEAD~ 回退到上一个版本(如果想回退到100个版本，使用git reset –hard HEAD~100 )
- cat XX         查看XX文件内容
- git reflog       查看历史记录的版本号id
- git checkout — XX  把XX文件在工作区的修改全部撤销。
- git rm XX          删除XX文件
- git remote add origin https://github.com/tugenhua0707/testgit 关联一个远程库
- git push –u(第一次要用-u 以后不需要) origin master 把当前master分支推送到远程库
- git clone https://github.com/tugenhua0707/testgit  从远程库中克隆
- git checkout –b dev  创建dev分支 并切换到dev分支上
- git branch  查看当前所有的分支
- git checkout master 切换回master分支
- git merge dev    在当前的分支上合并dev分支
- git branch –d dev 删除dev分支
- git branch name  创建分支
- git stash 把当前的工作隐藏起来 等以后恢复现场后继续工作
- git stash list 查看所有被隐藏的文件列表
- git stash apply 恢复被隐藏的文件，但是内容不删除
- git stash drop 删除文件
- git stash pop 恢复文件的同时 也删除文件
- git remote 查看远程库的信息
- git remote –v 查看远程库的详细信息
- git push origin master  Git会把master分支推送到远程库对应的远程分支上



