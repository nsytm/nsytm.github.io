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
install：把打好的包安装到本地仓库，以便其他项目可以引用  
package：只生成包，不安装到本地仓库
-pl：构建指定模块  
-am：构建指定模块的依赖模块

构建指定模块及其依赖模块

```bash
mvn clean install -pl module-1 -Dmaven.test.skip=true -am
```

构建指定模块

```bash
mvn clean install -pl module-1 -Dmaven.test.skip=true
```

对整个项目进行打包

```bash
mvn clean install -Dmaven.test.skip=true
```

tip：如果是多模块项目（父子结构）项目，请使用 ”构建指定模块及其依赖模块“ 命令或者在父工程使用 ”对整个项目进行打包“ 命令！