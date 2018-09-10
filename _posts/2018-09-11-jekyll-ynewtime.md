---
layout: post
title: jekyll-ynewtime 主题介绍（1/3）
date: 2018-09-11
description: "jekyll-ynewtime 主题的使用入门 | DESIGNED BY Y"
tags:
 - jekyll
---

**jekyll-ynewtime** 是一款简约设计的博客模板（&copy;Y）。

## 安装

1、 [fork](https://github.com/Ynewtime/jekyll-ynewtime) 这个模板；

![](/media/files/forkme.png)

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

[![](/media/files/gakki.jpg)*ガッキーさんです*](/media/files/gakki.jpg)

```
![](/media/files/gakki.jpg)*ガッキーさんです*
```

并列图片：

<div class="responsive">
  <div class="img">
    <a href="/media/files/zhihu-1.jpg">
      <img src="/media/files/zhihu-1.jpg" alt="并列图片1">
    </a>
    <div class="desc">
      并列图片1
    </div>
  </div>
</div>

<div class="responsive">
  <div class="img">
    <a href="/media/files/zhihu-2.jpg">
      <img src="/media/files/zhihu-2.jpg" alt="并列图片2">
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
    <a href="/media/files/zhihu-1.jpg">
      <img src="/media/files/zhihu-1.jpg" alt="并列图片1">
    </a>
    <div class="desc">
      并列图片1
    </div>
  </div>
</div>

<div class="responsive">
  <div class="img">
    <a href="/media/files/zhihu-2.jpg">
      <img src="/media/files/zhihu-2.jpg" alt="并列图片2">
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

![](/media/files/google10.gif)

```
![](/media/files/google10.gif)
```

#### 响应式视频：

<div class="embed-responsive embed-responsive-16by9">
<video src="https://t1.aixinxi.net/o_1cclr3epb1cd539u1195tsj1n1ba.mp4" class="embed-responsive-item" controls="controls"></video>
</div>

```
<div class="embed-responsive embed-responsive-16by9">
<video src="https://t1.aixinxi.net/o_1cclr3epb1cd539u1195tsj1n1ba.mp4" class="embed-responsive-item" controls="controls"></video>
</div>
```

### 8、MathJax支持

$$ E = M C^2 $$

$$ z = \frac{x}{y} $$ 

```
$$ E = M C^2 $$

$$ z = \frac{x}{y} $$ 
```