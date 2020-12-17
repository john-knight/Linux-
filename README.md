# 文件访问与删除：

#### cd: 切换工作目录

#### rm: 删除内容，如果要删除文件需添加-r

#### touch: 添加一个文件

#### ..: 跳转到上一级文件路径

#### ./: 在当前文件路径下，点开某个文件

#### vi: 打开文件编译器，进入文件编译器后需要点 i 或其他指令才能开始编译，点 esc 可推出当前模式进入指令模式，点：后加 wq 保存后退出，q！强制退出

#### ll: 列出所有的文件目录以及创建时间，是否可以修改等详细的信息

#### ps -ef: 列出所有的线程

#### grep: 可用|grep ×××（想要查询的名称） 来筛选 示例：ps -ef | grep ds ,当然Grep更为关键的作用是使用正则表达式来搜索字符串

#### sudo: 是一种权限管理机制，管理员可以授权于一些普通用户去执行一些 root 执行的操作，而不需要知道 root 的密码

#### pwd: 当前文件路径

#### ifconfig: 查询 ip 地址等网络信息

#### ls: 列出所有的文件目录,ls -a:列出所有的文件目录，包括隐藏文件，ls -1:排列显示所有的文件目录

#### less: 这个指令很常用，less可以直接在控制台输出文本文件；进入less控制台后， / 可以直接搜索指定字符串，n可以向下搜索、N向上搜索；向上翻页：b，向下翻页Space（空格键）。

# 文件下载与解压

#### tar: 解压指令后可加-C 解压到指定的文件目录，示例：tar zxvf ×××（要解压的目的文件） -C（要大写） ×××（要解压到的地址）

#### wget: 是 linux 上的命令行的下载工具。这是一个 GPL 许可证下的自由软件。wget 支持 HTTP 和 FTP 协议，示例：

#### apt-get apt-get：Advanced Package Tool 是一条 linux 命令，适用于 deb 包管理式的操作系统，主要用于自动从互联网的软件仓库中搜索、安装、升级、卸载软件或操作系统。

# Linux 线程相关操作

#### ps -ef: 查看所有进程

#### ps -ef | grep: // 筛选特定进程

#### kill pid: 杀掉特定 id 的线程

#### netstat tunpl | grep: 端口号 查询指定占用端口号的线程（常用于检查端口号是否被占用），当然，lsof -i:8080,也可以快速的搜索出端口占用情况

# Linux 进程操作
#### top: 命令 ， top命令类似windows的任务管理器，可以查看当前系统内的所有进程，以及cpu、内存的占有率。

# vi操作（我们在一系列的具体使用过程中来学习vi）
#### touch: 文件名 来创建一个文本文件
#### vi: 文件名 进入文件
#### vi: 有三种模式，分别为命令模式、插入模式、底行模式
#### 1 首先进入的是命令模式，输入 i 可进入插入模式 ，输入esc可退出插入模式进入命令模式！ 在命令模式下。输入：则进入底行模式。
#### 2 底行模式，输入wq保存并退出，输入q！直接退出并不保存！
#### 3 校验是否保存，我们可以cat 文件名 快速查看一下文件内容！

# git操作(以下包含所有常见的git操作以及配置git操作)
####




# 一切较为实用的Shell脚本
####Search.sh. :
  #!/bin/sh
  basePath=/opt/apps/deposit-interfaces/logs
  if [ $# != 1 ]; then
     echo usage: $0 \{TRACE_ID\}
     exit 1
  fi

  cat ${basePath}/*.log | tr "\n" "\030" | sed 's/\o0302020-/\n2020-/g' | grep $1 | sort | tr "\030" "\n"



# 火焰图
### 火焰图使用arths,https://arthas.aliyun.com/doc/profiler.html
### 1. Java -jar /opt/arthas/arthas-boot.jar
### 2. 选择相应服务
### 3. profiler start
### 4. profiler stop --file /tmp/output.svg
### 5. 从堡垒机文件管理器下载
### 6. 浏览器打开svg文件
# Dump
### 1. jmap -dump:format=b,file=/tmp/abc.bin <pid>
### 2. 打包: tar zcvf abc.bin.tar.gz abc.bin
### 3. 分割文件: split -b 200m abc.bin.tar.gz abc.bin.tar.gz_
### 4. 从堡垒机文件管理器下载
### 5. 本地解压 cat abc.bin.tar.gz_* | tar xv
### 6. 使用mat或者jprofiler分析dump
