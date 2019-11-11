---
title: github fork别人仓库后源码同步
date: 2019-11-10 10:44:13
tags:
---

**1**在本地计算机建立一个文件夹

在文件夹内点击鼠标右键启动Git Bash Here输入命令

	git clone git@github.com:goochen/magnetW.git

将github的项目下载到本地
![](https://i.imgur.com/BAqbayJ.png)
项目地址改成你自己的
输入命令

	cd magnetW

进入magnetW文件夹
![](https://i.imgur.com/rTY52Rt.png)

*2*.使用 **git remote -v** 查看当前的远程仓库地址，输出如下：
![](https://i.imgur.com/XtzhduQ.png)

	origin  https://github.com/goochen/magnetW.git (fetch)
	origin  https://github.com/goochen/magnetW.git (push)

可以看到从自己帐号 clone 下来的仓库，远程仓库地址是与自己的远程仓库绑定的
接下来运行进行添加别名 upstream（上游） 的地址，也就是指向我之前 Fork 的原仓库地址
![](https://i.imgur.com/UAsUSoW.png)

*3*.git remote add upstream https://github.com/dengyuhan/magnetW.git
![](https://i.imgur.com/K1zuEqt.png)

再次使用 git remote -v 输出如下：
![](https://i.imgur.com/CTGQ7sn.png)

	origin  https://github.com/goochen/magnetW.git (fetch)
	origin  https://github.com/goochen/magnetW.git (push)
	upstream        https://github.com/dengyuhan/magnetW.git (fetch)
	upstream        https://github.com/dengyuhan/magnetW.git (push)

可以看到了我们项目以及 upstream 上游项目
之后运行下面几条命令，就可以保持本地仓库和上游仓库同步了

*4*.将上游仓库的 master 分支下载到本地当前 branch 中

**git fetch upstream**
![](https://i.imgur.com/exj8Zdv.png)

进行合并

**git merge upstream/master**
![](https://i.imgur.com/dvkixqX.png)


进行推送提交

**git push origin master**
![](https://i.imgur.com/Uao8O2A.png)