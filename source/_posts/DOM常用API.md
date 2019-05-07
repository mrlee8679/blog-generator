---
title: DOM常用API（1）
date: 2019-04-27 19:02:42
tags:
---


## 基本概念

DOM 是 JavaScript 操作网页的接口，全称为“文档对象模型”（Document Object Model）。它的作用是将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作（比如增删内容）。

浏览器会根据 DOM 模型，将结构化文档（比如 HTML 和 XML）解析成一系列的节点，再由这些节点组成一个树状结构（DOM Tree）。所有的节点和最终的树状结构，都有规范的对外接口。

DOM 只是一个接口规范，可以用各种语言实现。所以严格地说，DOM 不是 JavaScript 语法的一部分，但是 DOM 操作是 JavaScript 最常见的任务，离开了 DOM，JavaScript 就无法控制网页。另一方面，JavaScript 也是最常用于 DOM 操作的语言。

DOM1级定义了一个Node接口，该接口由DOM中所有节点类型实现。这个Node接口在JS中是作为Node类型实现的。在IE9以下版本无法访问到这个类型，JS中所有节点都继承自Node类型，都共享着相同的基本属性和方法。
Node有一个属性nodeType表示Node的类型，它是一个整数，其数值分别表示相应的Node类型，具体如下：
Node.ELEMENT_NODE(标签节点):1
Node.ATTRIBUTE_NODE(属性节点):2
Node.TEXT_NODE(文本节点):3
Node.CDATA_SECTION_NODE(CDATA节点):4
Node.ENTITY_REFERENCE_NODE(实体引用节点):5
Node.ENTITY_NODE(实体节点):6
Node.PROCESSING_INSTRUCTION_NODE(处理指令节点):7
Node.COMMENT_NODE(注释节点):8
Node.DOCUMENT_NODE(文档节点):9
Node.DOCUMENT_TYPE_NODE(文档类型节点):10
Node.DOCUMENT_FRAGMENT_NODE(文档段节点):11
Node.NOTATION_NODE(DTD声明节点):12


## 节点创建型 API

### creatElement

createElement通过传入指定的一个标签名来创建一个元素，如果传入的标签名是一个未知的，则会创建一个自定义的标签，如下：

```
var div = document.createElement("div");
```

使用createElement要注意：通过createElement创建的元素并不属于html文档，它只是创建出来，并未添加到html文档中，要调用appendChild或insertBefore等方法将其添加到HTML文档树中。

### createTextNode

```
var textNode = document.createTextNode("一个TextNode");
```

createTextNode接收一个参数，这个参数就是文本节点中的文本，和createElement一样，创建后的文本节点也只是独立的一个节点，同样需要appendChild将其添加到HTML文档树中.

### cloneNode

```
var parent = document.getElementById("parentElement"); 
var parent2 = parent.cloneNode(true);// 传入true
parent2.id = "parent2";
```

这段代码通过cloneNode复制了一份parent元素，其中cloneNode的参数为true，表示parent的子节点也被复制，如果传入false，则表示只复制了parent节点。

### createDocumentFragment

createDocumentFragment方法用来创建一个DocumentFragment。DocumentFragment表示一种轻量级的文档，它的作用主要是存储临时的节点用来准备添加到文档中。



