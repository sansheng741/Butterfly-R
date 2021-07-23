---
title:  关于这个站点的建设以及Butterfly主题的优化

author: Radium-Bit

authorLink: ''

cover: https://cdn.jsdelivr.net/gh/radium-bit/res@latest/2233.webp

date : 2020-3-31

tags: About_WebSite

sticky: 1
---

{% note info %}
这是我的修改版[Butterfly-R](https://github.com/Radium-bit/Butterfly-R)的教程配置。属于Butterfly主题的一个衍生版本。下载后直接覆盖到你的**主题根目录**下
设置过程也可以参阅[JerryC的官方文档](https://jerryc.me/posts/4aa8abbe/)部分内容通用原版Butterfly。
[Butterfly-R -- 蓝奏云下载地址](https://radium-bit.lanzous.com/iFgwFf925qh)
{% endnote %}
{% note danger %}
**注意！这些方案只确定对上述版本的Butterfly主题有用，其他的hexo主题不保证兼容**
{% endnote %}
{% note warning %}
如果你对这一切完全不熟悉，建议先自学Hexo，Pug和Markdown语法；否则可能会出现部分看不懂的情况。
{% endnote %}

## 1.首先，您需要建立一个github账户。（如果已有Github则跳过这一步)

前往[Github](https://github.com)注册一个账号
![](https://wx1.sbimg.cn/2020/08/27/6QfXN.jpg)
点击 *Sign Up* 按钮即可进入注册流程
![](https://wx2.sbimg.cn/2020/08/27/6A5Zk.jpg)
按照提示输入你想要创建的用户名，邮箱，进行人机验证后即可。


## 2.创建一个新的项目，并且初始化ReadMe.md
#### 2.1 点击右上方你的头像，进入 Your repositories


![](https://wx1.sbimg.cn/2020/08/27/6Q7cw.png)

#### 2.2 点击New，在项目名称上写 


```bash
$Username.github.io    ## 将$Username替换为你的GitHub名称
```
<font color= 	#4169E1 size=3>后续出现 *$Username* 符号的话也当如此，替换为你的Github用户名。</font>

然后打钩选项  （Initialize this repository with a README）

![](https://wx1.sbimg.cn/2020/08/27/6QtnG.png)

最后点击 [Creat repositories]即可完成创建。

当你看到你的仓库出现一个项目。名为$Username.github.io时，证明你已经完成了sever主机准备建设。

![准备完成](https://wx2.sbimg.cn/2020/08/27/6A4dj.jpg)

*至此，你已经完成了服务器的预备建设。尝试访问$Username.github.io吧。只要不是“未找到网页”这一类的就表示你已经成功了。*

## 3.接下来，部署请自行安装NodeJS，Git

可以输入以下命令确认
```bash
node -v //检查node版本
npm -v //检查npm版本
git --version //检查git版本
```

然后，准备安装Hexo

```bash
npm i hexo-cli -g //安装Hexo
hexo -v           //验证安装
hexo init         //初始化Blog文件夹
npm install       //安装基本组件
```
<font color=#d31212 size=3 face="黑体">覆盖根目录，请覆盖后用命令行定位到主题根目录输入</font>

```bash
npm i
```

以安装依赖，确保后续步骤可以正常执行。

#### 3.1 预览、上传方式

```bash
hexo g    //生成页面
hexo s   //打开本地服务器，进行预览和确认
hexo d  //部署到GitHub Page
```

需要注意的是，如果需要部署到你的github，请先在根目录_config.yml添加

```yaml
deploy:
  type: git
  repository:
        gtihub: https://github.com/$Username/$Username.github.io
  branch: master
```

以及，在你的博客/source目录下添加一个文件叫"CNAME"，无扩展名。
并且在里面写入 

```
$Username.github.io
```

进入本机浏览器，访问localhost:4000即可访问你的页面  
确认无误后，即可执行

```bash
hexo d
```

部署到你的 *Github Page*
完成以后，你的页面将可以用 *$username.github.io* 来访问。
#### 3.2调教主题

{% note warning %}
在这之前：请了解 [jsDelivr](https://www.cnblogs.com/zhsh666/p/11432956.html) 等CDN的使用方法。这里不做更多描述
{% endnote %}

(1) 主题目录下_config.yml的配置

```Yaml
# Site
title: Radium·Stardust   #站点名
subtitle: ''             #子站点名
description: ''          #为搜索引擎抓取而准备的关键标题区
keywords:                #为搜索引擎抓取而准备的关键词区
author: Radium-bit       #网站作者名
language: zh-CN          #网站使用的语言，zh-CN为简体中文，zh-TW为繁体，en为默认英文
timezone: ''             #网站使用时区，一般不必设置
email: radium_official@163.com #网站的邮箱设置

#Medias (hexo-tag-mmedia插件设置)
mmedia:
  aplayer:
    cdn: https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.js
    style_cdn: https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.css
    default:
  meting:
    cdn: https://cdn.jsdelivr.net/npm/meting/dist/Meting.min.js
    api:
    default:
  dplayer:
    cdn: https://cdn.jsdelivr.net/npm/dplayer/dist/DPlayer.min.js
    style_cdn: https://cdn.jsdelivr.net/npm/dplayer/dist/DPlayer.min.css
    hls_cdn: https://cdn.jsdelivr.net/npm/hls.j/dist/hls.min.js
    dash_cdn: https://cdn.jsdelivr.net/npm/dashjs/dist/dash.all.min.js
    shaka_dash_cdn: https://cdn.jsdelivr.net/npm/shaka-player/dist/shaka-player.compiled.js
    flv_cdn: https://cdn.jsdelivr.net/npm/flv.js/dist/flv.min.js
    webtorrent_cdn: https://cdn.jsdelivr.net/npm/webtorrent/webtorrent.min.js
    default:

##b站追番设置
bangumi:
  enable: true #是否开启页面
  vmid: 445498147  #你的b站UID，请确认隐私设置已经开放
  title: '追番列表' #追番页面的标题
  quote: '生命不息，追番不止！' #你想说的话
  show: 1           #初始显示页面：0: 想看 , 1: 在看 , 2: 看过，默认为 1
  loading: '/img/bangumi-loading.gif'
```

#### 3.3 看板娘相关
看板娘使用了JSDelivr的方式引用，相关部分在 Butterfly.yml 文件中配置inject （即插入）

```yaml
<script src="https://cdn.jsdelivr.net/gh/radium-bit/res@master/live2d/autoload.js"></script>
```
大致格式如下
```yaml
# inject
# 插入代码到头部</head>之前 和 尾部</body>之前
inject:
  head:
  # - <link rel="stylesheet" href="xxxxx">
  - <link rel="stylesheet" href="/css/icons.css">
  #- <link rel="stylesheet" href="/css/mouse.css">
  #- <link rel="stylesheet" href="/css/background.css">
  bottom:
    # - <script src="xxxx"></script>
    - <script src="https://cdn.jsdelivr.net/gh/radium-bit/res@master/live2d/autoload.js"></script>  ##这个就是看板娘了
```
如果需要更改看板娘的参数，比如服饰，模型等。请clone分支[Live2D](https://github.com/Radium-bit/res/tree/master/live2d)
到你自己的电脑上并且修改 *waifu-tips.js* ，相关参数说明在js里有注释，自己看吧。  
如果要修改看板娘说的话，修改 *waifu-tips.json*  
最后，修改*autoload.js*中的链接指向部分
```javascript
// 注意：live2d_path 参数应使用绝对路径
const live2d_path = "https://你的服务器中Live2D资源绝对路径";
```
接着，把修改好的文件上传到你的服务器上，改变script标签即可
```html
<script src= "这里写你服务器里Live2d文件夹的autoload.js的链接">
```
就像这样
## 相关设置 
Butterfly.yml的相关设置请参考[JerryC的开发文档](https://jerryc.me/posts/4aa8abbe/)。  
bangumi追番设置请参考[Hexo哔哩哔哩番剧页面插件](https://blog.csdn.net/weixin_42429718/article/details/105627458?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159081850719195264544370%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=159081850719195264544370&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-105627458.pc_insert_v5&utm_term=bangumi+butterfly)  
Mmdia插件来自*会飞的小弋*，详细文档请参阅他的博文[hexo文章插入多媒体](https://lovelijunyi.gitee.io/posts/743c.html#%E4%BD%BF%E7%94%A8%E6%8F%92%E4%BB%B6)



---
<font color=#0c74d6 size=5>***未完待续***</font>
<font size=1>封面来自互联网，如有侵权请[点击这里](mailto:radium_official@163.com)联系我。</font>
---
