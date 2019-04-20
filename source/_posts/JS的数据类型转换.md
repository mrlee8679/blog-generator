---
title: JS 的数据类型转换与对象的储存
date: 2019-04-19 00:41:44
tags:
---

## 转换成 String

总共有3种方法可以把其他数据类型转变成 String 类型

### tostring
用tostring时，需要注意的是，对 null 和 undefined 使用toString 是会报错的，用 toString 转 object 会得到 "[object Object]" 。如下：

```
var n = 1
n.toString()
// "1"

var object = {a:'1'}
object.toString()
// "[object Object]"
```

### String 和 + ''
第二与第三种方法是使用全局函数 String() 与使用 + '' ,这两种方法可以把所有类型都转换成 String ，效果如下：

```

String({}) // "[object Object]"

null + '' // "null"

undefined + '' // "undefined"

```

## 转换成 Number

1、使用 Number('1') === 1；
2、使用 parseInt('1',10) === 1 ,用这种方法时最好记得把后面的 10 写上，这个 10 代表十进制。若写成 parseInt('011') 得到数字会是11，而不是八进制下的9，要使用八进制必须在后面加上8 如 parseInt('011',8) === 9 。当写 parseInt('a') 时得到的是NaN。
3、使用 parseFloat('1.23') === 1.23 , 表示浮点数；
4、'1' - 0 === 1;
5、+ '1' === 1 或者 - '1' === -1

## Boolean

可以使用 Boolean() 将其他类型的数据转换成 bolean 型的数据，也可以在要转换的数据前加 `!!` 这样也能做到与 Boolean 同样的效果。 boolean 型数据只有2个个值，就是 true 和 false 。有5个值，转换成 boolean 时会是 false ，这5个值被称为 falsy 值，它们分别是 0 、 NaN 、 '' 、 undefined 、 null ，所有的 object 转换成 boolean 都会是true 。

```
!! {} // true

!! 1 // true

!! 0 // false

!! NaN // false

!! '' // false

!! undefined // false

!! null // false
```

## Object

其他类型与对象的区别就在于存储的方式不一样。当 JS 分到内存后会分为2个大区域进行存储，分别是代码区和数据区，如 var a = 1 时，a 会存在代码区，1就会存在数据区，然后 a 和1就会产生关联。接下来主要讨论的是数据区发生了什么。

数据区的分为 Stack 栈内存与 Heap 堆内存。一般类型的数据就存放在 Stack 内存，有 Number 、 String 、 Symbol 、 Boolean 、 Null 和 Undefined 

![基本类型的存储](/C:/Users/86793/Desktop/blog/source/_posts/JS的数据类型转换/基本类型.png)

而 Object 类型的存储有点不一样，var b = {name:'son'} 他会把内容 (name:'son') 存在 Heap 堆内存里，并会生成一个地址，然后在 b 的对应的 Stack 栈内存里存的就是那个地址，可以说是 b 引用了这个对象。

![基本类型的存储](/C:/Users/86793/Desktop/blog/source/_posts/JS的数据类型转换/对象.png)

当一个对象没有被引用时，那这个对象就是垃圾，会被浏览器回收。
