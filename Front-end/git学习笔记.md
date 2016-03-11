
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

要关联一个远程库，使用命令`git remote add origin git@github.com:zhaokang555/xxx.git`

关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容

- 我们第一次推送master分支时，加上了`-u`参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改

---

#从远程仓库克隆











