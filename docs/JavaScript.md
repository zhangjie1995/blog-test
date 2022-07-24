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

## 基本语法

### 表达式和语句

```javascript
while(expression){
    statement1
    statement2
    ...
}
```

语句(statement): 带有目的的操作,i.e, 赋值语句,while 语句...

表达式(expression): 为了得到返回值的计算式

### 标识符(identifier)

规则:

1. 字母(unicode 字母,包括中文),数字,$,下划线(\_)
2. 首字符不能是数字
3. 不能使用保留字

### if-else 语句

```javascript
if (expression) {
  statement;
} else if (expression){
    ...
} else {
    ...
}
```

当花括号内只有一句语句时,可以省略花括号(但不建议)

### while/for 语句

```javascript
while (expression) {
  statement;
}
```

for 语句时 while 语句的语法糖,将初始化+判断条件+递增表达式整合,可以不写,但;不能省略.

```javascript
for (let i = 0; i < 2; i++) {
  statement;
}
```

break

> 跳出当前循环

continue

> 跳出当前循环的这一次,继续执行当前循环的下一次

label

> 定位符,可以让 break 跳出两层循环

```javascript
foo:
for(int i=0; i<30; i++){
    for (int j = 0; j< 30; j++){
        if(i=3) break foo;
    }
}
```

### 替代 if 的几种方式

```javascript
if (a > b) {
  statement1;
} else {
  statement2;
}
```

1. 三元运算符

```javascript
a > b ? statement1 : statement2;
```

2. &&

```javascript
a > b && statement1;
!(a > b) && statement2;
```

3. ||

```javascript
a > b || statement2;
!(a > b) || statement1;
```
## object

### 定义

- 无序数据集合
- 数据是键值对(key-value),且键为字符串/Symbol
- Object.keys(obj) 可得到 obj 对象的所有键的数组

定义方法:

1. `var obj = {}`
2. `var obj = new Object({})`
3. `console.log({})`

键命名时省略引号容易出错的地方

1. 数字

```javascript
var obj = {
  1e1: "科学计数",
  .3: "小数",
  0xff: "十六进制",
};
Object.keys(obj) //['10', '255', '0.3'] 


1e1.toString(); //'10'
.3.toString();//'0.3'
0xff.toString(); //'255'
```

2. 变量名

### CRUD

#### D
 