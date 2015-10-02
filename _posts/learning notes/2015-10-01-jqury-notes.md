---
layout: post
title: jQury笔记
category: 学习笔记
tags: [jqury,教程]
keywords: jquey,教程
description: 
---

## 安装

1.从[jqury.com](http://jqury.com)下载

2.CDN

    Baidu CDN:http://libs.baidu.com/jquery/1.10.2/jquery.min.js
    又拍云 CDN:http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js
    新浪 CDN:http://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js
    Google CDN:http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js
    Microsoft CDN:http://ajax.htmlnetcdn.com/ajax/jQuery/jquery-1.10.2.min.js


## 语法

__基础语法： `$(selector).action()`__

### 选择器

jquery选择器基于已存在的css选择器，还有一些自定义的选择器

`$(this)` - 当前元素
`$("p")` - 所有 \<p\> 元素
`$("p:first")` - 选取第一个\<p\>元素
`$("p .test")` - 所有 class="test" 的 \<p\> 元素
`$(".test")` - 所有class="test"的元素
`$("#test")` - 所有 id="test" 的元素
`$("[href]")` - 带有href属性的元素
`$("ui li:first")` - 选取第一个\<ul\>的第一个\<li\>元素
`$("ui li:first-child")` - 选取每个\<ul\>的第一个\<li\>元素
`$("a[target!='_blank']")` - 选取所有target属性值不等于"_blank"的\<a\>元素
`$(":button")` - 选取所有type="button"的\<input\>元素和\<button\>元素
`$("tr:even")` - 选取奇数位置的\<tr\>，偶数为odd





## 事件

### 文档就绪事件

为防止jquery代码在文档未加载完成时就执行，最好将函数封装在document ready函数中：

		$(document).ready(function(){

    		// jQuery code...

		});

简写为：

		$(function(){

    		// jQuery code...

			});

或者：

		$().ready(function(){

			 	//jQuery code...

			})

### 常见DOM事件

鼠标事件：`click` `dbclick` `mouseenter` `mouseleave` `mouseup` `hover` `mousedown` 
键盘事件：`keypress` `keydown` `keyup`
表单事件：`submit` `change` `focus` `blur`
文档/窗口事件：`load` `resize` `scroll` `unload`

    $("p").click(function(){
    	$(this).hide();
    	});

    $("input").focus(function(){
  		$(this).css("background-color","#cccccc");
			});


## 效果

1. 显示/隐藏

		//可选参数speed规定变化速度，可取"slow" "fast"或毫秒数
		//可选参数callback为变化完成之后执行的函数
		$(selector).hide(speed,callback);
		$(selector).show(speed,callback);
		//toggle()方法可切换hide()和show()
		$(selector).toggle(speed,callback);

2. 淡入淡出
		
		//淡入隐藏的元素
		$(selector).fadeIn(speed,callback);
		//淡出可见元素
		$(selector).fadeOut(speed,callback);
		//在fadeIn()和fadeOut()间进行切换
		$(selector).fadeToggle(speed,callback);
		//渐变为给定的不透明度(opacity)，值介于 0 与 1 之间，speed与opacity为必选参数
		$(selector).fadeTo(speed,opacity,callback);







