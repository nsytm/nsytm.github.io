---
layout: default
title: Maven
parent: DevNotes
nav_order: 0
---

# Maven

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
   {:toc}

---

### 1、Maven命令

#### 1.1、打包命令

参数说明：  
clean：删除target目录  
install：把打好的包发布至本地仓库，以备本地的其它项目作为依赖使用  
-pl：构建指定模块  
-am：构建指定模块的依赖模块

构建指定模块及其依赖模块

```bash
mvn clean install -pl module-1 -Dmaven.test.skip=true -am
```

构建指定模块（踩坑，module-1如果引用了其它的公共模块common，，那么在执行此命令打包的时候，common模块后续提交的代码都不会打在jar包里面）

```bash
mvn clean install -pl module-1 -Dmaven.test.skip=true
```