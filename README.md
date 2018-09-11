# 📌 jekyll-ynewtime

基于 Jekyll 的一个开源主题。示例见：[DEMO](https://biki.ynewtime.com/)

![](/media/files/intro-1.png)

👆 首页

![](/media/files/intro-2.png)

👆 归档页

![](/media/files/intro-3.png)

👆 标签页

![](/media/files/intro-4.png)

👆 介绍页

## 安装

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

## 更多特性

见 [DEMO](https://biki.ynewtime.com) 