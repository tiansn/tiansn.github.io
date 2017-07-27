---
layout: post
title:  "javascript类数组转化成数组的几种方法"
date:   2017-07-20
comments: true
tag:
- arguments
- 类数组
---

![类数组转数组](https://raw.githubusercontent.com/tiansn/tiansn.github.io/master/assets/img/themes/array.jpg)

这里说的类数组是类似数组的对象，比如函数的参数`arguments`,比如`document.getElementsByTagName('p')`返回的对象，这些对象像数组，但是属性里只有length,没有数组的其他方法。

下面用arguments举例，看怎么转换的

## 使用Array.prototype.slice.call(arguments)
这种方法是低版本的浏览器也可以兼容的
```
var args = Array.prototype.slice.call(arguments); 

var args = [].slice.call(arguments);
```

## 使用Array.from()
```
let args = Array.from(arguments);
```

## 使用spread运算符...
```
let args = [...arguments];
```

## 使用Array.apply(null, arguments)
>对参数使用slice会阻止某些JavaScript引擎中的优化 (比如 V8 引擎)。

如果你关心它们，尝试通过遍历arguments对象来构造一个新的数组。

另一种方法是使用 被忽视的/鄙视/轻视,/看不起 Array构造函数作为一个函数：
```
let args = (
arguments.length === 1 ? 
[arguments[0]] : 
Array.apply(null, arguments)
);
```

## 使用Array.slice(arguments)
如果 Array generics 可用的话，下面的代码也可以:
```
var args = Array.slice(arguments);
```

