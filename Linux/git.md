git 操作

1. 撤销本地的commit

 ```
    git reset HEAD^·
 ```


2. git pull 之后查看修改部分 `git diff HEAD^`

 git diff HEAD 显示工作目录与git仓库之间的差异，而git diff HEAD^ 则显示上一次提交之前工作目录与git仓库之间的差异。所以我们在git pull后，可以通过git diff HEAD^ 来查看拉下来的文件有那些具体的修改。

 3. 从远程某个分支拉取代码到本地
   
   `git checkout -b 本地分支名 origin/远程分支名`
