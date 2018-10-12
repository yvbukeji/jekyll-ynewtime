---
title: 图片压缩和分类整理脚本
date: 2018-09-14
layout: post
description: 一个自动化脚本，对博客的图片和 gif 进行预处理，批量转化为 webp 或 gif 格式，并根据文件类型自动整理到对应的文件夹。
tags:
 - 脚本
 - 教程
 - notes
---

**2018-09-27** 更新：由于 webp 格式在 Microsoft Edge 和 iOS 的支持问题尚未妥善解决，暂时将 webp 回退到 jpg 格式，不过由于目前将博客内的主要媒体资源都托管到了腾讯云 COS，对比原先的 github 仓库托管方案还是要快的。

<!--more-->

## 图片压缩

考虑到先前网页加载时图片和 gif 所消耗的大量带宽，因此专门写了一个自动化脚本，对博客的图片和 gif 进行预处理，批量转化为 webp 或 webm 格式，并根据文件类型自动整理到对应的文件夹。

来看看压缩了 75% 的 jpg 格式和 webp 格式对比：

[![](/media/files/WEBP/gakki.webp)](/media/files/WEBP/gakki.webp)

[![](/media/files/JPG/gakki.jpg)](/media/files/JPG/gakki.jpg)

那么问题来了，哪个是压缩后的图片呢？你可以点击图片查看，震惊有没有？？由于图片都做了压缩处理，这样一来，网页的加载自然也就更快了。

## 分类整理

脚本功能描述：

每次呢，博客中添加一张新的图片（jpg 格式，png 格式都行），或者新的 GIF 啊，都把它放在 media/files/NEW 这个文件夹里。然后呢，在博客写完、要提交到远程仓库或者服务器之前，只要进入 media/files/BATCH 文件夹里，用 wsl（win）或 terminal（Linux or mac）跑一遍 file_to_webp.sh，就可以自动整理你放进来的所有类型的文件啦。所有文件会归类到命名好的文件夹里。转换视频也是可以的，不过不推荐啦，所以脚本没有默认启用。这个脚本的依赖主要有三个：cwbep（转换 jpg/png 格式为 webp 格式）、FFmpeg（用来转换 gif 为 webm 格式）和 classifier（用来整理文件）。因此，如果你的 Linux 环境里面没有这两个包，需要先安装，附安装方法：  

```
sudo apt install cwebp FFmpeg（没错就是包管理器2333，Ubuntu大法好）  
pip install classifier（python环境需要你自己检查一下，python3是可以的）
```

当然，这个脚本非常简单，只是提供了一个便携的功能而已，你完全可以根据自己的情况定制和衍生。

```bash
#!/bin/bash
#==================================#
# Name: file_to_webp.sh
# Ahthor: Stephen Tseng
# Last Update Date: 2018-09-13
# Script for: Convert png or jpg to webp, gif to webm, and mp4 to webm.
#             And put them into classified dir
# Prerequests: FFmpeg(install with apt), Classifier(install with pip)
# For blog users:
# Put your images(.jpg,.png), .gif, and .mp4 all under dir:media/files
# Then run commands `./file_to_webp.sh`
# 
# 中文表述一下：
# 每次呢，博客中添加一张新的图片（jpg 格式，png 格式都行），或者新的 GIF 啊
# 都把它放在 media/files/NEW 这个文件夹里，然后呢
# 在博客写完，要提交到远程仓库或者服务器之前
# 只要进入 media/files/BATCH 文件夹里，用 wsl 跑一遍 file_to_webp.sh
# 就可以自动整理你放进来的所有类型的文件啦，所有文件会归类到命名好的文件夹里
# 这个脚本的依赖主要有两个：cwbep（转换 jpg/png 格式为 webp 格式）、FFmpeg（用来转换 gif 为 webm 格式）和 classifier（用来整理文件）
# 因此，如果你的 Linux 环境里面没有这三个包，需要先安装，附安装方法：
# FFmpeg: `sudo apt install cwebp FFmpeg` （没错就是包管理器2333，Ubuntu大法好）
# classifier: `pip install classifier` （python环境需要你自己检查一下，python3是可以的）
#==================================#

# for me, I am using miniconda as a python environment admin
# so I have to change to the environment first
source activate Y
# Change to dir ../
cd ..
# Set convert dir and output dir
SOURCE_DIR=NEW
OUTPUT_DIR=./
# If image size > 1KB, convert to webp.
SIZE=1024
# Set convert quality 50.
QUALITY=50
# Convert image to webp:
FILE_LIST=`find $SOURCE_DIR | egrep "^*\.(png|jpg|JPG|jpeg)$"`
for file_name in $FILE_LIST
do
    file_size=`ls -l $file_name | awk '{ print $5 }'`
    if [ $file_size -gt $SIZE ]; then
        new_file_name=${file_name%.*}
        cwebp -q $QUALITY $file_name -o $new_file_name.webp
    fi
done
# Convert animated gif to webm:
# find "$SOURCE_DIR" -name '*.gif' -exec sh -c 'ffmpeg -i "$0" "${0%%.gif}.webm"' {} \;
# Convert videos to webm:
# find "$SOURCE_DIR" -name '*.mp4' -exec sh -c 'ffmpeg -i "$0" -c:v libvpx -crf 10 -b:v 1M -c:a libvorbis "${0%%.mp4}.webm"' {} \;

# Classify the files by types in the same folder:
# run `pip install classifier` before you can use it directly
classifier -st jpg -sf "JPG" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"
classifier -st png -sf "PNG" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"
classifier -st gif -sf "GIF" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"
classifier -st mp4 -sf "MP4" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"
classifier -st webp -sf "WEBP" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"
classifier -st webm -sf "WEBM" -d "$SOURCE_DIR" -o "$OUTPUT_DIR"

# 补充：
# 转化 webp 为 jpg 格式的命令：
# ls -1 *.webp | xargs -n 1 bash -c 'dwebp "$0" "${0%.webp}.jpg"'
# 转化 webp 为 png 格式的命令：
# ls -1 *.webp | xargs -n 1 bash -c 'dwebp "$0" "${0%.webp}.png"'
```