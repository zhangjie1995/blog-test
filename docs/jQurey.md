## 构造函数
```javascript
window.$ = window.jQuery(selectorOrArrayOrTemplate){
    let elements
    if(typeof selectorOrArrayOrTemplate === 'string' ){
        elements = document.querySelectorAll(selectorOrArrayOrTemplate)
    }else if(selectorOrArrayOrTemplate instanceof Array){
        elements = selectorOrArrayOrTemplate
    }else if( ...){
        ...
    }else {
        ...
    }

    let api = Object.create(jQuery)
    api.elements = elements
    return api
}
jQuery.prototype = {
    constructor: jQuery,
    next(){
        ...
    },
    parent(){
        ...
    },
    each(fn){
        for(let i=0; i<this.elements.length; i++){
            fn.call(null, this.elements[i])
        }
        return this
    }
}
```

jQuery通过选择器或者元素数组获取元素,不过返回的并非元素本身,而是将元素包裹的对象,并且通过原型链将一系列函数绑定在该对象上,从而使得这些函数可以操作被包裹的对象.

## 链式操作

### 改变元素的操作

使用新的对象包裹新的元素们,仍然通过原型链绑定一系列的操作函数,并返回新对象
```javascript

jQuery.prototype = {
    constructor: jQuery,
    children(){
        return jQuery(this.Children)
    }
}

```

### 不改变元素范围的操作

每个操作都返回将元素包裹的对象
```javascript
jQuery.prototype = {
    constructor: jQuery,
    addClass(className){
        this.each((node)=>node.classList.add(className))
        return this
    }
}
```
## 创建元素

使用重载,根据传入的参数不同,采取不同的处理方式
```javascript
    $('<p>Hello</p>')

```

## 移动元素

```javascript
$('#div').after($('p'))
$('p').insertAfter($('#div'))
```
两种方法达成同样的效果,关键在于返回值的不同,这影响到后续的链式调用.

## 修改属性

```javascript
jQuery.prototype = {
    constructor: jQuery,
    attr(name,value){
        if(arguments.length === 1){
            if(typeof name === 'string'){
                ...
            }else if(typeof name === 'object'){
                for(let key in name){
                    ...
                }
            }
        }else if(arguments.length === 2){
            this.each((node)=>node[name] = value)
        }
    }
}

```

通过重载,使得一个函数可以完成getter和setter两种功能.
