---
layout: default
title: Linux 命令
nav_order: 0
has_children: true
permalink: docs/Linux
---

# Linux 命令

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
   {:toc}

---

#### 1、文件与目录命令

列出目录：  
-a：全部的文件，包含隐藏的文件  
-l：长数据串列出，包含文件的属性与权限等

```bash
ls -al logs/
```

创建文件：

 ```bash
 touch /logs/20231201/202312011547.log
 ```

创建目录：  
-m：设置目录权限  
-p：递归创建目录

```bash
mkdir -m 755 -p /logs/20231201
```

设置文件或目录的权限：  
-R：递归修改权限

```bash
chmod -R 765 /logs/20231201
```

删除文件或目录：  
-r：递归删除  
-i：提示是否删除  
-f：强制删除

```bash
rm -ri /logs/20231201/
```

> Tip：文件或目录设置权限

drwxr-xr-x 表示一个目录，其中：

* d：表示目录
* rwx：表示所有者（owner）有读、写、执行权限
* r-x：表示组用户（group）有读和执行权限
* r-x：表示其他用户（others）有读和执行权限

rwxr 是文件或目录权限的一部分，每个字符表示一种权限。这些字符的全称为：

* r：Read（读取），权限数字为 4
* w：Write（写入），权限数字为 2
* x：Execute（执行），权限数字为 1

#### 2、磁盘命令