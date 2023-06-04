---
title: '01_使用 hexo 搭建一个博客网站 '
updated: '2023-06-04 23:56:11'
excerpt: >-
  _使用hexo搭建一个博客网站hexo安装hexo官网安装使用npm安装npminstallhexoclig初始化某个项目文件（新建目录）进入目录后hexoinithexoinit#博客初始化(安装所需要的包)目录结构​public​目录下存放的是我们生成的「静态页面」_​source_posts​目录下存放的是我们写的「文章」_​themes​目录下存放的是「博客」的主题_​_configyml​是「博客全局配置」文件_​_configlandscapeyml​是「博客主题配置」文件​运行本地运行hex
tags: []
categories:
  - _posts
permalink: /post/01_使用 hexo 搭建一个博客网站 .html
comments: true
toc: true
---

# 01_使用 hexo 搭建一个博客网站 



### hexo 安装

[hexo 官网](https://hexo.io/zh-cn/)

#### 安装

使用 npm 安装

```undefined
npm install hexo-cli -g
```

初始化某个项目文件（新建目录）

进入目录后  hexo init

```undefined
hexo init  # 博客初始化 (安装所需要的包)
```

目录结构

​`public`​目录下存放的是我们生成的**「静态页面」**；

​`source/_posts`​目录下存放的是我们写的**「文章」**；

​`themes`​目录下存放的是**「博客」**的主题；

​`_config.yml`​是**「博客全局配置」**文件；

​`_config.landscape.yml`​是**「博客主题配置」**文件

​

#### 运行

本地运行  hexo s

```undefined
hexo s # http://localhost:4000/预览
```

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353562.png)​

访问

```undefined
http://localhost:4000/
```

![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353746.png)​

‍

#### 新建文章

运行路径下执行命令 hexo n：

```undefined
hexo n "第一篇博客" # 新建一个名为第一篇博客.md的文件
```

‍

‍

### 主题

#### 搭建基于ocean 主题的站点

[首页（主题网站）](https://www.zhwangart.com/)

[ocean GiteHub地址](https://github.com/zhwangart/hexo-theme-ocean)

[ocean主题安装指导文档](https://www.zhwangart.com/2018/11/30/Ocean/)

##### 安装

```undefined
git clone https://github.com/zhwangart/hexo-theme-ocean.git themes/ocean
```

##### 配置

在 `root`​/ `_config.yml`​ 中选择 `theme: ocean`​

```undefined
theme: ocean
```

**Ocean** 使用了 feathericon 图标库，

```undefined
https://feathericons.com/
```

菜单中的图标定义在“CSS source/css /_partial/navbar.styl”中，可根据需要进行更改或添加。

```undefined
themes\ocean\source\css\_partial/navbar.styl
```

如果你不需要开启 相册 与 关于 菜单，需要删除或者注销掉他们的图标，如下边的示例：

```undefined
.nav-item
  &:nth-child(1)         // 主页
    .nav-item-link
      &::before
        content '\f12f'
  &:nth-child(2)         // 归档
    .nav-item-link
      &::before
        content '\f12a'
  //&:nth-child(3)         // 相册
  //  .nav-item-link
  //    &::before
  //      content '\f1a9'
  //&:nth-child(4)         // 关于
  //  .nav-item-link
  //    &::before
  //      content '\f174'
```

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353869.png)​

这里 相册和关于先注释一下，内容后期看一下

试验了一下，这里注释只能将图标取消掉

取消的话需要主题配置这里注释一下

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353932.png)​

‍

评论功能这里不进行开启，后期再看

开启标签和分类功能后期再看

‍

‍

##### 插件安装

插件安装（关于本地搜索功能）

[hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 本地检索

安装

```undefined
npm install hexo-generator-searchdb --save
```

配置 Hexo 的配置文件 `_config.yml`​ 

添加插件配置（注意：不是主题的配置文件）：

```undefined
search:
  path: search.xml
  field: post
  content: true
```

##### 运行

```undefined
hexo s
```

‍

##### 修改标签

如果需要需求页面的部分标签描述，需要到下面这个文件中改

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353007.png)​

不是很理解这个国际化语言设置，先备份一下

```undefined
categories: Categories
search: Search
tags: Tags
tagcloud: Tag Cloud
tweets: Tweets
prev: Prev
next: Next
comment: Comments
archive_a: Archives
archive_b: "Archives: %s"
page: Page %d
recent_posts: Recent Posts
newer: Newer
older: Older
share: Share
powered_by: Powered by
rss_feed: RSS Feed
category: Category
tag: Tag
```

直接用它同一路径下的 zh-CN.yml 文件内容覆盖 defalut.yml 文件内容

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353084.png)​

还有部分标签，是直接在主题配置文件中直接改就好了（开始以为是配置属性）

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353160.png)​

主页的这个属性的改变，在 F12 调试中找到是css样式 video-inner text-center text-white 中设置

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353238.png)​

搜索文件后会发现这个配置是 config.subtitle 中设置的

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353374.png)​

但是在这个过程中，自己尝试修改了很多次，找了很多文件，还是不太清楚如何改

后面自己想了一下，这个是配置文件修改，其实不管是主题配置还是项目配置修改都是生效的

但是需要你重启一下服务（有时候也可能是缓存问题）

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353451.png)​

再次访问已经OK了

​![image](https://blogpublishpicture.oss-cn-guangzhou.aliyuncs.com/cnblogs/202306042353548.png)​

网上有一些优化内容，这里暂时不参与和研究

‍

##### 部署到 GitHub

看了一下说 Gitee 不能进行自动更新部署操作，这里还是使用 Github 作为自己的发布平台

安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)。

```undefined
npm install hexo-deployer-git --save
```

hexo 的配置文件 `_config.yml`​,  添加一下以下配置

```undefined
deploy:
  type: git
  repo: <repository url> #https://github.com/Github用户名/Github用户名.github.io.git
  branch: [branch] #published
```

在自己的 Github 账号下新建仓库，

仓库名必须为你的`Github用户名.github.io`​

​​​​

在博客根目录打开Git Bash，输入以下命令

```undefined
hexo d
```

> 当执行 `hexo deploy`​ 时，Hexo 会将 `public`​ 目录中的文件和目录推送至 `_config.yml`​ 中指定的远端仓库和分支中，并且**完全覆盖**该分支下的已有内容。
>
> 简单来说该指令集成了git的一部分操作

或者（建议）

```undefined
hexo clean                            #清除缓存       可缩写hexo c
hexo generate                         #生成静态文件    可缩写hexo g
hexo deploy                           #部署到Github   可缩写hexo d
```

部署后访问

```undefined
https://Github用户名.github.io/
```

‍

##### 配置 SSH 连接

回到Git Bash中，配置Github账户信息（`用户名`​​和`邮箱`​​都替换成你自己Github上的）：

```text
git config --global user.name "`用户名`"
git config --global user.email "邮箱"
```

在Git Bash中输入：`ssh-keygen -t rsa -C "你的Github邮箱"`​​ 生成ssh

```text
ssh-keygen -t rsa -C "邮箱"
```

然后按Git Bash给出的路径`(C:\Users\Lete.ssh)`​​找到`id_rsa.pub`​​文件 并复制其中的内容

进到新建的Github仓库 点击右上角`setting`​​​进入设置找到`Deploykeys`​​​选择 `Add Deploy keys`​​​ `Title`​​​随便填写 `Key`​​​的内容填刚才`id_rsa.pub`​​​文件中复制的内容

配置后再部署提交
