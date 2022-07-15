# HTML

## 发明人

李爵士

## 格式

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <!--语言,谷歌翻译参考这个属性 -->
  <head>
    <meta charset="utf-8" />
    <!--编码格式 -->
    <title>HTML入门笔记1</title>
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <!-- 兼容-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- 自适应 -->
  </head>
  <body></body>
</html>
```

## head-elements

- title
- meta

  ```html
  <meta name="" content="" />
  <!-- name的可选属性有:charset, viewport, description, keywords, author-->
  ```

- script
- style
- link

## 章节标签

1. 标题 h1~h6
2. 章节 section
3. 文章 article
4. 段落 p
5. 头部 header
6. 脚部 footer
7. 主要内容 main
8. 旁支内容 aside
9. 划分 div

## global-attribute

1. class
2. contenteditable
3. hidden
4. id
   > 唯一
5. style
   > 就近原则
6. ~~tabindex~~
7. title

   > 出现省略时用于提供详细描述

   ```css
   white-space: nowrap;
   overflow: hidden;
   text-overflow: ellipse;
   ```

## 内容标签

- ul ol li
  > 有序/无序列表
- p
  > paragraph,段落
- dl dt dd
  > 解释列表 description-term,des-data
- pre
  > 保留空格数量
- hr
  > 横线
- br
  > 换行
- a
  > hypertext
  ```html
  <a href="" target=""></a>
  <!-- href取值: //google.com  /a/b/index.html #xxx javascript:;  mailto:.com  tel:123324;-->
  ```
  > 作用: 跳转另一个网页或 anchor 伪协议
- em
  > emphasis,强调语气
- strong
  > 强调内容,样式表现为加粗
- code
  > 灰色背景
- quote
  > 语义标签,无样式
- blockquote
  > 代码块
- table thead tbody tfoot tr td th
  > 相关样式 border-collapse: collapse; border-spacing: 0;
- img
  > image,发送 get 请求
  ```html
  <img src="" alt="" />
  ```
  > 事件相关: onload,onerror
- form

```html
<form action="/yyy" method="get/post" autocomplete="on">
  <input type="text" />
  <button type="submit">submit</button>
</form>
```

> input 的 type: text/color/password/radio/checkbox/file
> 事件: onchange onblur onfocus
> 属性: name/value/required
