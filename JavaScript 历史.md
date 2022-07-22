# Javascript

## 历史

- 发明人: 布兰登(网景->firefox->brave)
- 诞生: 95 网景公司
- 标准指定: 96 ECMAScript
- 开源: 98 Firefox 开源 99 年 ES3
- 火爆: Chrome 08 诞生(js 引擎 V8)

  09 年 ES5 09 年 Node.js

  10 年 npm

  15 年 ES6

  Chrome 16 年 份额 62%

## 设计思路[1]

1. 借鉴 C 语言的基本语法
2. 借鉴 Java 语言的数据类型和内存管理
3. 借鉴 Scheme 语言，将函数提升到"第一等公民"（first class）的地位
4. 借鉴 Self 语言，使用基于原型（prototype）的继承机制

[1] [阮一峰网络日志](http://www.ruanyifeng.com/blog/2011/06/birth_of_javascript.html)

## 浏览器提供的功能

(以进程形式)Chrome 主进程,插件进程,网络服务以及 Tab 标签子进程

(以线程形式)用户界面, 渲染引擎, js 引擎(编译,优化,执行,垃圾回收), 存储

window / document / setTimeout

window

1. console
2. Object
   > 首字母大写的一般有 prototype
3. Array

## 内存

1. 不知道什么区
   > 存放变量名
2. stack
   > 栈,存放非对象
3. heap
   > 堆,存放对象

## 原型链
