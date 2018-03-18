---
title: Github和git命令总结
date: 2017-10-29 21:42:31
update: 2017-10-29 21:42:31
categories: Github和git
tags: 
---

# Github
## 1.仓库
用于存放项目

<!-- more -->

## 2.分支
master：主分支，存放**最终版本代码**

其他分支：对主分支的拷贝，我们**在其他分支修改再合并**到master。

在分支中对某个文件修改，然后Cmommit Changes就可以修改。

## 3.请求代码合并
pull request：子分支请求和master分支进行合并，确认之后可以提交

merge pull request：确认合并到master。 

如果想要删掉已经合并的分支，Delete branch

## 4.fork

把一个repo拷贝到你的页面，你也持有该仓库的一个副本

## 5.watch

该仓库有变更时，可以收到邮件提醒。

## 6.star

收藏

#### 工作流程

**fork**一个repo作为自己的副本->用**git**命令修改、管理该仓库（git add 、git commit 、git push）

->发起pull request，就可以**把自己的修改提交给原始仓库管理者**



# git命令

## 1.git clone https：//
先去repo页面点绿色的**Clone or download** ，复制地址

然后就可以在某个文件夹，右键->git bash使用命令 git clone + 已复制的https地址

上面的只能创建master分支。如何指定特定分支？

eg：git clone -b feature-edits https://github.com/Faith-Uchiha/hello-world.git

**git clone 分支名 repo https地址**

## 2.git pull
拉取该分支**最新**内容，与本地（当前电脑、文件夹）对比。
就是更新该分支的。

## 3.git add
git add .——添加所有目录  git add 文件名——添加文件

注意此命令只是**添加到了git队列，并没有真正上传到仓库分支**

即使不是添加新文件，而是**在旧文件上修改**，想要更新到分支上，也要git add git commit git push

## 4.git commit -am

-am 后面跟上注释，双引号

## 5.git push
真正添加到分支。
