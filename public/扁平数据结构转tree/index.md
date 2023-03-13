# 扁平结构转Tree


# 引子

在掘金上看到了这篇文章，感觉还蛮有意思的，试试看能不能解决。
[面试了十几个高级前端，竟然连（扁平数据结构转 Tree）都写不出来 - 掘金](https://juejin.cn/post/6983904373508145189)

输入：

```js
let arr = [
  { id: 1, name: "部门1", pid: 0 },
  { id: 2, name: "部门2", pid: 1 },
  { id: 3, name: "部门3", pid: 1 },
  { id: 4, name: "部门4", pid: 3 },
  { id: 5, name: "部门5", pid: 4 },
];
```

输出：

    [
    {
    "id": 1,
    "name": "部门1",
    "pid": 0,
    "children": [
    {
    "id": 2,
    "name": "部门2",
    "pid": 1,
    "children": []
    },
    {
    "id": 3,
    "name": "部门3",
    "pid": 1,
    "children": [
    ]}]}
    ]

# 解决

## 思路 1

循环每一个 id，然后对每一个 id 查找 pid，复杂度 O($N^2$)

这样可以吗？ 答案是不行的，要注意，这里每一个 parent 节点是可以有多个子节点的，子节点又是可以作为新的父母节点的。

在进一步思考这个问题前，回忆 **深拷贝**的代码

```js
function clone(o) {
  var temp = {};
  for (var key in o) {
    if (typeof o[key] == "object") {
      temp[key] = clone(o[key]);
    } else {
      temp[key] = o[key];
    }
  }
  return temp;
}
```

我们不难发现，这道题的 本质就是深拷贝！！
只不过需要将深拷贝中的 if 判断换成寻找 pid。
搞清楚这个后，代码就很容易写出来了。

```js

```


---

> Author: [TRoYals](https://naglfar28.com)  
> URL: https://naglfar28.com/%E6%89%81%E5%B9%B3%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E8%BD%ACtree/  

