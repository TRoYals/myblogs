# JavaScript面试（基础）


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
  \^1679435632847

3.  Map.forEach用法 \#card

``` js
let recipeMap = new Map([ ['cucumber', 500], ['tomatoes', 350], ['onion', 50] ]);
^1679435632870

// runs the function for each (key, value) pair 
recipeMap.forEach( (value, key, map) => { alert(`${key}: ${value}`); // cucumber: 500 etc });
```

### object from map

4.  how to create a map from object \#card
    use **Object.entries(obj)**

``` js
let obj = { name: "John", age: 30 };
let map = new Map(Object.entries(obj));
alert( map.get('name') ); // John
```

\^1679436804602

5.  how to create a object from a map \#card
    use **Object.fromEntries**

``` js
let map = new Map();
map.set('banana', 1);
map.set('orange', 2); 
map.set('meat', 4); 
let obj = Object.fromEntries(map.entries()); // make a plain object (*)_ // done! // obj = { banana: 1, orange: 2, meat: 4 } alert(obj.orange); // 2
let obj = Object.fromEntries(map);//the same with previous one
```

\^1679436804609

## Set

1.  the basic methods of Set. \#card
    most are the same with **Map**

- new Set(\[iterable\])
- set.add(value)
- set.has(value)
- set.delete(value)
- set.size
- set.clear
- map.set(key,value)
  \^1679436804613

2.  interation over Set.
    set.keys() set.values()(same with set.keys) and set.entries() (returns \[value,value\]). 　
    　
3.  把set转换为数组进行数组操作 　#card
    *let keys = Array.from(map.keys());*　
    　　
    　

## Variable Scope, Closure

### code blocks

the variable declared inside a code block {}, it's only visible inside that block.
\### Lexical Environment
1. variable declares　
<img src="http://oss.naglfar28.com/naglfar28/202303220647792.png"/>
2. function declarations
when a lexical environment is created, a function Declaration immediately created( that is the reson why we can use a function even before the declaration)
3. Inner and Outer Lexical Environment
4. returning a function
感觉弄的有点麻烦了，实际上只要把下面这个例子记清楚就可以了。

``` js
console.log(test);
console.log(fn1);
var test = 25;
function fn1(){
console.log(test);
}
function fn2(){
var test =35;
fn1();
}
fn2();
```

\#card
　`js 　outpus: 　undefined 　f fn1(){ 　XX} 　25`
前面两个输出是变量声明和函数声明的对比，后面之所以输出25.简要逻辑如下： fn2()中调用fn1()，而fn1()在全局变量声明中，找到fn1()后，fn1()找最近的test，最近的test就是25（全局中）
**注意这里的变量是用VAR声明的，只有VAR声明的变量如此，LET声明的变量建议自己去试试**
\^1679440647772

### Sample Question

1.  看看下面这个代码。最后一行代码的执行结果是什么？[](https://zh.javascript.info/closure# "运行")

``` js
let phrase = "Hello"; 
if (true) { let user = "John";
function sayHi() { alert(`${phrase}, ${user}`); } 
          } 
sayHi();
```

\#card
答案:error ，在if中声明的函数也不会被声明。
\^1679441518547

2.  编写一个像 `sum(a)(b) = a+b` 这样工作的 `sum` 函数。
    是的，就是这种通过双括号的方式（并不是错误）。 \#card

``` js
function sum(a) {
function sumb(b) {
return a + b;
}
return sumb;
}
```

\^1679441529984
　
3. 下面的代码输出什么？如果条件中var x=2 换成let x = 2 呢

``` js
let x = 1;
function func() {
console.log(x); // ReferenceError: Cannot access 'x' before initialization
var x = 2;//如果换成let x = 2 呢
}
func();
```

\#card
输出 undifined. 如果换成 let则输出 **error**
\^1679444622106

4.  通过函数筛选<img src="http://oss.naglfar28.com/naglfar28/202303220743983.png"/> \#card 　

``` js
function inBetween(a, b) {
function input(number) {
if (a <= number && b >= number) return 1;
else return 0;
}
return input;
}
function inArray(arr) {
function input(number) {
if (number in arr) return 1;
else return 0;
}
return input;
}
console.log(arr.filter(inBetween(3, 6)));
console.log(arr.filter(inArray([1, 2, 10])));
```

5.  <img src="http://oss.naglfar28.com/naglfar28/202303220811169.png"/>　
    \#card

``` js
function byField(field) {
function compare(a, b) {
return a.field > b.field ? 1 : -1;
}
return compare;
}
```

\^1679444622116

6.  函数大军　
    <img src="http://oss.naglfar28.com/naglfar28/202303220815470.png"/>
    \#card
    用for循环，或者在while循环里声明i（因为每次while循环都会创造新的词法环境，新的函数要去while循环外的词法环境找i
    \^1679444622120
    　
    　

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
2. 加载脚本Promise改写

## 浏览器

### 加载文档


---

> Author: [TRoYals](https://naglfar28.com)  
> URL: https://naglfar28.com/javascript%E9%9D%A2%E8%AF%95%E5%88%B7%E9%A2%98%E5%9F%BA%E7%A1%80/  

