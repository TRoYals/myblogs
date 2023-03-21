---
author: TRoYals
authorEmail: aozora00321@gmail.com
authorLink: Naglfar28.com
cards-deck: JavaScript
categories:
- draft
comment: true
date: "2023-03-21T21:46:42+08:00"
draft: true
hiddenFromHomePage: true
hiddenFromSearch: false
tags:
- draft
title: JavaScript面试
---

## Map \#card

- new Map() ---创建map
- map.set(key,value)---根据键存储值
- map.get(key) returns the value by the key. return *undefined* if key doesn't exists
- map.has(key) returns true if key exists, false otherwise
- map.delete(key) remove elements by key
- map.clear() removes everything
- **map.size** returns the current element count.
  \^1679408153211

1.  使用object作为map的key会发生什么

``` js
let john = { name: "John" };
let visitsCountObj = {}; // try to use an object
visitsCountObj[john] = 123; 
```

\#card

``` js
let john = { name: "John" };
let ben = { name: "Ben" };
let visitsCountObj = {}; // try to use an object
visitsCountObj[ben] = 234; // try to use ben object as the key
console.log(visitsCountObj);//{ '[object Object]': 234 }
visitsCountObj[john] = 123;
console.log(visitsCountObj);//{ '[object Object]': 123 }
```

Objects can be used as a key!
\^1679408869940

2.  map的链式调用 \#card
    每一次map.set的调用会返回本身，我们可以进行链式调用

``` js
map.set('1', 'str1') .set(1, 'num1') .set(true, 'bool1');
```

\^1679408869956

### map interationsn \#card

- map.keys() -returns an iterable for keys
- map.values() -returns an iterable for values
- map.entries() -return an iterable for entries \[key,value\], it's used by default in for ... of

## Promise

1.  Promise中then的调用
    用一个例子来搞懂，把这个记住应该就没问题了

``` js
const p = new Promise((resolve, reject) => {
console.log("a");
resolve();
console.log("b");
});
setTimeout(() => console.log("c"), 0);
p.then(console.log("d"));
p.then(() => console.log("e"));
console.log("f");
```

问输出顺序？ \#card
答案：**abdfec**
要注意的点
- 可以把p.then(()=\>XXX）看作一个setTimeout(()=\>XXX,0)，它是异步调用回调函数的。并且\*\*优先级高于setTimeout(()=\>XXX,0)
- 其他的没什么好注意的了
\^1679408153220

2.  加载脚本Promise改写

## 浏览器

### 加载文档
