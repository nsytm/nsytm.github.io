---
layout: default
title: Docker 命令
parent: Container
nav_order: 0
---

# Docker 命令

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
   {:toc}

---

### 1、docker 命令

#### 1.1、帮助启动命令

#### 1.2、镜像命令

#### 1.3、容器命令

列出当前正在运行的容器：

```bash
docker ps
```

列出所有的容器，包括已经停止运行的容器：

```bash
docker ps -a
```

在运行中的Docker容器内启动一个交互式的终端界面：  
docker exec：在正在运行的容器中执行命令；   
-i：交互式操作；  
-t：终端；  
container_id：容器ID或名称；  
bash:交互式Shell。

```bash
docker exec -it <container_id> bash
```

容器与宿主机互相复制文件

```bash
docker cp <container_id>:<container_path> <local_path>
docker cp <local_path> <container_id>:<container_path>
```