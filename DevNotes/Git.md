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


## 一、Git安装
windows安装：进入网站 https://git-scm.com/ 下载安装，然后在cmd命令行配置。
```
# 配置用户名和邮箱
git config --global user.name "FishC_Service"
git config --global user.email "fishc_service@126.com"

# 检查信息是否写入成功
git config --list 
```
## 二、Git操作
### 1、查看和修改用户名、邮箱
* git config 命令查看用户名、邮箱
```
git config user.name
git config user.email
```
* git config 命令修改用户名、邮箱
* 
```
# 仅对当前仓库有效
git config --local user.name "name"
git config --local user.email "email"

# 对当前用户的所有仓库有效
git config --global user.name "name"
git config --global user.email "email"
```
### 2、首次使用，克隆代码

1. 指定本地路径

   ```
   cd /e/daota
   ```

2. 克隆远程仓库代码到本地

   ```
   git clone <url>
   ```

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
