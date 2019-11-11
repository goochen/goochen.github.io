---
title: liunx常用命令
date: 2019-11-10 15:26:16
tags:
---
**liunx服务器时间修改**

	date -R
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
**文件/文件夹 操作**

**mkdir 新建 文件夹**

在当前文件夹新建一个 bash 文件夹，完整的绝对路径就是 /root/bash

    mkdir bash
     
    更多的命令可以用 mkdir --help 查看。

**cd 进入 文件夹**

你当前在 /root目录中，使用这个命令会进入 /root/bash目录，这是相对路径

    cd bash

如果你不在 /root目录中的话，就不能用上面的相对路径了，就需要绝对路径
    cd /root/bash

假设你当前在 /root/bash目录中，使用相对路径，你可以用这个命令进入上一级 /root目录， .. 代表相对路径 上级目录

    cd ..
当然你也可以用绝对路径来进入上一级 /root目录

    cd /root

**cp 复制或重命名 文件/文件夹**

复制当前目录内的 log.txt文件到 /var目录

    cp log.txt /var/log.txt

复制当前目录内的 bash文件夹到 /home目录

    cp -R bash /home/bash

复制当前目录内的所有.txt后缀的文件到 /var/log目录

    cp *.txt /var/log

复制当前目录内的所有以 doubi开头的文件到 /var/log目录

    cp doubi* /var/log

复制当前目录内的所有以 doubi开头 以.txt后缀结尾的文件到 /var/log目录
    cp doubi*.txt /var/log

假设当前目录是 /root/doubi/log，要把这个目录中的所有.txt后缀的文件复制到上一级目录 /root/doubi，那么这样做

    cp *.txt ..

就是相对路径，代表上一级目录，当然你也可以用绝对路径，这样更不容易出错

    cp *.txt /root/doubi

    重命名当前目录内的 log.txt文件为 log2.txt
    cp log.txt log2.txt

	复制当前目录内的 log.txt文件到 /var目录并重命名为 log1.txt
    cp log.txt /var/log1.txt

	复制当前目录内的 bash文件夹到 /home目录并重命名为 bash2
    cp -R bash /home/bash2

	复制当前目录内的 log.txt文件到 /var目录，但是 /var 目录中已经存着 log.txt，那么会提示 cp: overwrite `/var/log.txt'? 可以用 -f 强制覆盖

    cp -f log /var/log.txt

大家可能会发现，当你使用 cp -f 强制覆盖的时候，依然会询问你是否覆盖，这是因为 CP 为了避免你手误，默认加上了 -i 参数（该参数代表每次覆盖必须询问）。
所以想要避免 CP 默认的 -i 参数，只需要在 CP 命令前面加上斜杠即可 “/”

    /cp -f log /var/log.txt
     
复制当前目录内的 log.txt log1.txt log2.txt文件和 log233目录到 /home/log目录中

    cp -R log.txt log1.txt log2.txt log233 /home/log
     
    更多的命令可以用 cp --help 查看

**mv 移动或重命名 文件/文件夹**

关于 mv 命令，可以参考上面 cp 的使用方法，没什么区别，只是一个是复制，一个是移动，把上面 cp 命令改成 mv 就能套用了。

移动当前目录内的 log.txt文件到 /var目录

    mv log.txt /var/log.txt

移动当前目录内的 bash文件夹到 /home目录

    mv bash /home/bash

重命名当前目录内的 log.txt文件为 log2.txt

    mv log.txt log2.txt

复制当前目录内的 log.txt文件到 /var目录并重命名为 log1.txt

mv log.txt /var/log1.txt

复制当前目录内的 bash文件夹到 /home目录并重命名为 bash2

    mv bash /home/bash2

	更多的命令可以用 mv --help 查看。

**rm 删除 文件/文件夹**

删除当前目录下的 log.txt文件

    rm log.txt

删除当前目录下所有.txt后缀的文件

    rm *.txt

使用 rm 命令删除时，会提示你是否确定删除，输入 y 即删除，输入 n 则取消

rm: remove regular file `log.txt'? y

删除当前目录下所有.txt后缀的文件

    rm *.txt

删除当前目录下所有以 doubi开头的文件

    rm doubi*

删除当前目录下所有以 doubi开头 以.txt后缀结尾的文件

    rm doubi*.txt

