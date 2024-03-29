# Javascript
## 由来
### 历史

- 发明人: 布兰登(网景->firefox->brave)
- 诞生: 95 网景公司
- 标准指定: 96 ECMAScript
- 开源: 98 Firefox 开源 99 年 ES3
- 火爆: Chrome 08 诞生(js 引擎 V8)

  09 年 ES5 09 年 Node.js

  10 年 npm

  15 年 ES6

  Chrome 16 年 份额 62%

### 设计思路[1]

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

## 原型

原型存储对象的共有属性

对象的[__proto__]属性存储原型地址

所有对象都有原型,根对象的原型地址为null

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

#### delete
```javascript
delete obj['name']
delete obj.name //以上两种方式等价
delete obj[name]
'name' in obj // false
obj.name === undefined //不能用这种方式来判断属性是否存在
```
#### read
```javascript
Object.keys(obj)
Object.values(obj)
Object.entries(obj)
console.dir(obj)

//判断属性是否为自身属性
'name' in obj //当该属性是共有属性时或自身属性时返回true
obj.hasOwnProperty('name')//当该属性为自身属性时返回true

```

#### update-create

1. 直接赋值
2. 批量赋值

`Object.assign(obj,{p1:1,p2:2})`

3. 修改原型
```javascript
var obj = {name: 'zhangsan'};
var obj1 = {};
obj1.__proto__ = obj;//方式1
var obj1 = Object.create(obj);//方式2
//构造函数  ~待完整~
```




### new关键词的作用
```javascript
//为了节省内存,将相似对象的共有属性抽离,写进一个新的对象
//新建对象时,使用构造函数将新对象__proto__指向共有属性对象
function createSquare(width){
  let obj = Object.create(createSquare.prototype)
  obj.width = width
  return obj
}
createSquare.prototype = {
  getArea(){
    return this.width * this.width
  },
  constructor: createSquare
}
let obj = createSquare(3)// 'getArea' in obj -> true
</hr>
//使用new关键词可用简化以上步骤
function Square(width){
  this.width = width
}
//此时若直接赋对象会覆盖Square.prototype的其他属性比如constructor
Square.prototype.getArea = function(){
  return this.width * this.width
}
let obj1 = new Square(3)

```

总结 new X()所做的事情

1. 创建对象
2. 新对象原型指向X.prototype
3. 新对象作传进X()函数,形参为this,并使用构造函数为新对象添加自身属性
4. 返回this

> 对象.__proto__ === 构造函数.prototype



## 数组对象

### 定义

```javascript
let arr = [1,2]
let arr1 = new Array(1,2)
let arr2 = new Array(3)
```
### 其他对象转换成数组 
```javascript
let str = '1,2,3';
str.split(',')
Array.from('123')//类数组对象 下标+length
```
### 自身属性
```javascript
Array.keys(arr) //['0','1','length']
```

### Array.prototype的属性

1. shift/unshift
2. push/pop
3. join(',')
4. concat(obj)
5. slice(startIndex,[endIndex])

### CRUD
```javascript
//delete
delete arr[0]//length不变,下标不变
arr.length = 0//全部元素删除
arr.shift()//length+下标 变化 pop
arr.splice(start,[deleteCount],[addItems])
//遍历
//方式1
for(let i=0; i<arr.length; i++){
  console.log(arr[i])
}
//方式2
arr.forEach((value,index)=>{
  console.log(`${index}:${value}`)// 0:1  1:2 2:3
})
//查询

arr.indexOf(value)//返回value值的下标,没有返回-1
arr.find((x)=>{
  return x%2 == 0 //返回第一个偶数值
})
arr.findIndex

// update
arr[3] = 100 //当3>=arr.length时,会更新arr.length
//方式1 push unshift
//方式2 splice
arr.splice(index,0,items)
// 排序
arr.reverse()
'abcde'.split('').reverse().join('') //'edcba'
arr.sort((a,b)=>{
  return b-a
})
```
### 根据arr中元素创建一个新数组

