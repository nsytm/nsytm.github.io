---
layout: default
title: DB语法
nav_order: 0
parent: Database
---

# DB语法

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
   {:toc}

---

#### 1、SQL语法

创建一张表的备份：

```sql
create table backup_table_name as select * from original_table_name;
```

删除表中所有数据：

```sql
truncate table_name;
```

将表A的所有数据插入到表B（表结构完全相同）：

```sql
insert into B select * from A;
```
