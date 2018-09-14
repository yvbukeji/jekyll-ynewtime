# 📌 jekyll-ynewtime

基于 Jekyll 的一个开源主题。示例见：[DEMO](https://biki.ml/)

![](/media/files/WEBP/intro-1.webp)

👆 首页

![](/media/files/WEBP/intro-2.webp)

👆 归档页

![](/media/files/WEBP/intro-3.webp)

👆 标签页

![](/media/files/WEBP/intro-4.webp)

👆 介绍页

## 🔨 安装

1、 [fork](https://github.com/Ynewtime/jekyll-ynewtime) 这个模板；

2、 修改项目名称；

将 `jekyll-ynewtime` 改为你想要改成的博客名称，如果是站点主页，则修改为：`your-username.github.io`，如果是项目主页，则修改为对应项目的名称，然后在 `_config.yml` 修改一下 `baseurl` 的配置即可。

3、修改 `_config.yml` 中的配置项；

```yml
name: "Y" # put the site's name here
permalink: /:title # the way you wanna your links look like ==> https://jekyllrb.com/docs/permalinks/
description: "Your site's description" # put your site's description here
author: "Stephen" # put your name here
atom-baseurl: "https://your-site-url" # the url for rss feed, you can change it to your site's url
baseurl: "" # if you aren't publish your blog under permalink like: /blog/, you don't need change this, or change it to /your-repo's-name
social: "https://twitter.com/your-username" # put your social links here
```

## 🔨 更多特性

### 📕 关于字体

![](/media/files/WEBP/tenmincho-fonts2.webp)*貂明朝字体*

#### 字体选型

Jekyll-ynewtime 主题的字体一直很难选择，需要兼顾的方面很多，在文章中一般会涉及中英文字体，而中文字体字库过于庞大，因此从网页加载速度的角度考虑，需要优先选用系统自建的字体。英文一般系统内置，选用的时候只要注意不同模块，如正文和导航栏、底部栏的区分即可，还有代码块的 monospace 字体选择，也是需要单拿出来考虑。

在设计原则上，我优先选用了开源的泛中日韩 Source Han 字体，这款字体优雅、大方，背后是[ Google 的大力支持和 Adobe 公司的精心研发](https://source.typekit.com/source-han-serif/cn/)，在字体的呈现效果上是非常理想的（serif，正文）。对于日文字体，我选择了由主持过思源字体开发的 Adobe 日本首席字体设计师 Ryoko Nishizuka（西塚涼子）所设计的[貂明朝](https://typekit.com/fonts/ten-mincho)字体（serif，正文），这款字体‘浓墨重彩’，在笔画勾绘的细节处传神生动，颇具‘貂’的意味。关于貂明朝字体，你可以在[ Fate/Typo 知名字体博客](https://fatetypo.xyz/ten-mincho/)上了解更多技术细节。代码块的字体则选择了 Github 上开源的混改版‘Consolas with Yahei’作为主要的字体集。除了主字体集的选用之外，兼顾不同系统字体的适配原则是：英文 > 中文; 系统自带 > 动态加载。

![](/media/files/WEBP/tenmincho-fonts1.webp)*貂明朝字体效果*

#### 方案确定

字体的选用根据上述逻辑，按衬体和非衬体分成了两个场景，并综合考虑了美观性、中文字体字库庞大的问题、日文字体兼容和网页动态渲染的延迟问题，最终确定了 font-family，其中，衬体（serif）的 font-family 如下：

```
$font-serif: 'Noto Serif CJK SC', 'Noto Serif CJK', "Source Han Serif SC", "source-han-serif-sc", "PingFang SC", "ten-mincho", "Source Han Serif", SimSun, "宋体";
```

上述衬体字体的顺序逻辑是：（1）优先选用 Noto 或 Source Han 的简体中文集（需要系统支持）；（2）如果系统中没有这两类字体，则尝试动态加载 Adobe 的 source-han-serif-sc 字体（需要配置 _config.yml）（3）若动态加载失败，对于 MacOS 系统，优先考虑系统自带的平方字体；（4）对于 Win 或 Android，则尝试动态加载 Adobe 的 ten-mincho 字体；（5）若上述全部加载失败，回落到宋体，或系统默认简体中文字体。

对于 Jekyll-ynewtime 主题，衬体主要应用在文章主体，即正文的显示中，包括但不限于文章标题，子标题，引用和强调。

非衬体（sans-serif）的 font-family 如下：

```
$font-sans: Consolas,Georgia,Helvetica,Tahoma,Arial,'Noto Sans CJK SC','Noto Sans CJK',"Source Han Sans","Source Han Sans SC","source-han-sans-sc","PingFang SC","Hiragino Sans GB",STXihei,"华文细黑","Microsoft YaHei","微软雅黑","文泉驿微米黑",Heiti,"黑体";
```

上述非衬线字体的顺序逻辑是，（1）优先考虑英文字体，如 Windows 的 consolas 和 mac 的 Helvetica；（2）中文字体优先选择 Noto sans 和 source han sans（同样，需要系统支持）；（3）若系统没有安装上述的思源字体，则对 mac 用户，优先考虑系统默认的苹方字体（新系统），老系统回落到华文细黑，对 win 用户优先选用 Microsoft Yahei，Linux 则回落到文泉驿微米黑；（4）若全部启用失败，回落到黑体。

对于 Jekyll-ynewtime 主题，非衬体的应用场景是：（1）顶部导航栏；（2）分隔符；（3）底部 footer。

### 📕 自动化图片/ Gif 压缩和整理脚本 file_to_webp.sh

考虑到先前网页加载时图片和 gif 所消耗的大量带宽，因此专门写了一个自动化脚本，对博客的图片和 gif 进行预处理，批量转化为 webp 或 webm 格式，并根据文件类型自动整理到对应的文件夹。

脚本功能描述：

> 每次呢，博客中添加一张新的图片（jpg 格式，png 格式都行），或者新的 GIF 啊  
都把它放在 media/files 这个文件夹里，然后呢  
在博客写完，要提交到远程仓库或者服务器之前  
只要进入 media/files/BATCH 文件夹里，用 wsl（win）或 terminal（Linux or mac）跑一遍 file_to_webp.sh  
就可以自动整理你放进来的所有类型的文件啦，所有文件会归类到命名好的文件夹里  
转换视频也是可以的，不过不推荐啦，所以脚本没有默认启用  
这个脚本的依赖主要有两个：FFmpeg（用来转换 gif 为 webm 格式）和 classifier（用来整理文件）  
因此，如果你的 Linux 环境里面没有这两个包，需要先安装，附安装方法：  
FFmpeg: `sudo apt install FFmpeg` （没错就是包管理器2333，Ubuntu大法好）  
classifier: `pip install classifier` （python环境需要你自己检查一下，python3是可以的）

### 📕 样式细节

详见 [DEMO](https://biki.ml) 
