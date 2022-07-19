# css

## 版本

css2.1 用的最为广泛

## 语法

1. 选择器
2. @

   ```css
   @charset "UTF-8";
   @import url(2.css);
   @media (min-width: 100px) and (max-width: 200px);
   ```

## 查资料

1. 关键词+mdn
2. css tricks
3. 张鑫旭
4. [css spec 中文](http://www.ayqy.net/doc/css2-1/cover.html)

## **文档流**

## 盒模型

浏览器引擎将元素表示为一个个矩形盒子 box<br>
![盒模型](<https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model/boxmodel-(3).png>)<br>

box-sizing(width,min-width-max-width 控制的范围)

> border-box: content + padding + border
> content-box: content

### 三种盒子类型的区别

|              | 流动方向           | 宽度        | 高度                     |
| ------------ | ------------------ | ----------- | ------------------------ |
| inline       | 从左到右           | 内容        | line-height 间接决定     |
| block        | 从上到下           | width->auto | height->包含文档流的高度 |
| inline-block | 成块出现的从左到右 | 同上        | 同上                     |

### overflow

内容块部分超出设定的 height 或 width

1. auto
   > 仅在内容块溢出时显示滚动条
2. hidden
   > 溢出部分隐藏
3. scroll
   > 显示滚动条,无论是否溢出
4. visible
   > 默认

### 脱离文档流

float<br/>
position: absolute/fixed;

## 盒模型

content-box border-box

### margin 合并/塌陷

> 发生条件
>
> 1. blocks
> 2. 兄弟
> 3. 父子
>    ** 如何取消 **

1. overflow
2. border
3. padding

## 单位

1. px
2. em
   > font-size
3. %
4. rem
5. vw and vh

## 布局

### float

使用场景: 需要兼容 IE9,且不需要响应式布局
how<br>
pre-code

1. border->outline

normal steps

1. 子元素 float 和 width
2. 父元素 .clearfix

   ```css
   .clearfix:after {
     content: "";
     display: block;
     clear: both;
   }
   ```

** 案例 **

1. 双栏
2. 三栏
3. 平均布局
   > 负 margin

### flex

#### container

1. display
   > flex/inline-flex
2. flex-direction
   > row | row-reverse | column column-reverse
3. flex-wrap
   > nowrap | wrap | ~~ wrap-reverse ~~
4. justify-content
   > flex-start | flex-end | center | space-between | space-around | ~~space-evenly~~
5. align-items
   > flex-start | flex-end | center | stretch(default) | ~~baseline~~
6. ~~align-content~~
   > flex-start | flex-end | center| stretch| space-between| space-around

#### items

1. order
   > default 0;
2. flex-grow
   > default 0;
3. flex-shrink
   > default 1
4. ~~flex-basis~~
5. align-self
   > flex-end ...

### grid

.container

> 1. grid-template-columns: 1fr 50px 1fr;
> 2. display: grid;
> 3. grid-template-rows: 1fr 1fr 1fr;
> 4. grid-gap
> 5. grid-template-areas

```css
.container {
  min-height: 100vh;
  display: grid;
  grid-template-areas:
    "header header header"
    "aside main ad"
    "footer footer footer";
  grid-template-rows: 60px auto 60px;
  grid-column-gap: 1px;
  grid-row-gap: 10px;
}
.container > header {
  grid-area: header;
}
```

.item

> 1. grid-column-start:
> 2. grid-area

## 层叠上下文

background < border < normal flow < float < 文字

会创建层叠上下文的属性:

1. transform
2. html
3. flex,grid 容器的子元素,position 不为 static 且 z-index 不为 auto 的元素
4. opacity 属性小于 1

## 定位

position

1. relative
   > 实际位置不变,显示位置可偏移
   > 作用: 偏移(少), 做 absolute 的父元素
   ```css
   .demo {
     position: relative;
     top: 10px;
   }
   ```
2. fixed
   > 相对于视口定位, 如果父元素有 transform 属性,会错乱
   > 使用场景广告,回到顶部,移动端有 bug
3. absolute
   > 脱离文档流
   > 使用场景: 关闭窗口,相对于第一个带 relative 的父元素偏移
4. sticky
5. static(default)
   > 文档流中本来的位置

属性

1. z-index
   > auto(default)

## 文字

1. white-space
   > nowrap

## 动画

### 渲染原理

1. DOM 树
2. CSS 树
3. 渲染树 render
4. layout 布局(normal flow,盒模型)
5. paint(边框颜色,文字颜色,阴影)
6. composite(层叠上下文)

更改样式的方式不同 渲染步骤不同

### 动画优化

1. js 优化
   > 使用 requestAnimationFrame 代替 setTimeout/setInterval
2. css 优化
   > 使用 will-change/translate

### relative

### transform

只能转换盒模型定位的元素

1. 位移 translate
   > transform: translateX(50px);
   > 场景:
   ```css
   .item {
     position: absolute;
     left: 50%;
     transform: translate(-50%, -50%);
   }
   .container {
     position: relative;
   }
   ```
2. 缩放 scale

3. 旋转 rotate

4. 倾斜 skew

动画控制

transition
属性: 控制属性 时长 过度方式 延迟
过渡方式: linear | ease | step

**demo**

> 1. [跳动红心](https://jsbin.com/veyuvalahe/edit?html,css,output)

## animation

animation: 时长 | 动画名 | 过渡方式 | 延迟 | 次数(infinite) | 方向(reverse|alternate|)|填充模式(forwards)|暂停

```css
.item {
  animation: xxx 15s;
}
@keyframes xxx {
  0% {
  }
  50% {
  }
  100% {
  }
}
```

**demo**
[跳动红心](https://jsbin.com/navetuyuye/edit?html,css,output)