对数组成员进行某种操作
```javascript
//n->n
arr.map(item=>item*item)
//n-> lesser
arr.filter(item=>item%2==0)
//n->1
reduce((previousValue,currentValue)=>{},initialValue)
arr.reduce((sum,item)=>{return sum+item},0)
arr.reduce((result,item)=>{return result.concat[item*item]},[])
arr.reduce((result,item)=>{return item%2==0?result.concat[item]:result},[])
```
## 函数对象
### 定义
```javascript
let f = new Function(para1, para2, statement)
function f1(para1,para2){
  statement
}
let f2 = function(para1,para2){
  statement
}
let f3 = function f(para){

}//f的作用域仅在等号左边

let f4 = (x,y)=> x*y

```
### 作用域
全局变量 局部变量 闭包(函数+词法环境) 词法环境

### 函数的执行时机
```javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}

```

以上代码的执行结果为`6 6 6 6 6 6`
原因是: 函数在调用刚开始,会自动创建一个新的词法环境以存储这个调用的局部变量和参数;

而箭头函数的外部词法环境为setTimeout的内部词法环境,setTimeout的外部词法环境为for代码块,for代码块的外部此法环境为全局;

箭头函数在for循环执行完毕之后运行,根据词法环境找到全局变量i,此时的i为6.所以输出`6`

以上代码打印 `0 1 2 3 4 5`的方法,让该箭头函数的词法环境的某个链定义局部变量i
```javascript
//方法1
let i = 0
for(let i=0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
//方法2
let i = 0
for(i=0; i<6; i++){
  !function(i){
    setTimeout(()=>{
        console.log(i)
      },0)
  }(i)
}

```

###  形参 实参
```javascript
function add(){
  var x = arguments[0]
  var y = arguments[1]
}
```
### 返回值

任何函数都有返回值,默认返回undefined

### 调用栈(call stack)
```javascript
function a() {  
    setTimeout(function() {alert(1)}, 0);  
    alert(2);  
}  
a(); 
```
> setTimeout使得alert(1)加入到新的函数调用栈中,只有等待a()所在的调用栈所有函数执行完成后,alert(1)所在的调用栈才会被启用~
### 申明提升
### arguments
类数组, 可通过Array.from()转换为数组.
### this
在定义函数时调用者的地址未知,那函数如何拿到调用者的属性,=>调用者在调用时将自己的地址传给此函数.

js中通过this这一隐藏的参数将调用者的地址传给调用的函数

显示传参:
```javascript
person.sayHi.call(person,[arguments])
```
### 绑定this
```javascript
//bind
function f1(a,b){
  console.log(this,arguments[0],b)
}
let obj = {name:'f2的固定调用者'}
let f2 = f1.bind(obj)
f2()//等价于 f1.call(obj)
```
### 箭头函数
没有arguments和this,this仅是普通变量

### Function.prototype的属性

### window.Function的构造函数

任何函数的构造函数都是Function,因为函数定义方式等价于new Function()

构造函数的终点是Function,原型的终点是null
```javascript
window.Function.__proto__.constructor === window.Function // true
```
### 立即执行函数
```javascript
!function(){
  var a = 3
  console.log(2)
}()
```

## class
```javascript
class Square{
  constructor(width){
    this.width = width
  }
  getArea(){
    return Math.pow(this.width, 2)
  }
}

```

## 运算符
### ==
> 全部使用===
> NaN !== NaN  
### && ||
```javascript
console && console.log && console.log('hi')
console?.log?.('hi')//可选链

function add(n=0){
  return n+1
}
add(null) //1  null/undefined==>n=0
```
### & | ~ >> << ^
位运算符会消除小数
```javascript
console.log(~~6.83) //6
console.log(6.83>>0) //6
console.log(6.83|0)//6
```
位运算判断奇偶
```javascript
6 & 1 //0
7 & 1 //1
```
位运算交换两个整数值
```javascript
a ^= b
b ^= a
a ^= b
```

### .运算符
```javascript
//封装Number String Boolean
let a = 1
a.xxx = 'test'
console.log(a.xxx)//undefined
```

### void
void 表达式或语句

作用: 求值/执行语句 -> 返回 undefined

### , 运算符
返回最后一部分的值作为整个表达式的值