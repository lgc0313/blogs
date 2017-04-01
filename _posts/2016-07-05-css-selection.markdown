---
layout:     post
title:      "CSS选择器总结"
subtitle:   ""
date:       2016-07-05
author:     "lgc"
header-img: "img/post-bg-js-version.jpg"
tags:
    - CSS
---

# 基本选择器
-  \* 通用选择器，匹配任何元素
- E 标签选择器，匹配所有使用E标签的元素
- .class class选择器
- \#id id选择器
## 实例
```css
    \* { margin:0; padding:0; }
    p { font-size:2em; }
    .info { background:#ff0; }
    p.info { background:#ff0; }
    p.info.error { color:#900; font-weight:bold; }
    #info { background:#ff0; }
    p#info { background:#ff0; }
```
[在线演示](http://jsbin.com/redapub/edit?html,css,output)
# 多元素选择器
- E,F 多元素选择器，同时匹配所有E元素或F元素，E和F之间用逗号分隔
- E F 后代元素选择器，匹配所有属于E元素后代的F元素，E和F之间用空格分隔
- E>F 子元素选择器，匹配所有E元素的子元素F
- E+F 毗邻元素选择器，匹配所有紧随E元素之后的同级元素F
## 实例
```css
    div p { color:#f00; }
    #nav li { display:inline; }
    #nav a { font-weight:bold; }
    div > strong { color:#f00; }
    p + p { color:#f00; }
```
[在线演示](http://jsbin.com/lupahe/edit?html,css,output)
# CSS 2.1 属性选择器
- E[attr] 匹配所有具有att属性的E元素，不考虑它的值。（注意：E在此处可以省略，比如"[cheacked]"。以下同）
- E[att=val] 匹配所有att属性等于"val"的E元素
- E[att~=val] 匹配所有att属性具有多个空格分隔的值、其中一个值等于"val"的E元素
- E[att|=val]  匹配所有att属性具有多个连字号分隔（hyphen-separated）的值、其中一个值以"val"开头的E元素，主要用于lang属性，比如"en"、"en-us"、"en-gb"等等
## 实例
```css
    p[title] { color:#f00; }
    div[class=error] { color:#f00; }
    td[headers~=col1] { color:#f00; }
    p[lang|=en] { color:#f00; }
    blockquote[class=quote][cite] { color:#f00; }
```
# CSS 2.1中的伪元素
- E:first-line    匹配E元素的第一行
- E:first-letter    匹配E元素的第一个字母
- E:before    在E元素之前插入生成的内容
- E:after在E元素之后插入生成的内容
## 实例
``` css
    p:first-line { font-weight:bold; color;#600; }
    .preamble:first-letter { font-size:1.5em; font-weight:bold; }
    .cbb:before { content:""; display:block; height:17px; width:18px; background:url(top.png) no-  repeat 0 0; margin:0 0 0 -18px; }
    a:link:after { content: " (" attr(href) ") "; }
```
[在线实例](http://jsbin.com/votibo/edit?html,css,output)
# CSS 3的同级元素通用选择器
- E ~ F匹配任何在E元素之后的同级F元素
## 实例
```css
    p ~ ul { background:#ff0; }
```
[在线演示](http://jsbin.com/falole/edit?html,css,output)
# CSS 3 属性选择器
- E[att^="val"]    属性att的值以"val"开头的元素
- E[att$="val"]    属性att的值以"val"结尾的元素
- E[att*="val"]    属性att的值包含"val"字符串的元素
## 实例
```css
    div[id^="nav"] { background:#ff0; }
```
## CSS 3中的结构性伪类
- E:root    匹配文档的根元素，对于HTML文档，就是HTML元素
- E:nth-child(n)    匹配其父元素的第n个子元素，第一个编号为1
- E:nth-last-child(n)    匹配其父元素的倒数第n个子元素，第一个编号为1
- E:nth-of-type(n)    与:nth-child()作用类似，但是仅匹配使用同种标签的元素
- E:nth-last-of-type(n)    与:nth-last-child() 作用类似，但是仅匹配使用同种标签的元素
- E:last-child    匹配父元素的最后一个子元素，等同于:nth-last-child(1)
- E:first-of-type    匹配父元素下使用同种标签的第一个子元素，等同于:nth-of-type(1)
- E:last-of-type    匹配父元素下使用同种标签的最后一个子元素，等同于:nth-last-of-type(1)
- E:only-child    匹配父元素下仅有的一个子元素，等同于:first-child:last-child或 :nth-child(1):nth-last-child(1)
- E:only-of-type    匹配父元素下使用同种标签的唯一一个子元素，等同于:first-of-type:last-of-type或 :nth-of-type(1):nth-last-of-type(1)
- E:empty    匹配一个不包含任何子元素的元素，注意，文本节点也被看作子元素
[在线实例](http://jsbin.com/fihowi/edit?html,css,output)
##实例
```css
    p:nth-child(3) { color:#f00; }
    p:nth-child(odd) { color:#f00; }
    p:nth-child(even) { color:#f00; }
    p:nth-child(3n+0) { color:#f00; }
    p:nth-child(3n) { color:#f00; }
    tr:nth-child(2n+11) { background:#ff0; }
    tr:nth-last-child(2) { background:#ff0; }
    p:last-child { background:#ff0; }
    p:only-child { background:#ff0; }
    p:empty { background:#ff0; }
```
# CSS 3的反选伪类
- E:not(s)    匹配不符合当前选择器的任何元素
##实例
```css
    :not(p) { border:1px solid #ccc; }
```
# CSS 3中的 :target 伪类
- E:target    匹配文档中特定"id"点击后的效果
[实例](http://www.w3school.com.cn/tiy/t.asp?f=css_sel_target)