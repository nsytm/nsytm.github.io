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

docker帮助文档：

```bash
docker --help
```

查看docker服务状态：  
Active: active (running) 即表示服务为正在运行状态。

```bash
systemctl status docker
``` 

启动docker服务：

```bash
systemctl start docker
```

停止docker服务：

```bash
systemctl stop docker
```

重启docker服务：

```bash
systemctl restart docker
```

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
bash：交互式Shell。

```bash
docker exec -it <container_id> bash
```

容器与宿主机互相复制文件：

```bash
docker cp <container_id>:<container_path> <local_path>
docker cp <local_path> <container_id>:<container_path>
```

查看容器的端口映射情况：  
80/tcp -> 0.0.0.0:32768，表示容器内的 80 端口映射到了主机的 32768 端口上。

```bash
docker port 容器ID/名称
```

查看容器内运行的所有进程：

```bash
docker top 容器ID/名称
```

查看容器的日志：

```bash
docker logs 容器ID/名称
```