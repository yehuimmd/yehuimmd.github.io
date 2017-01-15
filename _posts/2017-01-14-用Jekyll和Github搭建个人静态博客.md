---
layout: post
title:  "用jekyll和github搭建个人静态博客"
date:   2017-01-14 13:03:42
categories: jekyll update
---

## jekyll+github搭建个人博客

经过一天多的折腾，终于算是搭建好了自己的个人博客，看到有些社区评论说：在windows下用jekyll搭建静态博客，简直就自讨苦吃，但是都到一半了，有什么办法呢，只好坚持搭完咯~~

搭建github博客可以用hexo，也可以用jekyll，我用的是后者，hexo大家可以试试，在这里推荐一个用hexo搭建的教程：http://gaoxianglyx.top
下面就是我的搭建步骤了，希望可以帮到还在折腾的你：

- 下载ruby
- 安装jekyll
- 安装bundler
- 建立你的第一个静态博客
- 开启jekyll服务器
- 写一篇自己博文
- 用github pages 展示你的博客

     - 创建个人仓库
     - 克隆仓库到一个指定的文件目录
     - 把你本地的第一个博客文件里的所以文件复制到这个克隆下来的文件
     - 把这些文件push到远程仓库
     - 查看你的博客网站
 
接下来我们的操作都是在cmd命令行中进行的

### 下载ruby

什么是ruby：Ruby，一种简单快捷的面向对象（面向对象程序设计）脚本语言，安装Jekyll需要电脑上安装Ruby，以下是安装步骤：

- window系统下，可以使用rails install来安装ruby环境，下载地址为：http://rubyinstaller.org/downloads/  ，建议下载2.3以上的新版。
- 下载 RailsInstaller 之后，双击 railsinstaller-3.2.0 文件，启动 Ruby 安装向导点击next，向导完成安装，记得勾选 Add Ruby executables to your PATH，直到 Ruby 安装程序完成 Ruby 安装为止
- 安装后，在cmd中输入ruby -v和gem -v来看看是否安装成功，看到版本号就说明成功。

**注：用RubyInstaller安装Ruby之后都附带有Gems，如有需要可以单独下载RubyGems。网址为：https://rubygems.org/pages/download**

### 下载jekyll

好激动啊！终于到这里了，
jekyll：jekyll是一个简单的免费的Blog生成工具，类似WordPress。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。但是可以配合第三方服务,例如Disqus。最关键的是jekyll可以免费部署在Github上，而且可以绑定自己的域名。（注：我自己的没有绑定域名）
我们使用gem来安装jekyll，在命令行中输入

      gem install jekyll
      
所有的jekyll的gem依赖包都会被自动安装。

### 下载bundle

在命令行输入
          
      gem install bundler
      
  bundler：就是一个打包机，他会连接rubygems.org（或者其他你声明的源），然后列出所有你指定的符合你需要的 gem。因为所有你在Gemfile里的依赖有它们自己的依赖，所以基于上面的Gemfile运行bundle install会安装相当多的的 gem。（我也不太了解，自己可以百度）
  
### 建立自己的第一个博客

首先看看你想把你的博客建在哪里，我的是搭建在C盘，如果你想建在D盘，则输入：

      cd d:
 
 然后输入创建的博客

     jekyll new blog  //blog为你的博客文件名
    
控制台可以看见（创建的地址有所不同）New jekyll site installed in C : /blog。你的C盘的文件夹下也会出现相应的blog文件。

### 开启jekyll内置服务器

实现转入blog的目录，输入：
     
       cd blog//一定要进入创建的对应blog目录，否则服务无法开启
       
然后输入：
       
       jekyll serve  //开启服务器，可以按ctrl+c停止
       
Jekyll服务器默认端口是4000，所以打开浏览器输入：http://localhost:4000 就可以看到生成的博客页面。如下：
![](http://images2015.cnblogs.com/blog/1019973/201701/1019973-20170114223440525-1524406009.png)

### 使用jekyll写博文

你可能喜欢markdown或html来写博文，都可以，但是博文文件的**命名规则**要服从下面的规则：
         
        year-month-title.markup //markup为你的文件格式的后缀名
	
在你的文章头部添加yaml头信息

	---
	layout: post
	title:  "Jekyll+Github搭建个人博客"
	date:   2017-01-14 15:03:25
	categories: original
	---
	
写上自己的博文内容，将这个文件保存在blog里面的_posts目录里面即可。在重启jekyll内置服务器，刷新页面：http://localhost:4000，如果没有，可以先输入：

     jekyll build 
     
     
重新生成页面，在启动服务器，这样就可以在页面看到自己添加的博文的标题了。
这就是在本地搭建jekyll和写博文的大致过程了，相信还有其他的搭建方法，但是估计都是大同小异吧。

### 用github 展示你的博客

接下来的操作都是用GIT命令完成的，不再是cmd了。首先，大家应该都拥有了github账号，没有的注册一个就好了。

- 创建个人仓库

就是建立一个新的仓库，但是这个仓库的名字必须为你的github的名字+github+io，即yourname.github.io

- 将目录切换到你想要放github博客的文件目录下，在这个目录git bash 将刚才建的仓库克隆下来：
    
	    git clone git@github.com:yourname/yourname.github.io.git
	    
这时，你会发现你的文件夹下会多出一个yourname的文件，我们把之前的blog下的所有文件复制到里面。

- 然后把里面的所有文件push到刚刚建的远程仓库，步骤我就不写了。
这时，在浏览器里面输入网址：http://yourname.github.io  就可以看你的个人博客网站了，这就是你的博客网站的地址了。
**前面所说的yourname指的是你的github账号名字。**

- 嗯，接下来你就可以查看你的博客网站了。其中还可以在github的settings中选择你的博客主题。我也还在选主题中。

**这就是一个用jekyll+github搭建个人博客的大概过程了，在搭建过程中，你也许会遇到种种的问题，那就百度吧。我也是这样过来的！~~~~**，

这是我的一个小总结，希望可以同样喜欢折腾的你们。
