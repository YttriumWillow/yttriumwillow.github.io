
## **准备环境**

* 安装nodejs✅
* 安装git✅
* 安装hexo✅

```text
 # 此为全局安装，可能需要sudo权限
 npm install -g hexo-cli
```

## **创建git仓库**

直接在github主页创建一个新的仓库，此处假设仓库名称为blog_tensorrt

## **使用hexo建初始博客**

首先初始化一个博客项目，此处blog可以换成自己想要起的名称。该操作之后在当前目录下会出现一个叫做blog的新的文件夹

```text
 hexo init blog
```

进入blog文件夹下

```text
 cd blog
```

可以看到当前的文件夹下有一个themes的文件夹，此时看到里面没有文件，下载icarus主题代码到其中

```text
 git clone git@github.com:ppoffice/hexo-theme-icarus.git /themes/icarus
```

之后修改_config.yml文件，将theme修改为icarus

```text
 theme: icarus
```

之后在命令行进行构建

```text
 hexo g
```

输入生成命令可能会报错，提示有没有安装的包，安装确实的包

```text
 yarn add bulma-stylus@0.8.0 hexo-component-inferno@^1.1.0 hexo-pagination@^2.0.0 hexo-renderer-inferno@^0.1.3 inferno@^7.3.3 inferno-create-element@^7.3.3
```

接着生成

```text
 # 该命令多执行几次，知道没有新的文件生成
 hexo g
```

查看网页初始效果

```text
 hexo s
```

* [ ] 打开网页[http://localhost:4000](http://localhost:4000/)

自定义博客设计
此时博客目录下有文件_config.icarus.yml，修改该文件即可，每一项在icarus官网https://ppoffice.github.io/hexo-theme-icarus/Configuration/icarus%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97-%E4%B8%BB%E9%A2%98%E9%85%8D%E7%BD%AE/#more均有详细的说明，在此不做赘述。

部署网站
首先修改_config.yml文件

 # Site
 title: eryoyo的博客
 subtitle: 坚持✊
 description: tensorrt笔记整理
 keywords: 
 author: eryoyo
 language: zh-CN
 timezone: Asia/Shanghai
 ​
 # URL
 ## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
 url: https://eryoyo.github.io/blog_tensorrt
之后进行本地查看

 hexo clean
 hexo g
 hexo s
网站可以在http://localhost:4000/blog_tensorrt里面查看到

之后接着修改_config.yml文件

 deploy:
   type: git
   repo: git@github.com:eryoyo/blog_tensorrt.git
   branch: master
安装部署需要的包

 npm install hexo-deployer-git --save
之后部署

 hexo deploy
在仓库里面setting里面修改github pages的none为master分支，点击save，等待一会之后就可以在访问自己刚刚部署到的网站了



主站建成。