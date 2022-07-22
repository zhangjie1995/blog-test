# 表达式和语句

```javascript
while(expression){
    statement1
    statement2
    ...
}
```

语句(statement): 带有目的的操作,i.e, 赋值语句,while 语句...

表达式(expression): 为了得到返回值的计算式

# 标识符(identifier)

规则:

1. 字母(unicode 字母,包括中文),数字,$,下划线(\_)
2. 首字符不能是数字
3. 不能使用保留字

# if-else 语句

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

# while/for 语句

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

# 替代 if 的几种方式

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
