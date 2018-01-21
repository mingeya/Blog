---
title: 备份Hexo源文件
date: 2018-01-10 10:48:07
tags: hexo
---

## 备份Hexo源文件

### 前言

在我使用Hexo搭建博客后，不久电脑就崩溃了，只能重装系统，幸运的是在重装系统之前把Hexo文件夹上传到了百度晕，因此还能够使用。但是如果更换了电脑需要更新博客或者不小心博客源文件丢失，那将是一件非常糟心的事情了。未雨绸缪，需要对Hexo源文件进行备份。

### 备份方案

在网上搜索了一下，大致有三种方案。

- 将博客源文件拷贝到U盘 ,但是这样做的话，同步又比较麻烦。
- 使用网盘，同样是比较麻烦。
- 将博客文件托管到Github。

大部分是将Hexo文件同样托管至Github。

### 实现方法

- 在[Github](http://github.com/)下创建一个新的repository，取名为`Blog`。(与本地的Hexo源码文件夹同名)

  + 进入本地的`Hexo`文件夹，执行以下命令创建仓库:

  ```js
  git init
  ```

- 设置远程仓库地址，并更新:

  ```
  git remote add origin git@github.com:mingeya/blog.git
  git pull origin master
  ```

- 修改`.gitignore`文件（如果没有请手动创建一个），在里面加入`*.log` 和 `public/` 以及`.deploy*/`。因为每次执行`hexo generate`命令时，上述目录都会被重写更新。因此忽略这两个目录下的文件更新，加快push速度。

- 执行命令以下命令，完成Hexo源码在本地的提交。

  ```js
  git add .
  git commit -m "备份Hexo源码文件"
  ```

- 执行以下命令，将本地的仓库文件推送到Github。

  ```js
  git push origin master
  ```

- 现在在任何一台电脑上，只需要输入`git clone git@github.com:mingeya/Blog.git`,即可完成将Hexo源文件复制到本地。

- 在本地编写完博客时，顺次执行以下命令，即可完成Hexo博客源文件的更新同步，保持Github上的hexo源码为最新版本。

  ```js
  git add .
  git commit -m "更新hexo"
  git push origin master
  ```

- 当远程仓库有更新时，执行以下命令，即可同步hexo源文件到本地。

  ```js
  git pull origin master
  ```

具体备份方案如上，Hexo源代码文件就完成了同步和更新了。