# css

## 版本

css2 用的最为广泛

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
![盒模型](<https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model/boxmodel-(3).png>)
box-sizing

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

兄弟
父子
** 如何取消 **

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
