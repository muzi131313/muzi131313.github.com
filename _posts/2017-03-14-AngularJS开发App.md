---
layout: post
title: AngularJS开发App
tags:
- AngularJS
- roastwind
categories: AngularJS
---
<style>
a{text-decoration: none;}
a:link{text-decoration: none;}
a:visited{text-decoration: none;}
a:hover{text-decoration: none;}
a:active{text-decoration: none;}
.highlight{ background: #fff !important;};
</style>
##Native App
- 优缺点<br/>
1.优点:运行效率高、可调用各种设备资源；<br/>
2.缺点：人力成本高、发布速度慢(appstore发布)、更新版本问题、实现图文混排功能有各种坑。<br/>

- 混乱不堪的Android平台--版本帝(4个大版本，14个小版本)<br/>
- 混乱不堪的Android平台--众多品牌/分辨率/厂商


##Web App
- phonegap(cordava),appcan(webview),appcelerator<br/>
- 设计开发打包一体化(Intel XDK)(node webkit)

> 常见WEB APP框架对比:<br/>
jQuery Mobile->zepto->Sencha Touch->GMU->[ionic](http://ionicframework.com/docs/)(最好)(AngularJS)<br/>
案例：[豆瓣音乐人](https://music.douban.com/artists/)


##Hybrid App(复合型应用)
- 移动平台上特点：<br/>

> 1.操作流畅度不够(转场动画、列表滚动)<br/>
> 2.运行性能差<br/>
> 3.设备API不够<br/>
>> ps.方案、原理:<br/>
>> 1.blendUI:[示例](http://div.io/topic/560)<br/>
>> 2.[移动优先的跨终端Web](http://www.imooc.com/view/43):天猫前端->鬼道、徐凯

- 架构：<br/>

> 1.Android外壳->WebView->Mobile Ui控件库<br/>
> 2.Ios外壳->UIWebView->Mobile Ui控件库<br/>
> 3.总结:view切换、通讯服务->Webkit内核,HTML5/CSS3->通用组件

- 优缺点：<br/>
优点：<br/>

> 1.综合了开发效率和运行效率
> 2.发版本方便

缺点：<br/>

> 1.运行效率中等(切换等交互效果)
> 2.需要写一点原生代码(至少2个平台)

- 总结:<br/>

> 1.条件允许，尽量使用原生开发，局部嵌入WebView<br/>
> 2.赶时间演示demo，使用webapp<br/>
> 3.Hybird App改进在于使用多个WebView(一个Activity里面嵌一个)<br/>
> 4.webapp只使用一个webview<br/>
> 5.webapp打包时，需要原生环境。<br/>


<h1>知道一个东西的优点，你是入门了</h1>
<h1>知道一个东西的缺点，你是精通了</h1>


