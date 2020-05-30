---
title:  关于这个站点的建设以及Butterfly主题的优化

author: Radium-Bit

authorLink: ''

cover: https://cdn.jsdelivr.net/gh/radium-bit/res@latest/2233.webp

date : 2020-3-31

tags: About_WebSite

sticky: 1
---

{% note danger %}
**注意！这些方案只确定对上述版本的Butterfly主题有用，其他的hexo主题不保证兼容**
{% endnote %}
这是我的修改版[Butterfly-R](https://github.com/Radium-bit/res/tree/master/Butterfly-R)。属于Butterfly主题的一个衍生版本。下载后直接覆盖到你的**主题根目录**下
设置过程也可以参阅[JerryC的官方文档](https://jerryc.me/posts/4aa8abbe/)
{% note warning %}
如果你对这一切完全不熟悉，建议先自学Hexo，Pug和Markdown语法；否则可能会出现部分看不懂的情况。
{% endnote %}

1.首先，您需要建立一个github账户。（如果已有Github则跳过这一步)

2.创建一个新的项目，并且初始化ReadMe.md

2.1 点击右上方你的头像，进入 Your repositories

![](https://cdn.jsdelivr.net/gh/radium-bit/res@latest/CtBl/gittest.png)

2.2 点击New，在项目名称上写 

```bash
$YN.github.io    ## 将$YN替换为你的GitHub名称，后续出现也当如此
```

然后打钩选项  （Initialize this repository with a README）

![](https://cdn.jsdelivr.net/gh/radium-bit/res@latest/CtBl/startRM.png)

最后点击 [Creat repositories]即可完成创建。

当你看到你的仓库出现一个项目。名为$YN.github.io时，证明你已经完成了sever主机准备建设。

![准备完成](https://cdn.jsdelivr.net/gh/radium-bit/res@latest/CtBl/Final_SV.png)

*至此，你已经完成了服务器的预备建设。尝试访问$YN.github.io吧。只要不是“未找到网页”这一类的就表示你已经成功了。*

>3.接下来，部署请自行安装NodeJS，Git
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
```
npm i
```
以安装依赖，确保后续步骤可以正常执行。

>3.1 预览、上传方式
```bash
hexo g    //生成页面
hexo s   //打开本地服务器，进行预览和确认
hexo d  //部署到GitHub Page
```
进入本机浏览器，访问localhost:4000即可访问你的页面  
>3.2调教主题

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
Butterfly.yml的相关设置请参考[JerryC的开发文档](https://jerryc.me/posts/4aa8abbe/)。
bangumi追番设置请参考[Hexo哔哩哔哩番剧页面插件](https://blog.csdn.net/weixin_42429718/article/details/105627458?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159081850719195264544370%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=159081850719195264544370&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-105627458.pc_insert_v5&utm_term=bangumi+butterfly)


---
<font color=#0c74d6 size=5>***未完待续***</font>
<font size=1>封面来自互联网，如有侵权请[点击这里](mailto:radium_official@163.com)联系我。</font>
---
