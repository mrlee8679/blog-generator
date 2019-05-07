---
title: 一个 jQuery 的 API
date: 2019-05-07 00:18:22
tags:
---

## 代码部分

``` 
window.jQuery = function(nodeOrSelector){
  let nodes = {}
  if (typeof nodeOrSelector === 'string') { 
    let temp = document.querySelectorAll (nodeOrSelector)
    for (let i = 0 ; i < temp.length; i++){
      nodes[i] =temp[i]
    }
    nodes.length = temp.length
  }else if (nodeOrSelector instanceof Node){
    nodes = {
      0 : nodeOrSelector,
      length : 1
    }
  }
  nodes.addClass = function(classes){
    classes.forEach( (value) => {
      for ( let i = 0; i < nodes.length; i++ ){
        node[i].classList.add(value)
      }
    } )
  }
  nodes.text = function(text){
    if ( text === undefined ){
      var texts = []
      for ( let i = 0; i < nodes.length; i++ ){
        text.push( nodes[i].textContent )
      }
      return texts
    }else{
      for (let i=0; i < nodes.length; i++){
        nodes[i].textContent = text
      }
    }
  }
  return nodes
}
```

## 细节

```
if ( typeof nodeOrSelector === 'string' ) { 
    let temp = document.querySelectorAll(nodeOrSelector)
    for ( let i = 0 ; i < temp.length; i++ ){
      nodes[i] =temp[i]
    }
    nodes.length = temp.length
  }else if (nodeOrSelector instanceof Node){
    nodes = {
      0 : nodeOrSelector,
      length : 1
    }
}
```

这段代码是为了区分传入的参数是一个节点还是多个节点，若传入多个节点就通过 querySelectorAll 生成一个伪数组，并将节点放进这个伪数组中。

```
node.addClass = function(classes){
    classes.forEach( (value) => {
      for ( let i = 0; i < nodes.length; i++ ){
        node[i].classList.add(value)
      }
    } )
}
```

这部分是给找到的元素添加 className。

```
nodes.text = function(text){
  if ( text === undefined ){
    var texts = []
    for ( let i = 0; i < nodes.length; i++ ){
        text.push( nodes[i].textContent )
    }
    return texts
  }else{
    for ( let i=0; i < nodes.length; i++ ){
      nodes[i].textContent = text
    }
  }
}
```

这部分是判断传是否要修改文本内容，若没有传入参数则就说明想获取对象内容，所以就新建一个数组并将内容传入数组中。若传入的是文本，就说明想修改文本内容，所以就进行文本内容修改的操作。