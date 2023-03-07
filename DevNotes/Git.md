---
layout: default
title: Git
parent: DevNotes
nav_order: 1
---

# Git
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 1.Git安装与配置

windows安装：进入网站 https://git-scm.com/ 下载安装，然后在cmd命令行配置。

### 1.1 配置用户名和邮箱

```
# 仅对当前仓库有效
git config --local user.name "pgl"
git config --local user.email "501143xxx@qq.com"

# 对当前用户的所有仓库有效
git config --global user.name "pgl"
git config --global user.email "501143xxx@qq.com"
```

### 1.2 查看配置信息

```
# 检查信息是否写入成功
git config --list 

# 查看用户名、邮箱
git config user.name
git config user.email
```

## 2.第一次使用git克隆项目到本地

#### 2.1 右键点击git bash here, 进入git命令窗口, 指定本地路径, 使用一个空的文件夹来存放项目代码

```
cd /e/daota
```

#### 2.2 克隆远程仓库代码到本地

```
# 默认情况下, 根据url最后一个 / 之后的项目名称, 创建本地项目目录 
git clone <url>

# 指定项目名称为本地项目目录
git clone <url> projectname

# 拉取指定分支的代码, -b:表示选择分支
git clone -b <branchname> <url>
```

#### 2.2 克隆代码报错

```
# 报错一
fatal: unable to access 'https://github.com/nsytm/remote.repository.name.git/': SSL certificate problem: unable to get local issuer certificate

# 解决方法, 取消 git 对 SSL 的检验
git config --global http.sslVerify "false"

# 报错二

```

### 3.第一次使用git提交代码

#### 3.1 创建并进入目录

```
# 创建目录, -p:表示递归创建
mkdir -p /e/github/test
```

#### 3.2 创建本地仓库, 添加远程仓库

##### 3.2.1 方式一

```
# 初始化当前目录为本地仓库, 生成.git配置文件 (可以使用 ls -ah 命令查看.git文件)
git init

# 添加远程仓库, shortname:远程仓库别名, 一般使用origin来代替url, url:远程仓库地址
git remote add <shortname> <url>
```

##### 3.2.2 方式二

```
# 默认会拉取远程仓库中的所有内容
git clone xxx

# git clone是一个复合命令, 相当于连续执行了下面三个命令
git remote add origin https://github.com/nsytm/remote.repository.name.git
git fetch
git checkout master
```

#### 3.3 git add 命令可将文件添加到暂存区

```
# 添加一个或多个文件到暂存区
git add [file1] [file2] ...
git add qq.txt weixin.txt

# 添加指定目录到暂存区, 包括子目录
git add [dir]
git add /e/github/he

# 添加当前目录下的所有文件到暂存区
git add .
```

#### 3.4 git commit 命令将暂存区内容添加到本地仓库中

注意: 执行 commit 提交代码前, 要先拉取最新的代码, 使用 git fetch 或 git pull 命令

```
# 提交暂存区所有文件到本地仓库中, message:表示备注信息
git commit -m [message]

# 提交暂存区的指定文件到仓库区
git commit [file1] [file2] ... -m [message]

-a:表示修改或删除文件后不需要执行 git add 命令, 可以直接执行 commit, 但是新文件还是要 add
git commit -a
```

#### 3.4 git push 命令用于从将本地的分支版本上传到远程并合并

```
# 提交代码到远程仓库
git push <远程主机名> <本地分支名>:<远程分支名>

# 如果本地分支名与远程分支名相同，则可以省略冒号
git push <远程主机名> <本地分支名>
```

## update pgl 2023/03/07

### 分支命令

* 查看分支

```
# 查看本地分支
git branch

# 查看远程分支
git branch -r

# 本地 + 远程
git branch -a

# 查看本地分支对应的远程分支
git branch -vv
```

* 修改分支名称

```
# 将 oldname 修改为 newname
git branch -m oldname newname

# 将本地分支,提交到远程仓库
git push origin newname

# 删除 oldname 分支
git push origin -d oldname
```

* 新建分支

```
# 新建dev分支，并切换。仅切换，则去掉参数 -b
git checkout -b dev

# 新建dev分支
git branch dev

# 将本地分支,提交到远程仓库
git push origin dev
```

* 删除分支

```
# 删除本地dev分支
git branch -d dev

# 删除远程dev分支
git push origin --delete dev
```
