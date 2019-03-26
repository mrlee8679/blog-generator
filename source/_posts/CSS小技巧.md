---
title: CSS小技巧
date: 2019-03-26 09:55:20
tags:
---

## 左右布局

当需要出现以下结构时，需要设置左右布局时；

``` 
    <div class="parent">
        <div class="Child1"></div>
        <div class="Child2"></div>
    </div>
```

可以设置浮动，左右布局常用的方法就是为子元素设置浮动，然后在其父元素上使用clearfix 类清除浮动。示例如下：

``` 
    .clearfix::after{
    content:"";
    display:block;
    clear:both;
    }
    .Child1,
    .Child2{
    float:left;
    }
```

也可以设置绝对定位，为父元素设置 position:relative; 为子元素设置position:absolute 。示例如下：

```
    .parent{
    position:relative;
    }
    .Child1{
    position:absolute;
    left:0;
    top:0;
    }
    .rightChild{
    position:absolute;
    left:200px;
    top:0;
    }
```
## 左中右布局

左中右布局，情况跟左右布局差不多，主要方法也是浮动或者绝对定位，不过可以分情况选择其一使用甚至结合使用。

## 水平居中

### 内联元素水平居中

可以在最近的一层块级元素设置 text-align:center，如：

``` 
    <div class="parent">
        <a>Child</a>
    </div>
``` 

在 CSS 中：

``` 
    .partent{
        text-align:center;
    }

text-align:center 是用于设置div块中的内容（a标签）居于整个div宽度的中间。
```

### 块级元素水平居中

可以像内联元素一样用 text-align:center 进行水平居中，只要给该块级元素加上 display: inline ，让它内联显示即可；如：

``` 
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
    </ul>
```

在 CSS 中：
```
    ul{
        text-align:center;
    }
    ul>li{
        display: inline;
    }
```

或者使用 margin:0 auto; 也可以让块级元素水平居中。

## 垂直居中

若元素是单行文本, 则可设置 line-height 等于父元素高度，就可以垂直居中。

## 背景图片的居中设置

当设置了背景图片时，可以用 background-size: cover 让图片大小自适应（保持原有比例，可能背景图片部分看不见），并用background-position: center center 让背景图片在显示范围中居中。

## 查找想要的CSS的代码

当知道想要的CSS效果，却不知道相应的CSS效果时，可以用 GOOGLE 查找相应的代码，如；想要查找渐变效果的CSS代码，可以 google 搜索 css gradual generator ，第一个查找结果就是想要的效果生成器；再例如，想要阴影效果时，可以搜索 css shadow generator。