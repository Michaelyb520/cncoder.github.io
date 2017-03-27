---
layout: post
title:  "jquery使用技巧总结"
categories: JQuery
tags:  JQuery
author: Romennts 
---

* content
{:toc}


* .bind()方法可使用.on()方法来代替

1. on()方法提高代码易读性，如下

```javascript

$("input").bind("click", { foo: "hello" }, handler);

$("input").on("click", { foo: "hello" }, handler);
```

2. .bind()绑定事件的时候，这些元素必须已经存在，而on()可以处理类似于代理这样的东东，也就是说不存在的元素（动态生成的元素也可以处理），如下动态生成的 To do list ，再双击删除，可使用on()轻松完成，你会发现，on换成bind是不行的。 

```html
<input type="text" id="str">
<button id="btn">添加</button>
<h3>To do list</h3>
<ul></ul>
```

```javascript
$(document).ready(function(){

		$('#btn').on('click',function(){
			var str = $('#str').val();
			console.log(str)
			$('<li>').text(str).appendTo('ul');
			
			$('#str').val('');
		})

        //To do list双击删除
		$(document).on('dblclick','li',function(){
			$(this).remove();
		})
	});
```