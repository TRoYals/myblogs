---
title: "React+TS+Solidity+NftMarket"
subtitle: ""
date: 2023-02-20T10:11:44+08:00
draft: false
author: "TRoYals"
authorLink: "Naglfar28.com"
authorEmail: "aozora00321@gmail.com"
description: ""
keywords: ""
license: ""
comment: true
weight: 0

tags:
  - draft
categories:
  - draft

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
  enable: false
lightgallery: false
seo:
  images: []

repost:
  enable: true
  url: ""
# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

## strat the project

npx create-next-app nft-marketplace --typescript

Use the tailwind

Install Tailwind CSS with Next.js - Tailwind CSS: https://tailwindcss.com/docs/guides/nextjs

## Web3 Provider

```
npm install ethers @metamask/providers
```

A Provider is an abstraction of a connection to the Ethereum network, providing a concise, consistent interface to standard Ethereum node functionality.

- [Providers](https://docs.ethers.org/v5/api/providers/)

提供钱包接口服务

[Getting Started](https://docs.ethers.org/v5/getting-started/)

## Ganache Truffle

本地部署以太网

把这个看一遍基本就明白了
[Truffle quickstart - Truffle Suite](https://trufflesuite.com/docs/truffle/quickstart/)

```
npm install @openzeppelin/contracts

```
