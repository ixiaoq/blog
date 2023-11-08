
# git 常用命令
> Workspace：工作区

>  Index / Stage：暂存区

>  Repository：仓库区（或本地仓库）

>  Remote：远程仓库（github）

### 初始化代码库

在当前目录新建一个 Git 代码库
```sh
git init
```

新建一个目录，将其初始化为 Git 代码库
```sh
git init [project-name]
```

下载一个项目和它的整个代码历史
```sh
git clone [url]
```

### 配置

显示当前的Git配置
```sh
git config --list
```
设置提交代码时的用户信息
```sh
git config [--global] user.name "[name]"
git config [--global] user.email "[email address]"
```

### git add（增加/删除文件）

添加指定文件到暂存区
```sh
git add [file1] [file2] ...
```
添加指定目录到暂存区，包括子目录
```sh
git add [dir]
```
添加当前目录的所有文件到暂存区
```sh
git add .
```
添加每个变化前，都会要求确认

对于同一个文件的多处变化，可以实现分次提交
```sh
git add -p
```
删除工作区文件，并且将这次删除放入暂存区
```sh
git rm [file1] [file2] ...
```
停止追踪指定文件，但该文件会保留在工作区
```sh
git rm --cached [file]
```
改名文件，并且将这个改名放入暂存区
```sh
git mv [file-original] [file-renamed]
```

### git commit（代码提交）

提交暂存区到仓库区
```sh
git commit -m [message]
```
提交暂存区的指定文件到仓库区
```sh
git commit [file1] [file2] ... -m [message]
```
提交工作区自上次commit之后的变化，直接到仓库区
```sh
git commit -a
```
跳过使用暂存区域
```sh
git commit -am [message]
```
提交时显示所有diff信息
```sh
git commit -v
```
使用一次新的commit，替代上一次提交

如果代码没有任何新变化，则用来改写上一次commit的提交信息
```sh
git commit --amend -m [message]
```
文件补充重做上一次commit
```sh
git commit --amend
```

### git remote（远程同步）

下载远程仓库的所有变动
```sh
git fetch [remote]
```
显示所有远程仓库
```sh
git remote -v
```
显示某个远程仓库的信息
```sh
git remote show [remote]
```
增加一个新的远程仓库，并命名
```sh
git remote add [shortname] [url]
```
取回远程仓库的变化，并与本地分支合并
```sh
git pull [remote] [branch]
```
上传本地指定分支到远程仓库
```sh
git push [remote] [branch]
```
强行推送当前分支到远程仓库，即使有冲突
```sh
git push [remote] --force
```
推送所有分支到远程仓库
```sh
git push [remote] --all

### branch（分支）

常设分支: master 和 develop

临时分支：功能（feature）、预发布（release）、修补bug（fixbug）

这三种分支都属于临时性需要，使用完以后，应该删除，使得代码库的常设分支始终只有Master和Develop。

列出所有本地分支
```sh
git branch
```
列出所有远程分支
```sh
git branch -r
```
列出所有本地分支和远程分支
```sh
git branch -a
```
新建一个分支，但依然停留在当前分支
```sh
git branch [branch-name]
```
新建一个分支，并切换到该分支
```sh
git checkout -b [branch]
```
新建一个分支，指向指定commit
```sh
git branch [branch] [commit]
```
新建一个分支，与指定的远程分支建立追踪关系
```sh
git branch --track [branch] [remote-branch]
```
切换到指定分支，并更新工作区
```sh
git checkout [branch-name]
```
切换到上一个分支
```sh
git checkout -
```
建立追踪关系，在现有分支与指定的远程分支之间
```sh
git branch --set-upstream [branch] [remote-branch]
```
合并指定分支到当前分支
```sh
git merge [branch]
```
删除分支
```sh
git branch -d [branch-name]
```
删除远程分支
```sh
git push origin --delete [branch]
```
显示当前分支的最近几次提交
```sh
git reflog
```
选择一个commit，合并进当前分支
```sh
git cherry-pick [commit]
```
分支重命名
```sh
git remote rename [old-name] [new-name]
```



### 回滚/撤销某次的提交

> --soft：撤销后保留修改  --hard：撤销后不保留修改

撤销某次操作（保留修改)
```sh
git reset --soft <commitid>
```
回滚指定文件
```sh
git reset HEAD file
```
回退到上一版（保留修改）
```sh
git reset HEAD^
```
回退到 10次提交之前（不保留修改）
```sh
git reset --hard HEAD~10
```
回退到commit id为3628164的版本（不保留修改）
```sh
git reset --hard 3628164
```
撤销某次操作（不保留修改)
```sh
git revert <commitid>
```
将本地的状态回退到和远程的一样 
```sh
git reset --hard origin/master
```

### git stash（暂存文件）

执行存储时，添加备注，方便查找。
```sh
git stash save "message"
```
查看当前stash中的内容
```sh
git stash list
```

将当前stash中的内容弹出，并应用到当前分支对应的工作目录上。

注：该命令将堆栈中最近保存的内容删除（栈是先进后出）
```sh
git stash pop
```
将堆栈中的内容应用到当前目录，不会将内容从堆栈中删除，适应于多个分支的情况
```sh
git stash apply
// 删除所有缓存的stash
```sh
git stash clear 
```

### git tag（标签）

列显已有的标签
```sh
git tag
```
列显指定标签详情
```sh
git show v1.4
```
新建标签
```sh
git tag -a [版本号]    -m [备注]
例：git tag -a v1.4 -m 'my version 1.4'
```
删除标签
```sh
git tag -d v1.4
```
推送 指定标签到服务器上
```sh
git push origin v1.5
```
推送 所有标签到服务器上
```sh
git push origin --tags
```
删除远程标签
```sh
git push origin :refs/tags/标签名
```
检出标签  到 分支
```sh
git checkout -b [branchname] [tagname]
git checkout -b version2 v2.0.0
```

### 查看信息

显示有变更的文件
```sh
git status
```
显示当前分支的版本历史
```sh
git log
```
显示commit历史，以及每次commit发生变更的文件
```sh
git log --stat
```
搜索提交历史，根据关键词
```sh
git log -S [keyword]
```
显示某个commit之后的所有变动，每个commit占据一行
```sh
git log [tag] HEAD --pretty=format:%s
```
显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
```sh
git log [tag] HEAD --grep feature
```
显示某个文件的版本历史，包括文件改名
```sh
git log --follow [file]
```sh
git whatchanged [file]
```
显示指定文件相关的每一次diff
```sh
git log -p [file]
```
显示过去5次提交
```sh
git log -5 --pretty --oneline
```
显示所有提交过的用户，按提交次数排序
```sh
git shortlog -sn
```
显示指定文件是什么人在什么时间修改过
```sh
git blame [file]
```
显示暂存区和工作区的差异
```sh
git diff
```
显示暂存区和上一个commit的差异
```sh
git diff --cached [file]
```
显示工作区与当前分支最新commit之间的差异
```sh
git diff HEAD
```
显示两次提交之间的差异
```sh
git diff [first-branch]...[second-branch]
```
显示今天你写了多少行代码
```sh
git diff --shortstat "@{0 day ago}"
```
显示某次提交的元数据和内容变化
```sh
git show [commit]
```
显示某次提交发生变化的文件
```sh
git show --name-only [commit]
```
显示某次提交时，某个文件的内容
```sh
git show [commit]:[filename]
```

