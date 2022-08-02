## dom事件模型
e.target 操作元素,最小触发元素

e.currentTarget 监听元素

事件结束之后,e消失

因为元素之间存在嵌套,为了确定哪个元素上面个绑定了事件,所以事件触发后,会在子元素和父元素之间传播---->事件的传播

传播分为两个阶段: 捕获(capture)-->target-->冒泡(bubble),分别使从window对象传播到target元素和从target传播到window对象.这两个阶段,会使得同一个事件在多个节点上触发.

## 取消冒泡
```JavaScript
e.stopPropagation()
```
## 如何阻止滚动
```javascript
x.addEventListener('wheel', (e)=>e.preventDefault())

x.addEventListener('touchstart', (e)=>e.preventDefault())
// css取消滚动条
// ::webkit-scrollbar:{
//      display:none;
// }
```

## 自定义事件
```javascript
x.addEventListener('click',()=>{
    const diyEvent =  new CustomEvent('diy',{
        detail: {name: 'diy', age: 0},
        bubbles: true,
        cancelable: false
    })
    x.dispatchEvent(diyEvent)
})
```

## 事件委托

考虑到传播机制,可以将子元素的监听函数放在其祖先元素上,当事件传播到其祖先元素时触发并执行回调函数.方便以后添加类似的子元素时不用额外添加监听器.

[案例](http://js.jirengu.com/kuyugibeno/1/edit?html,js,console,output)
