# Git使用

工作区->使用git add将修改的文件加入到暂存区->暂存区->使用git commit提交文件->仓库

## 1、初始化Git

**1.创建仓库的目录**

**2.右键下执行Git Bash Here**

$ git --help	查看帮助

$ git config --list	查看配置信息

**3.使用git命令设置用户名**

格式：$ git config --global(全局设置) user.name 用户名

$ git config --global user.name admin

**4.设置邮箱**

$ git config --global user.email 123456@qq.com

## 2、初始化仓库

**1.初始化仓库**

$ git init 

初始化后在仓库目录里会生成一个.git文件夹，除去.git目录外，全都为工作区，缓冲区和仓库都在.git目录里。

**2.创建文件**

$ touch.exe 1.tex

**3.查看git状态**

```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        1.tex

nothing added to commit but untracked files present (use "git add" to track)
```

on  branch master：当前的分支为主分支

**4.将文件加入到暂存区**

$ git add .

.代表整个目录

**5.再次查看git状态**

```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   1.tex
```

**6.提交文件到仓库**

```
$ git commit -m "1.tex"
[master (root-commit) 7f4af18] 1.tex
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 1.tex

$ git status
On branch master
nothing to commit, working tree clean
```

## 3、Git版本回退

**1.查看版本信息**

```
$ git log
commit cef49764b1916a76bfe7b9c2a3540abc1f93cfce (HEAD -> master)
Author: jason <1378616922@qq.com>
Date:   Thu Jan 7 06:38:20 2021 +0800

    3.txt

commit 01a3c5e7a702dc77fb895a33c146e47762ab6e60
Author: jason <1378616922@qq.com>
Date:   Thu Jan 7 06:37:46 2021 +0800

    2.txt

commit dc7fff9b16c501b3a1203be27016eaf9d964d1b2
Author: jason <1378616922@qq.com>
Date:   Thu Jan 7 06:36:50 2021 +0800

    1.txt
```

**2.以单行方式查看版本**

```
$ git log --pretty=oneline
cef49764b1916a76bfe7b9c2a3540abc1f93cfce (HEAD -> master) 3.txt
01a3c5e7a702dc77fb895a33c146e47762ab6e60 2.txt
dc7fff9b16c501b3a1203be27016eaf9d964d1b2 1.txt
```

cef49764b1916a76bfe7b9c2a3540abc1f93cfce：版本号

**3.版本回退**

```
$ git reset --hard HEAD
HEAD is now at cef4976 3.txt
```

HEAD：代表当前所在的版本

回退到上一个版本

```
$ git reset --hard HEAD~
HEAD is now at 01a3c5e 2.txt
```

回退到前多少个版本

```
$ git reset --hard HEAD~1
HEAD is now at dc7fff9 1.txt
```

回退到指定版本

```
$ git reset --hard cef4976
HEAD is now at cef4976 3.txt
```

## 3、Git删除

**1.删除工作区中的文件**

当工作区中新增了文件，没有被提交暂存区，直接删除即可。

```
$ rm -rf 4.txt
```

**2.删除暂存区中的文件**

当文件提交到暂存区后，需要先删除暂存区中的内容。

```
$ git rm --cached 4.txt
rm '4.txt'
```

**3.删除仓库中文件**

```
$ rm -rf 4.txt

$ git add .

$ git commit -m 'rm 4.txt'
[master 98f04fc] rm 4.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 4.txt
```

## 4、分支

1.查看分支

```
$ git branch
```

2.创建分支

```
$ git branch dev
```

3.切换分支

```
$ git checkout dev
Switched to branch 'dev'
```

4.合并分支

```
$ git merge dev master
Updating 98f04fc..cd6a434
Fast-forward
 dev.php | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 dev.php
```

# GitHub

### 1.下载仓库中的项目

git clone url 目录

```
$ git clone https://github.com/shenjason/ThinkPHP7.git ./
```

### 2.文件加入到暂存区

```
$ git add .
```

### 3.提交到本地仓库

```
$ git commit -m '说明信息'
```

### 4.推送到远程仓库

```
$ git push origin main
```

