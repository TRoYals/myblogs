---
author: TRoYals
authorEmail: aozora00321@gmail.com
authorLink: Naglfar28.com
categories:
  - workflow
comment: true
date: "2023-03-14T23:01:13+08:00"
draft: false
hiddenFromHomePage: true
hiddenFromSearch: false
tags:
  - tools
title: obsidian_to_hugo workflow
---

# 基于 obsidian 与 hugo 的 obsidian 博客工作流

> 其实内容还是比较简单的，这里写的话主要是做一个记录。

## obsidian

### 下载 pandoc 导出插件

社区插件中下载，能将 md 格式导出为支持 hugo 的 markdown 格式。
选择 hugo 中的**post/** 文件夹作为默认导出位置，十分方便。

### templatr 生成模版

这里主要是根据 hugo 的默认的 metadata 来调整模版，一个例子
![](https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/202303142306361.png)

想在 ob 中写 blog 直接导入就可以了，很快捷。

## hugo

导入后 git 同步就可以了。
