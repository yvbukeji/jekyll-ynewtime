---
layout: post
title: jekyll-ynewtime 主题介绍（1/3）
date: 2018-09-11
description: "jekyll-ynewtime 主题的使用入门， DESIGNED BY Y"
tags:
 - jekyll
---

[jekyll-ynewtime](//github.com/Ynewtime/jekyll-ynewtime) 是一款简约设计的博客模板（&copy;Y）。

## 安装

1、 [fork](https://github.com/Ynewtime/jekyll-ynewtime) 这个模板；

![](/media/files/WEBP/forkme.webp)

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

## 特性

### 1、标题样式

# h1
## h2
### h3
#### h4

```
# h1
## h2
### h3
#### h4
```

### 2、分隔符样式

---

```
---
```

### 3、引用样式

> Q: Why is there never a bus when you want one?
A: Good question! There aren't enough buses on this road, sometimes...

```
> Q: Why is there never a bus when you want one?
A: Good question! There aren't enough buses on this road, sometimes...
```

### 4、代码样式

```json
{
    "fonts": {
        "SimSun": {
            "replace": "Microsoft YaHei UI",
            "#size": 0,
            "#width": 0,
            "#weight": 0,
            "#italic": false,
            "#underLine": false,
            "#strikeOut": false
        }
    },
    "debug": false
}
```

代码样式有两种解决方案，可以采用 jekyll 原生的 [highlight](https://jekyllrb.com/docs/liquid/tags/#code-snippet-highlighting) 方法，也可用传统的 markdown 代码高亮方法。

### 5、表格样式

| 特性 | 对比
|-|-
| 启动速度 | Sublime > VScode > Atom
| 插件体验 | VScode > Atom > Sublime
| 终端交互 | VScode > Sublime > Atom
| 运行内存 | Sublime > VScode > Atom

```
| 特性 | 对比
|-|-
| 启动速度 | Sublime > VScode > Atom
| 插件体验 | VScode > Atom > Sublime
| 终端交互 | VScode > Sublime > Atom
| 运行内存 | Sublime > VScode > Atom
```

### 6、图片样式

Markdown 单行图片：

![](/media/files/WEBP/gakki.webp)*ガッキーさんです*

```
![](/media/files/WEBP/gakki.webp)*ガッキーさんです*
```

UNSPLASH 随机图片：

<img src="https://source.unsplash.com/random" alt="UNSPLASH RANDOM PHOTO"><em>UNSPLASH RANDOM PHOTO</em>

```
<img src="https://source.unsplash.com/random" alt="UNSPLASH RANDOM PHOTO"><em>UNSPLASH RANDOM PHOTO</em>
```

并列图片：

<div class="responsive">
  <div class="img">
    <a href="/media/files/WEBP/zhihu-1.webp">
      <img src="/media/files/WEBP/zhihu-1.webp" alt="并列图片1">
    </a>
    <div class="desc">
      并列图片1
    </div>
  </div>
</div>

<div class="responsive">
  <div class="img">
    <a href="/media/files/WEBP/zhihu-2.webp">
      <img src="/media/files/WEBP/zhihu-2.webp" alt="并列图片2">
    </a>
    <div class="desc">
      并列图片2
    </div>
  </div>
</div>

<div class="clearfix"></div>

```html
<div class="responsive">
  <div class="img">
    <a href="/media/files/WEBP/zhihu-1.webp">
      <img src="/media/files/WEBP/zhihu-1.webp" alt="并列图片1">
    </a>
    <div class="desc">
      并列图片1
    </div>
  </div>
</div>

<div class="responsive">
  <div class="img">
    <a href="/media/files/WEBP/zhihu-2.webp">
      <img src="/media/files/WEBP/zhihu-2.webp" alt="并列图片2">
    </a>
    <div class="desc">
      并列图片2
    </div>
  </div>
</div>
<div class="clearfix"></div>
```

### 7. 多媒体嵌入

#### Gif：

![](/media/files/GIF/google10.gif)

```
![](/media/files/GIF/google10.gif)
```

#### 响应式视频：

<div class="embed-responsive embed-responsive-16by9">
<video src="/media/files/MP4/telegramX.mp4" class="embed-responsive-item" controls="controls"></video>
</div>

```
<div class="embed-responsive embed-responsive-16by9">
<video src="/media/files/MP4/telegramX.mp4" class="embed-responsive-item" controls="controls"></video>
</div>
```

### 8、MathJax支持

$$ E = M C^2 $$

$$ z = \frac{x}{y} $$ 

```
$$ E = M C^2 $$
$$ z = \frac{x}{y} $$ 
```

### 9、字体设计

参考 [Jekyll-ynewtime 中日英字体网页混排实践](/JCKfonts)

### 10、自动化脚本

参考[图片压缩和分类整理脚本](/ImgToWebp)