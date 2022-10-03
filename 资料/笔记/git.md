<h3>git

集中式，都在一台服务器，优点每个人都能看到项目其他人在干什么，缺点：不能出故障。

分布式版本控制：客户端会把仓库完整地镜像下来，包括完整地历史记录；

这样一来，任何一处协同工作用的服务器故障，事后都可以用任何一个镜像出来的本地仓库恢复

因为每一次的克隆操作，实际上都是一次对代码仓库的完整备份。

git bash 是一个shell ，是Windows下的命令行工具，可以执行linux命令

git bash 基于cmd，在cmd的基础上添加一些新的命令和功能



操作系统多用户

<h4>远程仓库的验证

使用 --global选项,name该命令只需要运行一次,因为在之后无论以做什么,git都会使用这些信息

**配置用户名**

git config --global user.name ""

git config --global user.email ""

**检测当前的配置信息**

git config --list

**配置别名 alias.**

git config --global alias.co checkout

<h4>获取git仓库

先创建本地仓库

git init

需要将本地资料添加到暂存区,管理资料

git add .

提交到本地仓库资料

git commit -m ""

git log查看本地日志



克隆远程地址

git clone

<h5>文件状态

​    stated 暂存区稳健状态

unmodified commit命令 可以将staged中文件提交到git仓库

modified，修改某个文件，会处于modified状态

![1663838385607](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663838385607.png)

![1663838424135](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663838424135.png)

git status 显示文件夹状态

红色说明没有跟踪，绿色已经跟踪，可以提交到本地仓库

![1663839278924](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663839278924.png)

![1663839596080](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663839596080.png)

![1663839639330](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663839639330.png)

<h4>git忽略文件

先创建.gitignore

github有开源的gitignore的模板

一般脚手架默认自动配置

![1663854385201](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663854385201.png)

![1663854531204](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663854531204.png)

git log 查看本地版本

git reset  回退版本

HEAD 指向最后一次提交

git --reset hard^

![1663854700288](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663854700288.png)

git reflog 会把之前回退的过程也记录下来

<h4>远程仓库

搭建自己的git仓库,放在自己的服务器上

gitlab注册账号,就用自己的服务器用gitlab软件操控

gitee

**克隆**

身份验证

https 需要登录账号

ssh 需要配置.ssh 秘钥

**验证**

![1663856534584](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663856534584.png)

**ssh**

生成公钥和私钥

**ssh-keygen -t ed25519 -C "your email"**

**ssh-keygen -t rsa -b 2048 -C "you email"**

**当rsa不被允许使用时ssh-keygen -t ecdsa -b 521 -C “your_email@example.com”**

两种加密方式

![1663857400036](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663857400036.png)

**本地仓库和远程仓库建立连接**

查看远程仓库的地址和分支

git remote -v

添加远程仓库

**git remote add pb url     pb可以代替整个字符串**

git pull相当于 get fetch和 git merge

git fetch 只是下载到仓库，merge才会合并到文件显示

git pull origin master 拉取远程仓库



**git branch -- set-upstream-to =origin/master 设置上游分支，不再需要指定线上分支节点，可以直接进行合并**，

没有共同祖先的分支不允许合并

**只能通过代码 git merge --allow-unrelated-histories  强行关联，最关机键的一步**这样才能正常提交

**git push origin HEAD:main(线上分支名)**

![1663881846482](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663881846482.png)

![1663882201181](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663882201181.png)

当线上分支名和本地分支名不一致的时候

需要指定分支名

git push origin master:main(线上分支名)

设置默认分支

git config push.default simple（默认和本地分支同名的线上分支）

git config push.default upstream (存在的上游分支名字)

**切换分支**

git checkout -b dev  切换分支

没有上游分支,会把本地的分支推送到远程仓库新建同名分支 git config push.default current

<h4>标签

git tag v1.0.0

git tag -a v1.2.0 -m "store状态管理"

git show  查看标注

git push origin v1.0.0       tag推送远端

git checkout v1.0.0   跳转到相应版本

![1663915526991](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663915526991.png)

<h4>git提交对象,提交原理

git cat file p 4658 查看提交文件内容

**git创建分支**

只是创建一个可以移动的分支,git branch testing

分支切到哪,head指针就指到哪

git checkout -b dev 创建分支并切换到此分支

合并分支,解决冲突

git merge hotfix

修改同一个文件会冲突

比较下来左边是master分支,右边是修复的分支

然后把解决过的内容先提交本地仓库,再提交到线上仓库

![1663923362940](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663923362940.png)

<h4>git的工作流

![1663923764773](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663923764773.png)

![1663924039786](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663924039786.png)

新功能新特性开feature分支

Release 准备发布分支,准备发布合并到master

<h4>远程分支

建立远程分支

git remote add origin xxx  此时将远程库地址设置成origin

git pull/push

**和远程分支建立联系**

git branch --set-upstream-to=origin/main

git config push.default upstream

pull 时,此时有单独的main分支,线上分支和线下分支没有共同节点,需要设置

git merge --allow-unrelated-histories 将线上和本地两个仓库文件设置有公共节点

push时,需要修改默认参数simple为upstream

git config push.default upstream



**线上分支和线下分支不一致的时候**

git checkout --track origin/main

git push origin develop 直接将本地develop push到远端并建立develop分支

git checkout develop  检查线上分支，建立线下分支，显示跟踪线上分支

git push origin -d feature 删除远程 feature

<h4>git rebase

git rebase master 操作会把当前指向的节点重新指向master指向的节点

git log --pretty=online 查看简洁的提交记录

git log --pretty=online ==graph 查看图结构日志

git checkout master  

get merge feature  此时将master指针调整到feature指针指向的文件

![1663933497160](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663933497160.png)

**永远不要再主分支使用rebase**

一定要再次分支进行操作

![1663933847873](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663933847873.png)

**git的线上和本地是分两步完成的，需要执行至少两次命令**

**线上和本地关联git branch --set-upstream-to=origin/main**

**git merge --allow-unrelated-histories 将线上和本地两个仓库文件设置有公共节点**

**push时,需要修改默认参数simple为upstream**

**git config push.default upstream**