当你用 rm 删除目录的时候会发现提示这不是一个文件

    rm bash
    rm: cannot remove `bash': Is a directory
    可以加上 -r 来归递删除目录及其目录下的内容
    rm -r bash
因为为了避免手误删除错误，所以 rm默认是加上了 -i 的参数，也就是每一次删除文件/目录都会提示，如果觉得烦可以用 -rf 参数

    rm -rf bash

rm -rf 这个命令请慎重使用，而且千万不要使用 rm -rf / 或者 rm -rf /* 之类的命令(系统自杀)，可能会让你系统爆炸，所以使用请慎重！

	更多的命令可以用 rm --help 查看。

**VI 编辑文件内容**

VI 介绍

VI 是Linux很棒的一个文本编辑器，不过也存在一些缺点，比如操作麻烦。而 vim就相当于 VI 的加强版，主要介绍 VIM。

VIM 介绍

打开当前目录下的 log.txt文件，如果没有那么会新建 log.txt文件（安装vim后，使用 vi和 vim打开文件没区别）

    vi log.txt

    vim log.txt

在命令行模式下，直接输入以下 符号和字母(区分大小写)
    进入编辑模式（插入模式，按 Esc键 即可返回命令行模式）

    i
	删除光标当前所在的一行
    dd
    删除文件内所有内容
    dddG
    复制光标当前所在的一行
    yy
    粘贴刚才复制的一行内容
    p
    撤销上个操作（误操作可以用这个恢复）
    u
    保存当前文件（ : 是英文的冒号）
    :w
    另存当前文件内容为 log2.txt
    :w log2.txt
    退出当前文件
    :q
    不保存 并强制退出当前文件
    :q!
    保存并退出当前文件
    :wq
    更多的命令可以用 vi --help / vim --help 来查看。

**netstat 查看链接和端口监听等信息**

参数介绍：

	-n ：不显示别名（主机名/域名以 数字或IP显示）

    -e ：显示其他/更多信息

    -p ：显示进程PID/进程名

    -c ：持续输出（设置后会每隔 1秒输出一次，Ctrl+C 终止）

    -l ：显示正在监听的套接字

    -a ：显示全部信息

下面这些就不很常用了。

    -r ：显示路由表

    -i ：显示网络接口（网卡）

    -g ：显示多播组信息

    -s ：显示网络统计

    -M ：显示伪装连接

    -v ：显示正在进行的工作

	更多的命令可以用 netstat --help 来查看。

使用示例：

    显示当前服务器的所有连接信息
    netstat -a
     
    显示当前服务器的所有 TCP连接信息
    netstat -at
     
    显示当前服务器的所有 UDP连接信息
    netstat -au
     
    显示当前服务器的所有 端口监听信息
    netstat -lnp
     
    显示当前服务器的所有 TDP端口监听信息
    netstat -lntp

一般来说经常使用这个命令：

    显示当前服务器的所有正在监听 TCP端口的信息，并且 显示进程PID和进程名，但不显示别名（域名以IP显示），这个命令算是最常用的了。
    netstat -lntp
     
    输出示例
    Active Internet connections (only servers)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      14233/nginx.conf
    tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1555/sshd       
    tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      14233/nginx.conf
    tcp6       0      0 :::22                   :::*                    LISTEN      1555/sshd
    —————————————————————————————————————
    显示监听 80端口的进程PID和进程名，grep是匹配并显示 符合关键词的行。
    netstat -lntp|grep ":80"
     
    输出示例
    Active Internet connections (only servers)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      14233/nginx.conf
    —————————————————————————————————————
    显示 ssh的监听情况，grep是匹配并显示 符合关键词的行。
    netstat -lntp|grep "ssh"
     
    输出示例
    Active Internet connections (only servers)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1555/sshd

表头解释：

    Proto ：连接协议（tcp/udp是IPv4，tcp6/udp6是IPv6）
    Recv-Q ： 接收队列（基本都是0，如果不是代表堆积）
    Send-Q ：发送队列（基本都是0，如果不是代表堆积）
    Local Address ：本地地址和端口
    Foreign Address ：对外地址和端口
    State ：连接状态
    PID/Program name ：进程PID/进程名

    每隔 1秒显示一次当前服务器的所有连接信息
    netstat -c
     
    每隔 1秒显示一次当前服务器的所有 TCP连接信息
    netstat -ct
     
    每隔 1秒显示一次当前服务器的所有 UDP连接信息
    netstat -cu
     
    显示当前服务器的路由表
    netstat -r
     
    显示当前服务器的网络接口信息（网卡）
    netstat -i
     
    显示当前服务器的网络统计信息
    netstat -s
     
    更多的命令可以用 netstat --help 来查看。

在使用 netstat命令中，会显示一些连接状态，下面是各状态的意思：

    LISTEN
    监听来自远程连接的 TCP端口连接请求
     
    SYN-SENT
    发送连接请求后，等待匹配的连接请求
     
    SYN-RECEIVED
    在收到和发送一个连接请求后，等待对方对连接请求的确认
     
    ESTABLISHED
    代表一个打开的连接
     
    FIN-WAIT-1
    等待远程 TCP连接中断请求，或先前的连接中断请求的确认
     
    FIN-WAIT-2
    从远程 TCP等待连接中断请求 
     
    CLOSE-WAIT
    等待从本地用户发来的连接中断请求 
     
    CLOSING
    等待远程TCP对连接中断的确认 
     
    LAST-ACK
    等待原来的发向远程TCP的连接中断请求的确认 
     
    TIME-WAIT
    等待足够的时间，以确保远程TCP接收到连接中断请求的确认 
     
    CLOSED
    没有任何连接状态（或者关闭了连接）

**ps 查看进程信息**

参数介绍：

    待写...
     
    # 更多的命令可以用 man ps 来查看。

使用示例：

    显示当前进程信息
    ps -ef
     
    显示 ssh 进程（ grep -v grep 表示排除关键词grep，因为使用 grep匹配ssh，也会把grep自己的进程匹配进去的）
    ps -ef|grep -v grep|grep 'ssh'

    输出示例

    UID        PID  PPID  C STIME TTY          TIME CMD #注意使用上面命令的话是不会显示表头这一行的，我只是为了更好理解加上的
    root      1738     1  0 01/27   ?       00:08:56 /usr/sbin/sshd
     
    # 待写...

表头解释：

    UID ：启动进程的用户
    PID ：进程标识符（进程 1代表init 是整个系统的父进程）
    PPID ：父进程标识符（进程 1代表init 是整个系统的父进程）
    C ：CPU占用率 %
    STIME ：启动进程的日期
    TTY ：终端号
    TIME ：进程运行时间（非休眠状态）
    CMD ：启动进程的命令（或进程名/进程程序所在目录）

**kill 结束进程**

    当我们想要结束一个进程的时候，我们可以用 kill 命令
    PID是每个进程的一个唯一标识符，可以使用上面的 ps 命令来查看你要结束进程的PID。
     
    假设我们要结束 Nginx的进程，那么这样做（ grep -v grep 表示排除关键词grep，因为使用 grep匹配ssh，也会把grep自己的进程匹配进去的）：
    ps -ef|grep -v grep|grep "nginx"
     
    输出示例
    UID PID PPID C STIME TTY TIME CMD #注意使用上面命令的话是不会显示表头这一行的，我只是为了更好理解加上的
    root 2356 1 0 04/03 ? 00:03:12 nginx
     
    然后我们可以看到第二列的 PID 进程标识符，然后我们 kill 即可。
    kill -9 2356
     
    中断进程 -2 相当于 程序运行在前台，然后输入 Ctrl+C 的效果，但是进程有权利忽略，所以不一定能结束进程
    kill -2 PID
    强制结束进程 -9 ，注意：强制结束某个进程后，可能会造成进程数据丢失等问题！
    kill -9 PID
	
**apt-get Debian/Ubuntu系统包管理器**

apt-get 是Debian/Ubuntu系统中 一个用于快速下载/安装的简单命令行管理工具！

点击展开 查看 apt-get命令说明

参数介绍：

    命令:
    update - 检索 新的包列表

    upgrade - 升级 可更新的所有软件包

    install - 安装 新软件包（pkg是libc6不是libc6.deb）

    remove - 删除 软件包

    autoremove - 自动删除 所有未使用的软件包

    purge - 删除 软件包和配置文件

    clean - 清除 已下载的归档文件

    autoclean - 清除 旧的下载的档案文件

    check - 验证 是否有损坏的依赖

    download - 下载 二进制包到当前目录
     
    选项：
    -q ：不输出任何信息

    -qq ：除了错误之外，没有输出

    -d ：仅下载，不要安装或解压缩存档

    -y ：对所有确定询问都选择 Yes，并且不提示

    -f ：尝试纠正 被破坏依赖关系的系统

    -m ：如果存档是可定位的，则尝试继续

    -u ：显示升级包的列表

    -b ：在获取源代码包后构建源包
     
    更多的命令可以用 apt-get --help 查看。

使用示例：

    检索 新的包列表
    apt-get update
     
    升级 可更新的所有软件包（注意这个命令会升级所有的软件包，所以会升级很长时间）
    apt-get upgrade
     
    安装 Nginx 软件包
    apt-get install nginx
     
    卸载 Nginx 软件包
    apt-get remove nginx
     
    卸载 Nginx 软件包 并删除所有相关配置文件
    apt-get remove --purge nginx
     
    在安装软件和卸载的时候，为了避免误操作，都会询问是否继续，每次都要输入 y 来确定会很麻烦，可以加上 -y 参数

    安装 Nginx 软件包 并不显示确定提示
    apt-get install nginx -y
     
    卸载 Nginx 软件包，删除所有相关配置文件 并不显示提示
    apt-get remove --purge nginx -y
     
    清除 旧的/无用 的软件包
    apt-get clean && apt-get autoclean
     
    下载 Nginx 二进制软件包到当前目录，但不解压和安装
    apt-get download nginx -d
     
    更多的命令可以用 apt-get --help 查看。

**yum CentOS系统包管理器**

yum 是CentOS系统中 一个用于快速下载/安装的简单命令行管理工具！

点击展开 查看 yum命令说明

参数介绍：

    命令：
    update - 检索 新的包列表

    upgrade - 升级 软件包

    search - 搜索 软件包

    install - 安装 软件包

    list - 列出 软件包或者软件包组

    info - 显示软件包或者软件包组的详细信息

    erase - 删除 软件包（这两个命令一样）

    remove - 删除 软件包（这两个命令一样）

    groupinfo - 显示 有关包组的详细信息

    groupinstall - 安装 软件包组（就像一种软件合集）

    grouplist - 列出 可用的软件包组

    groupremove - 删除 软件包组

    check - 检查 软件包

    check-update - 检查 可更新的软件包

    clean - 清除 缓存目录内的软件包

    deplist - 列出 一个包的依赖关系

    distribution-synchronization - 同步 已安装的软件包到最新的版本
    downgrad - 降级 一个软件包

    reinstall - 重新安装 软件包（自动删除重装）

    repolist - 显示 配置的软件包仓库

    resolvedep - 确定 软件包需要的依赖关系
     
    选项：

    -t ：容忍错误

    -C ：完全从系统缓存运行，不要更新缓存

    -R 分钟 ：最大命令等待时间

    -q ：安静的操作

    -y ：对于所有问题回答是

    --nogpgcheck ：禁用gpg签名检查
     
    更多的命令可以用 yum --help 查看。
    
	检索 新的包列表
    yum update
     
    安装 Nginx 软件包
    yum install nginx
     
    安装 Development Tools 软件包组（这个软件包组中包含了编译所需的软件）

    注意：当软件包或者软件包组的名字中包含空格的时候，请把 软件包或软件包组 加上双引号！
    yum groupinstall "Development Tools"
     
    卸载 Nginx 软件包
    yum erase nginx / yum remove nginx
     
    卸载 Development Tools 软件包组
    yum groupremove "Development Tools"
     
    升级 所有可更新的软件包
    yum upgrade
     
    升级 Nginx 可更新的软件包
    yum upgrade nginx
     
    在安装软件和卸载的时候，为了避免误操作，都会询问是否继续，每次都要输入 y 来确定会很麻烦，可以加上 -y 参数

    安装 Nginx 软件包 并不显示确定提示
    yum install nginx -y
     
    卸载 Nginx 软件包 并不显示确定提示
    yum erase nginx -y / yum remove nginx -y
     
    搜索 Nginx 软件包是否存着
    yum search nginx
     
    列出 可用的软件包
    yum list
     
    列出 可用的软件包组
    yum grouplist
     
    清除 缓存目录中的所有软件包
    yum clean
     
    清除 缓存目录中的 Nginx 软件包
    yum clean nginx
     
    重装 Nginx 软件包
    yum reinstall nginx
     
    更多的命令可以用 yum --help 查看。
