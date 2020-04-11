---
title: "如何用Hugo搭建个人博客"
date: 2020-04-11T22:16:11+08:00
draft: false
---
我也是第一次成功使用Hugo搭建博客站并托管到Github，把完整使用Hugo搭建博客的过程分享一下。

## 了解一下Hugo：
> Hugo，译为雨果，目前世界上最快的博客生成器，以Go语言实现的静态网站的生成器。

## Hugo（For Mac）
安装hugo，打开终端，输入：

    brew install hugo

安装完成后，输入命令查看是否安装成功：

    hugo version

## 使用Hugo生成站点
1. 可以查看官方文档，☞[官方教程](https://gohugo.io/)
2. 也可以看我的步骤。
   
### 1.找到一个目录，创建一个新的site，名为**xxx.github.io-creator**：

    hugo new site xxx.github.io-creator

*xxx是你Github的名字，成功后会在当前目录下生成一个名为xxx.github.io-creator的目录*


### 2.初始化site，并指定默认主题（可以改，首次最好使用默认主题）
```
cd quickstart
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```
然后将主题添加到配置文件：

    echo 'theme = "ananke"' >> config.toml


### 3.添加内容
在posts目录下创建一个名为xxx的MarkDown文件

**hugo new posts/xxx.md**

*文件里默认存在以下内容*
```
---
title: "xxx"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```
*添加自己的内容后，将draft修改为flase发布才能正常显示，draft是草稿*

### 4.启动Hugo服务
`hugo server -D`
```
                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
启动后可以打开`http://localhost:1313/`在本地预览，Ctrl+C关闭后就无法访问

### 5.站点配置
打开目录下`config.toml`
```
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```
默认英文显示，显示中文将languageCode修改为**zh-Hans**

## 构建静态页面
    hugo -D
在当前目录下生成一个public目录，这个目录下的文件就是*博客的静态页面*

**到这里博客的本地文件已生成完毕**，以下为部署至Github访问

***
## 部署至Github
1. 在生成的目录即上文所说的**xxx.github.io-creator**目录下
   
   新建 *.gitignore*，打开该文件，在文件第一行填入： /public/

   *在push的时到git的远程仓库，*.gitignore*这个文件内包含的目录会被忽略*
2. 初始化public,将静态页面的目录初始化git
   ```
   cd public
   git init 
   ```
3. 打开[Github](https://www.github.com)，新建仓库 **xxx.github.io**（xxx是你git账户名）
4. 在`public`目录下执行：
   ```
   git remote add origin git@github.com:xxx/xxx.github.io.git
   git add .
   git commit -m '第一次部署'
   git push -u origin master
   ```
5. 此时代码已经上传至你Github的远程仓库，进入该仓库首页，点击`setting`
   ![](/images/2.png)
6. 找到Github Pages一栏
   ![](/images/3.png)
   *将branch修改为master*

## 通过Github的域名访问你的博客
打开**xxx.github.io**，即可访问你部署的博客


## 如果想配置其他域名
1. 打开[阿里云](https://www.aliyun.com/)
2. 打开 域名与网站-域名注册
   ![](/images/4.png)
3. 注册购买自己想要的域名后，打开控制台，点击域名后的*解析*
   ![](/images/5.png)
4. 打开Github的博客的仓库，setting-GitHub Pages-Custom domain，点击**Lean more**
   ![](/images/6.png)
   ![](/images/7.png)
   找到apex
   ![](/images/8.png)
   找到apex需要配置的A记录
   ![](/images/9.png)
5. 将apex域指向GitHub页面的IP地址，即在阿里云添加这4个A记录
   添加记录
   ![](/images/10.png)

   主机记录为`@`，记录值为上面的IP，分别添加4次

   ![](/images/11.png)
6. 添加完成后，回到Github的博客的仓库：
   
   setting-GitHub Pages-Custom domain
   **填入自己注册的域名，点击SAVE**即可通过自定义域名访问自己的博客