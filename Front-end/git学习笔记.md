#git学习笔记

git init  

---

git status  
git diff  

---

git log  
git log --pretty=oneline  
git log --oneline // 简写  
git reflog  

---

git reset --hard HEAD^  
git reset --hard HEAD^^  
...  
git reset --hard HEAD~13  
git reset --hard xxxxxx // 在版本之间穿梭

---

- 场景1: 当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。
- 场景2: 当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD file`，就回到了场景1，第二步按场景1操作。





