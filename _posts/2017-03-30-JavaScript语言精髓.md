---
layout: post
title: JavaScript语言精髓
tags:
- JavaScript
- roastwind
categories: Interview
---
<style>
a{text-decoration: none;}
a:link{text-decoration: none;}
a:visited{text-decoration: none;}
a:hover{text-decoration: none;}
a:active{text-decoration: none;}
.highlight{ background: #fff !important;};
</style>

## 位运算符
- `$` and按位与
- `|` or 按位或
- `^` xor 按位异或
- `~` not 安位非
- `>>` 带符号的右位移
- `>>>` 无符号的（用0补足的）右位移
- `<<` 左位移

````
var num = 11;
var numText = ~[12,13].indexOf(num) ? 'hello' : 'bye';
````

ps:
> 用`~`符号在代码中是怎样的一种体验,下面是解释(给你一个眼神，自己体会):<br/>
> `~1 = `<br/>
> 将1(这里叫：原码)转二进制 ＝ 00000001
按位取反 ＝ 11111110
发现符号位(即最高位)为1(表示负数)，将除符号位之外的其他数字取反 ＝ 10000001
末位加1取其补码 ＝ 10000010
转换回十进制 ＝ -2<br/>
[参考来源](https://segmentfault.com/q/1010000005697515)

