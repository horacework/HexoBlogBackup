title: 常用Git命令小结
date: 2016-09-28 16:19:02
tags: [Git,程序开发]
---

## 前言

从大二暑假实习到现在接触Git不知不觉已经两年了，自从用上Git之后就习惯性地把非商业性的代码共享（备份）到Github上，随着IDE工具的发展，许多IDE都已经集成Git版本管理工具，但我还是习惯于在bash内操作。

<!-- more -->

## 简单的概念

个人意见：Git就是给你提供代码版本管理的工具，目标就是能够熟练运用，提高工作效率，我们只需要把需要用的功能掌握就OK了。

Git 内部管理分为三个区，工作区、暂存区、主要代码区（当前分支）

![img1](/img/git.jpg)

## 实际怎么用

**初始化** ` $ git init `

在当前文件夹建立git仓库，一般在项目代码文件夹内执行此命令

**第一步**  ` $ git add fileName.xxx `

将代码区的文件添加到暂缓区 ,也可以直接把当前文件夹内的所有文件都添加到暂缓区 `$ git add . ` 或者 `$ git add -A `

**第二步** ` $ git commit -m'messagexxxxx' `

将暂缓区内的文件提交到当前代码分支，message是提交的log

`$ git status ` 可查看当前状态以及文件的提交状态（工作区、暂缓区），提交之后会显示为空

## 配合Github使用

**添加秘钥** 可以在个人Github主页内的Setting-->SSH and GPG keys选项中添加本机秘钥，至于如何生成公钥里面有详细教程

**添加远程分支** `$ git remote add origin URLURLURL ` 

注意URL的形式，有https与ssh方式，ssh方式在你添加秘钥后无需输入用户名与密码，https方式则相反。

`$ git push -u origin master ` 把master分支代码推送到远程github仓库，同步完成后即可在github上看到自己的commit。

## 常见问题

#### .gitignore文件无法生效

在add之前编辑.gitignore文件是可以生效的，但是实际情况在我们commit了几次之后，发现很多私人配置都传上去了，所以我们需要配置.gitignore文件来忽略掉我们的私人或者不需要上传的文件。

`$ git rm cached fileName.xxx ` 或者 `$ git rm cached . ` 除去全部文件的追踪

#### github文件与本地无法同步导致无法上传

遇到这种情况基本上是因为你在github上初始化项目的时候候选了自动生成readme文件或者法律声明文件。

解决办法如下：先将上面的文件pull下来 `$ git pull ` （有可能会显示冲突）
之后commit一次，之后就可以push上去了。

## 小结
以上是我这两年来常用的git命令以及常见问题，概念部分内容以及图片参考[廖雪峰GIT教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
