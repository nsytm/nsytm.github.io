---
layout: default
title: Linux
nav_order: 7
has_children: true
permalink: docs/Linux
---

# Linux 学习笔记

{: .no_toc }

CSS utility classes come in handy when you to want to override default styles to create additional whitespace (
margins/padding), correct unexpected shifts in font size or weight, add color, or hide (or show) something at a specific
screen size.
{: .fs-6 .fw-300 }

### 1.Linux 基本命令

#### 1.1 cd

**cd**（英文全拼：change directory）命令用于改变当前工作目录的命令，切换到指定的路径。

**切换到指定目录:** 如切换到 /usr/bin/目录

```cmd
cd [dirName]
cd /usr/bin
```

**切换到用户主目录（home）:** 使用 **~** 表示当前用户的主目录，也可以使用 cd 命令直接切换到主目录。

```cmd
cd
cd ~
```

**切换到上级目录:** 使用 **..** 表示上级目录，可以通过连续多次使用 **..** 来切换到更高级的目录。

```cmd
cd ..
cd ../../   // 切换到上上级目录
```

#### 1.2 ls

**ls**（英文全拼：list directory contents）命令用于显示指定工作目录下之内容（列出目前工作目录所含的文件及子目录)。

```cmd
ls [-alrtAFR] [文件名或目录名称...]
```

**选项与参数：**

- **-a** 显示所有文件及目录 (**.** 开头的隐藏文件也会列出)。
- **-d** 只列出目录（不递归列出目录内的文件）。
- **-l** 以长格式显示文件和目录信息，包括权限、所有者、大小、创建时间等。
- -h 将文件容量以人类较易读（例如 GB、KB 等等）的方式列出来。
- -r 倒序显示文件和目录。
- -t 将按照修改时间排序，最新的文件在最前面。
- -A 同 -a ，但不列出 "." (目前目录) 及 ".." (父目录)。
- -F 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/"
- -R 递归显示目录中的所有文件和子目录。

**示例：**

```cmd
ls -l			        // 等同于 ll
ls -al			        // 将当前目录下的所有文件列出来（含属性与隐藏文件）
ls -al /applog/dcos/    // 将 dcos 目录下的所有文件列出来（含属性与隐藏文件）
```

#### 1.3 cat

**cat**（英文全拼：concatenate）命令用于直接查询一个文件的内容（文件内容一次性全部显示到屏幕上）。

```cmd
cat [-AbeEnstTuv] [--help] [--version] fileName
```

**选项与参数：**

- **-n 或 --number:** 由 1 开始对所有输出的行数编号。
- -b 或 --number-nonblank: 和 -n 相似，只不过对于空白行不编号。
- -s 或 --squeeze-blank: 当遇到有连续两行以上的空白行，就代换为一行的空白行。
- -v 或 --show-nonprinting: 使用 ^ 和 M- 符号，除了 LFD 和 TAB 之外。
- -E 或 --show-ends: 在每行结束处显示 $。
- -T 或 --show-tabs: 将 TAB 字符显示为 ^I。
- -A, --show-all: 等价于 -vET。
- -e: 等价于"-vE"选项。
- -t: 等价于"-vT"选项。

**示例：**

```cmd
cat -n 2023-07-03.log
```

#### 1.4 more

more 命令类似 cat ，不过会以一页一页的形式显示，更方便使用者逐页阅读。

**说明：**

- 空格键+(space)：代表向下翻一页；
- Enter：代表向下翻一行；
- /字符串：代表在这个显示的内容当中，向下搜寻『字符串』这个关键词；
- q：代表立刻离开 more，不再显示该文件内容；
- b：代表往回翻页，不过这动作只对文件有用，对管线无用。

**示例：**

```cmd
more 2023-07-03.log
```

#### 1.5 less

less 与 more 类似，less 可以随意浏览文件，支持翻页和搜索，支持向上翻页和向下翻页。

**说明：**

- 空格键或者 [pagedown]：向下翻动一页；
- [pageup]：向上翻动一页；
- /字符串：向下搜寻 [字符串]；
- ?字符串：向上搜寻 [字符串]；
- n：重复前一个搜寻。

**示例：**

```cmd
less 2023-07-03.log
```

#### 1.6 tail

**tail** 命令可用于查看文件的内容，有一个常用的参数 **-f** 常用于查阅正在改变的日志文件。

```cmd
tail -f filename	// 把文件里的最尾部的内容显示在屏幕上，并且不断刷新，只要更新就可以看到最新的文件内容。
```

**选项与参数：**

- -f 循环读取

**示例：**

```cmd
tail -500 log.log	// 查看log文件的最后500行
tail -500f log.log	// 实时刷新最后500行
```

#### 1.7 df

**df**（英文全拼：disk free） 命令用于列出文件系统的整体磁盘使用量。

```cmd
df [-ahikHTm] [目录或文件名]
```

**选项与参数：**

- -h : 以人们较易阅读的 GBytes、MBytes、KBytes 等格式自行形式；
- -i : 不同磁盘容量，而以 inode 的数量来显示。

**示例：**

```cmd
df			// 将系统内所有的 filesystem 列出来！
df -h		// 将容量结果以易读的容量格式显示出来
df -h /etc	// 将 /etc 底下的可用的磁盘容量以易读的容量格式显示
```

#### 1.3 mkdir

#### 1.3 rmdir

#### 1.3 cp

#### 1.3 rm

#### 1.3 mv

#### 1.3 rm

#### 1.3 rm

#### 1.3 rm





















