## 概念

多数情况下，this 指向调用它所在`方法`的那个`对象`。

解释： 谁调的函数，this 就指向谁。如果没有指定谁调用，就指向全局对象。严格模式下指向`undefined`

> `this`是在调用时决定的；`闭包`是在书写时决定的。

### 核心

不管方法被书写在哪个位置，它的 this 只会跟着它的调用方走

### 特殊情境

好消息！在三种特殊情境下，this 会 100% 指向 window：

- 立即执行函数（IIFE）
- setTimeout 中传入的函数
- setInterval 中传入的函数

setTimeout 和 setInterval 以及里面的函数，都会首先被交付到全局对象手上

## 严格模式

#### 普通函数中

普通函数是指函数声明或者函数表达式的函数。

在非严格模式下，this 会指向全局变量（window 或 global）

严格模式下，如果没有指定对象，this 就是 undefined

#### 全局代码中

即在 `全局作用域` 下执行的函数或代码段里的 this。

不管它是否处于严格模式下，它的 this 都指向全局变量。

```js
// 全局打印
console.log(this);

// 全局作用域下实现的延时函数
setTimeout(function () {
  console.log(`你好，我是${this.name}`);
});
```

经过试验，所有的高阶函数中，this 指向的都是全局对象。

如：`Array.prototype.map`，`Array.prototype.filter`，`Array.prototype.reduce`，

## 箭头函数

- 和严格模式无关
- 类似闭包，认词法作用域
- 绑定到书写时的父作用域

指向它声明时的作用域，与调用无关
