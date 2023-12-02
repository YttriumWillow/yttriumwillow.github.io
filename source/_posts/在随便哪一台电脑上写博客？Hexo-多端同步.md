---
title: 在随便哪一台电脑上写博客？Hexo 多端同步
date: 2023-11-04 11:00:11
cover: /gallery/covers/20231102-2.jpg
categories: 博客
tags:
  - 博客
toc: true
---
将 Github 运用到底！

<!-- more -->

再来个奇妙小仓库还是太麻烦了，我们使用分支功能。

### 启用同步

在第一用户端的博客根目录下 Git Bash 新建一个仓库。

```bash
git init
```

然后确保你的 `.gitignore` 文件里屏蔽了以下目录和文件的提交。

```txt
/.deploy_git  
/public
```

添加该仓库到远程仓库列表：

```bash
git remote add origin [your github repository]
# 例如作者本人的:
# git remote add origin git@github.com:YttriumWillow/yttriumwillow.github.io.git
# 这是 SSH 模式下的提交，你的远程仓库 HTTPS 地址可能是这样
# https://github.com/username/username.github.io.git
```

一路提交更改到 `hexo` 分支。

```bash
git add . # 将变更添加到 git 暂存区  
git commit -m "[comment]" # 提交本次更改，并附加提交信息
git push origin main:hexo # 将本地 main 分支的提交发布到远程仓库的 hexo 分支
# 我为了省事用的 main 主分支，有的仓库的默认分支可能是 master
```

你的 Github 仓库里面就会出现这个分支。

![img](/img/20231104/your-github-displays.png)

### 在其他设备上同步

如果这是一台全新的设备， 请先安装 Git, Node.js 并更新 npm。

打开你需要同步该文件的目录并启动终端。

使用 Git 同步：

```bash
git clone -b hexo [your github repository]
```

安装 hexo 依赖：

```bash
npm install hexo-cli -g
npm install
npm install hexo-deployer-git # 这东西好像会同步到 package.json 但最好安装一下
```

已经同步完毕。使用 `hexo g / hexo s` 进行测试。

更新博客前请先 pull 进行同步。

```bash
git pull origin hexo
```

更新结束后提交修改。

```bash
git add .  
git commit -m "[comments]" 
git push origin main:hexo
```

你可以直接使用 bat 来做到一键完成这些功能。

这样我们就可以在不同的设备上写 hexo 博客了。
