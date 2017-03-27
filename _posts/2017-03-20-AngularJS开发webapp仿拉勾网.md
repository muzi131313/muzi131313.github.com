---
layout: post
title: AngularJS Webapp
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

## 1.单页应用的特点
- 页面不刷新
- 依靠监听hash值进行页面之间的切换

## 2.gulp打包的依赖
- gulp
- gulp-clean
- gulp-concat
- gulp-connect
- gulp-cssmin
- gulp-imagemin
- gulp-less
- gulp-load-plugins
- gulp-uglify
- open

##3.编写gulpfile.js文件
- $的使用

````
var $ = require('gulp-load-plugins')();
````

> 需要实例化

- html的配置

````
$.htmlmin({
    removeComments: true,//清除HTML注释
    collapseWhitespace: true,//压缩HTML
    collapseBooleanAttributes: true,//省略布尔属性的值 <input checked="true"/> ==> <input />
    removeEmptyAttributes: true,//删除所有空格作属性值 <input id="" /> ==> <input />
    removeScriptTypeAttributes: true,//删除<script>的type="text/javascript"
    removeStyleLinkTypeAttributes: true,//删除<style>和<link>的type="text/css"
    minifyJS: true,//压缩页面JS
    minifyCSS: true//压缩页面CSS
});
````

- css的配置

````
$.cssmin({
	advanced: true,//类型：Boolean 默认：true [是否开启高级优化（合并选择器等）]
    compatibility: 'ie7',//保留ie7及以下兼容写法 类型：String 默认：''or'*' [启用兼容模式； 'ie7'：IE7兼容模式，'ie8'：IE8兼容模式，'*'：IE9+兼容模式]
    keepBreaks: false,//类型：Boolean 默认：false [是否保留换行]
    keepSpecialComments: '*'
    //保留所有特殊前缀 当你用autoprefixer生成的浏览器前缀，如果不加这个参数，有可能将会删除你的部分前缀
})
````

- 热编译

````
gulp.task('image', function () {
	gulp.src(app.srcPath + 'image/**/*')
	.pipe(gulp.dest(app.devPath + 'image'))
	.pipe($.imagemin())
	.pipe(gulp.dest(app.prdPath + 'image'))
	.pipe($.connect.reload());	// 输出绑定connect的reload事件
});
gulp.task('serve', function () {
	$.connect.server({
		root: [app.devPath],
		livereload: true, 	// 自动刷新
		port: 1234,

	})
	open('http://localhost:1234/index.html');
	gulp.watch(app.srcPath+'image/**/*', ['image']); // 监听image任务
});
````

> [gulp具体配置](https://github.com/muzi131313/angularjs_employee/blob/master/gulpfile.js)

##4.路由配置

- [ui.router](http://runjs.cn/code/74vszpdz)<br/>

````
'use strict'

angular.module('app').config(['$stateProvider', '$urlRouterProvider', function ($stateProvider, $urlRouterProvider) {
	$stateProvider.state('main', {
		url: '/main',
		templateUrl: 'view/main.html',
		controller: 'mainCtrl'
	})
	$urlRouterProvider.otherwise('main');
}]);
````

- [路由参数](http://runjs.cn/code/zey9cp7w)<br/>

````
'/home'				--> '/home'

'/home/:id'			--> '/home/123'
'/home/{id}'		--> '/home/123'

'/home/detail?id=123'	--> 非restful传参
````

- 重要指令和服务: [ui-sref](https://ui-router.github.io/ng1/docs/latest/modules/directives.html#uisref), [$state](https://ui-router.github.io/ng1/docs/latest/modules/directives.html#uistate),[directive](https://ui-router.github.io/ng1/docs/latest/modules/directives.html#uisref)

```
// html: 页面跳转
<a ui-sref="main({id: contact.id})" ng-bind="contact.name"></a>
// html
<a ui-sref="contacts.detail({id: contact.id})" ng-bind="contact.name"></a>
// js: 服务定义,replace: 消除当前路径,调回时不会再回到当前页面
$state.go('contacts.detail', {id: contact.id}, {location: 'replace'})
// 参数获取
$state.params.id <===> $stateParams.id
```

