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


### 1.Git安装与配置

windows安装：进入网站 https://git-scm.com/ 下载安装，然后在cmd命令行配置。

#### 1.1 配置用户名和邮箱

```
# 仅对当前仓库有效
git config --local user.name "pgl"
git config --local user.email "501143xxx@qq.com"

# 对当前用户的所有仓库有效
git config --global user.name "pgl"
git config --global user.email "501143xxx@qq.com"
```

#### 1.2 查看配置信息

```
# 检查信息是否写入成功
git config --list 

# 查看用户名、邮箱
git config user.name
git config user.email
```

### 2.第一次使用git克隆项目到本地

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

# 拉取指定分支的代码 -b:表示选择分支
git clone -b <branchname> <url>
```

### update pgl 2022/3/1

3. 克隆代码失败

   ```
   fatal: unable to access 'https://github.com/nsytm/nsytm.github.io.git/': SSL certificate
    problem: unable to get local issuer certificate
   
   # 解决方法，取消 git 对 SSL 的检验
   git config --global http.sslVerify "false"
   ```

4.

### 3、分支操作命令

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
