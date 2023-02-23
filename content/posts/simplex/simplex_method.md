---
title: "Simplex_method"
subtitle: ""
date: 2023-02-20T21:24:46+08:00
draft: true
author: "TRoYals"
authorLink: "Naglfar28.com"
authorEmail: "aozora00321@gmail.com"
description: ""
keywords: ""
license: ""
comment: true
weight: 0

tags:
  - algorithem
categories:
  - math

hiddenFromHomePage: true
hiddenFromSearch: false

summary: ""
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg

toc:
  enable: true
math:
  enable: true
lightgallery: false
seo:
  images: []

repost:
  enable: true
  url: ""
# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

## 前言

上学期选了 MA4254，课程的后半节要求用 simplex 算法，当时没学过，于是刷了不少题来应付考试，然后这学期 MA3252 的时候又遇到了 Simplex，结果上学期刷的题忘的一干二净了。。。虽然简单复习了一下后还是想起来了，但是毫无疑问，这个知识我学的并不扎实，于是有了这篇 blog，准备查缺补漏，算是自己的一个笔记吧。

## Special Case of Simplex

先从特殊的 simplex 谈起吧（因为这篇 blog 就是因为没有算出一个特例而写的）

### Degeneracy

A BFS with one or more zero basic vairiables is degenerate.

- A tie in the minimum ratio test leads to degeneracy.
- Degeneracy reveals that model has at least one redundant constraint at that BFS (which may not affect later BFS).
  简单来说就是，就是 BFS 中至少有一个 0，这样的现象说明，对于当前的 BFS，存在着多余的限制。

#### Degenerate Case

1. case 1
   <img src="https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/20230220214205.png"/>
   在这个例子中，第二次迭代的时候出现了，$X_4=0$，但是并未对下一次迭代产生影响，并且在第二次迭代时已经找到了最优解。

2. case 2

   下一个例子说明，出现退化时，不一定找到了最优解。
   <img src="https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/20230220214712.png"/>
   <img src="https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/20230220214750.png"/>
   在这个例子中，第三次迭代时出现了退化，但此时并没有取到最优解。

3. case 3

   出现退化会出现什么不好的影响呢，答案是退化可能会导致循环(cycling)的情况,下面的这个例子说明了这点
   <img src="https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/20230220215028.png"/>
   <img src="https://naglfar28.oss-ap-southeast-1.aliyuncs.com/naglfar28/20230220215039.png"/>

#### Bland's anticycling rule

笔者就是遇到了 cycling 没解出来破防才写下了这篇文章。。
这里简单介绍一下**Bland 规则**:

{{< admonition type=tip title="Bland's anticycling rule" open=false >}}

1. Choose the lowest-numbered (i.e., leftmost) nonbasic column with a negative (reduced) cost.
2. Now among the rows, choose the one with the lowest ratio between the (transformed) right hand side and the coefficient in the pivot tableau where the coefficient is greater than zero. If the minimum ratio is shared by several rows, choose the row with the lowest-numbered column (variable) basic in it.
   {{< /admonition >}}

   替入变量：目标条件中，系数为负数的第一个作为替入变量

   替出变量：对所有的约束条件中，选择对约束最紧的第一个（但不为 0）

   <br/>
   这样，在原来的例子中，第一次选的替入变量应为$X_1$，替出变量应为$X_7$

### Alteranative Optima

在 LP 中，可能会出现多个最优解

### Unbounded Solution

### Infeasibility

线性规划-单纯形算法详解 | 细语呢喃
https://www.hrwhisper.me/introduction-to-simplex-algorithm/#valine-comments
