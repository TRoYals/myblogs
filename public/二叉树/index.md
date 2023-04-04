# 二叉树


## 二叉树递归遍历

略
## 二叉树迭代法遍历
二叉树 前序迭代遍历
\#card
1. 定义一个栈和一个指针cur，初始时cur指向根节点，栈为空。
2. 当cur不为空或者栈不为空时，进行循环：
a. 访问cur节点并将其入栈，然后将cur指向其左子节点。
b. 如果cur为空，弹出栈顶节点node并将cur指向node的右子节点。
3. 循环结束后，所有节点均已遍历完毕。

``` js
var preorderTraversal = function(root) {
let cur = root ;
let stack = [];
let res = [];
while(stack.length||cur){
if(cur){
stack.push(cur)
res.push(cur.val);
cur = cur.left;
}else{
let temp = stack.pop();
cur = temp.right;
}
}
return res
};
```

<br>
二叉树 中序迭代遍历
\#card

1. 定义一个栈和一个指针cur，初始时cur指向根节点，栈为空。
2. 当cur不为空或者栈不为空时，进行循环：
a. 如果cur不为空，将cur入栈，然后将cur指向其左子节点，重复此操作直到cur为空。
b. 如果cur为空，弹出栈顶节点node并访问它，然后将cur指向node的右子节点。
3. 循环结束后，所有节点均已遍历完毕。

``` js
let stack = [];
stack.push(root)
let cur = root;
let res = [];
while(cur || stack.length){
if(cur.left) {
stack.push(cur.left)
cur = cur.left
}else{
let temp = stack.pop();
res.push(temp.val);
cur = temp.right
}
}
return res
```

<br>

二叉树后序迭代遍历
\#card

1. 定义一个空栈 `stack` 和一个空数组 `res`，以及一个指针 `cur` 和一个指针 `pre`，其中 `cur` 初始指向根节点 `root`，`pre` 初始值为 `null`。
2. 当 `cur` 不为空或栈不为空时，循环执行以下操作：
a. 如果 `cur` 不为空，将 `cur` 压入栈中，然后将 `cur` 指向其左子节点或右子节点，优先遍历左子树。如果 `cur` 既没有左子节点也没有右子节点，则将 `cur` 置为空。
b. 如果 `cur` 为空，则从栈中查询栈顶元素（不是弹出） `node`，判断该元素的右子节点是否存在且没有被遍历过，如果是，则将 `cur` 指向它的右子节点；否则，将该元素的值加入到结果数组 `res` 中，然后将 `pre` 指向该元素，同时将该元素从栈中弹出。
3. 循环结束后，返回结果数组 `res`。

``` js
var postorderTraversal = function(root) {
let stack = [];
let cur = root;
let res = [];
let pre = null
while(cur || stack.length){
if(cur){
stack.push(cur)
cur = cur.left||cur.right;
}else{
let node = stack[stack.length-1];;
if(node.right && node.right !==pre ){
cur = node.right
}else{
res.push(node.val)
pre = node;
stack.pop()
}
}
}
return res
};
```

## 二叉树层序遍历

\#card
1. 首先创建了一个空数组 `res` 和一个空队列 `queue`，将根节点添加到队列中。如果根节点为空，则直接返回空数组 `res`。
2. 接下来，代码进入一个 while 循环，该循环在队列不为空时一直执行。在循环中，首先获取当前队列的长度，并创建一个空数组 `curLevel` 用于存储当前层级的节点值。
3. 然后，代码在 for 循环中遍历队列中的节点，并将节点的值添加到 `curLevel` 数组中。如果节点有左子节点，则将其左子节点添加到队列中；如果节点有右子节点，则将其右子节点添加到队列中。for 循环结束后，将 `curLevel` 数组添加到 `res` 数组中，表示当前层级的节点遍历完毕。
4. 最后，当队列为空时，while 循环结束，代码返回 `res` 数组，其中包含了每个节点所在的层级及其值。　

``` js
var levelOrder = function(root) {
let res = [], queue= [];
queue.push(root)
if(root === null){
return res;
}
while(queue.length){
let length = queue.length;\\这一步很关键，因为在之后的操作中queue的长度会发生变化！！
let curLevel = [];
for(let i = 0;i<length;i++){
let node = queue.shift()
curLevel.push(node.val)
node.left && queue.push(node.left)
node.right && queue.push(node.right)
}
res.push(curLevel)
}
return res
};
```

同样的模型还可以求最长二叉树/最小 etc

## 翻转二叉树

``` js
var invertTree = function(root) {
let res =[],queue = [];
if(root ==null)return root
queue.push(root)
while(queue.length){
let length = queue.length;
for(let i =0;i<length;i++){
let node = queue.shift();
let temp =node.right;
node.right = node.left;
node.left = temp;
node.left && queue.push(node.left)
node.right && queue.push(node.right)
}
}
return root
};
```


---

> Author: [TRoYals](https://naglfar28.com)  
> URL: https://naglfar28.com/%E4%BA%8C%E5%8F%89%E6%A0%91/  

