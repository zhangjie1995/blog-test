# document object model
## 获取元素
1. idxx
```javascript
window.test 
test
```
2. ~~getElement~~
仅在需要兼容IE的时候使用
```javascript
document.getElementById('test')
document.getElementsByTagName('div')[0]
document.getElementsByClassName('div')[0]
```
3. querySelector
```javascript
document.querySelector('div>span:nth-child(2)')
document.querySelectorAll('div')[2]
```
4. 获取特殊元素
```javascript
document.documentElement
document.head
document.body
window
document.all[3]//特殊情况chrome document.all为false
```

## 元素与节点

### 元素原型链
![div原型链](https://static.xiedaimala.com/xdml/file/3ac7c224-c23d-491f-84b5-4fabfbeab9b8/2019-10-17-20-36-26.png)

### 节点
节点包括元素和文本等,对应的nodeType为1和3等.

## CRUD
### create
```javascript
let div1 = document.querySelector('#div1') 
let style = document.createElement('style')
let text = document.createTextNode('hello')

div1.append(style)
div1.append(text)
div1.innerText = 'hello'
div1.textContent = 'hello'//三种添加文本的方式都可以,区别是第一种只能添加,后两种直接修改全部文本

div1.prepend(style)
div1.before(style)
div1.after(style)
div1.replaceWith(style)
div1.appendChild(style)//古老方式 不推荐

```

一个元素只能出现在一个地方,除非复制一份
```javascript
let div2 = document.querySelector('#div2')
div2.append(style)
//这时style元素只会出现在div2的子结点中
let style2 = style.cloneNode(true)//true表示deep clone
div1.append(style2)
```

### delete
```javascript
//IE
div1.parentNode.removeChild(div1)
//移除的div1仍存在,div1 = null 之后
document.body.appendChild(div1)
//无需兼容
div2.remove()

//属性
div2.removeAttribute('tst')
```
### update
```javascript
//属性
div1.id = 'div1'
div1.className = 'blue'//class是保留字,所以使用className
div1.classList.add('red')
div1.style.color = 'red'
div1.style.backgroundColor = 'blue'
div1.setAttribute('test', 'aaaa') 

//事件
div1.onclick = function(x){
    console.log(this)
    console.log(x)
}
//添加事件后,当触发事件时,浏览器会调用函数 fn.call(div1.event)
//其中event包含了事件的所有信息,如坐标等等
//div1.onclick默认值为null

//内容
div1.innerText = 'hi'
div1.textContext = 'he'
div1.innerHTML = ''



```
### read
```javascript
//属性
//标准属性
div.classList
//非标准属性
div.getAttribute('href')//有时候与上面方式得到的值会有所不同

div.parentNode
div.parentElement
div.childNodes//包括文本节点
div.children//不包括文本节点

div.firstChild
div.lastChild
div.previousSibling
div.nextSibling
div.previousElementSibling
div.nextElementSibling

//遍历一个div元素中的所有元素,含嵌套元素
travel = (node, fn)=>{
    fn(node)
    if(node.children){
        for(let i=0; i<node.children.length; i++){
            travel(node.children[i], fn)
        }
    }
}
travel(div1, (node) => console.log(node))
```

## js执行线程 渲染线程
