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
- 所有的js，css打包到一个文件中去

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
- gulp-plumber: css编译错误,不会中断进程,而是抛出错误

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

##5.模板和控制器之间的解耦
- 5.1.在自定义模板时指定scope作用域

````
'use strict';

// appPositionList,在html中对应app-position-list
angular.module('app').directive('appPositionList', [function () {
	return {
		restrict: 'A',
		replace: true,
		templateUrl: 'view/template/positionList.html',
		// 修改scope,暴露data接口,降低模板和控制器之间的耦合
		scope: {
			data: '='
		},
		link: function (scope, iElement, iAttrs) {
			
		}
	};
}]);
````

- 模板定义时使用暴露的数据data

````
<ul class="position-list bg-w">
	<!-- 修改scope,暴露data接口,降低模板和控制器之间的耦合-->
	<li class="item" ng-repeat="job in data">
		<img alt="" class="logo f-l" ng-src="{{job.imgSrc}}">
		<h3 class="title" ng-bind="job.name">WEB前端</h3>
		<p class="desc" ng-bind="job.companyName+'['+job.city+']'+job.industry">
			慕课网[北京]互联网
		</p>
		<p class="desc" ng-bind="job.time">2017-04-03 10:09:08</p>
	</li>
</ul>
````

- 使用时，传入控制器中指定data的属性值

````
<div app-position-list data="jobList"></div>
$scope.jobList = [{
	id: 1,
	name: 'WEB前端',
	imgSrc: 'image/company-1.png',
	companyName: '慕课网',
	city: '北京',
	industry: '互联网',
	time: '2017-04-03 10:09:08'
}]
````

##6.名词释义
- 数据绑定(data-binding)

> 在angular应用中，自动同步组件组件和数据之间的行为

- 指令(redirective)

> 1.通过html标签、属性、样式或注释使angular编译器来为指定dom元素绑定特定行为,甚至改变dom和它的子元素<br/>
> 2.内置指令:ng-model,ng-bind,ng-click,ng-class,ng-if,ng-hide,ng-repeat, [示例](http://runjs.cn/code/st3wtuie)<br/>
> > ng-show: 控制是否显示; ng-if: 控制是否存在

> 3.自定义指令:
`scope:继承父scope,子类scope发生变化,不会影响父类scope;暴露接口;@:是一个常量;=:是一个变量;&:是一个回调函数`
> > 指令必须有一个***根dom元素***


##7.控制器（controller）和作用域($scope)
- 控制器: 视图对应的业务逻辑,为数据模型添加行为和属性

> **常用属性**:  
> 1.`$id`:和$scope一一对应，一般是一个值  
> 2.`$parent`:$scope的父作用域,嵌套、或指令  
> 3.`$root`:$rootScope  
> **常用函数:**  
> 1.`$watch`:监控$scope上的属性发生变化（尽量少用,太多会影响性能）  
> 2.`$on`:接收事件  
> 3.`$broadcast`:向下进行广播  
> 4.`$emit`:向上广播  
> 5.`$digest`:双向数据绑定失效时  
> ***<1>.广播时，需要考虑事件的接收方是不是已经初始化完成***  
> ***<2>.绝对、绝对、绝对不要在controller中操作原生dom；如需,要么通过scope数据绑定;要么通过指令来操作***  
> ***<3>.用原生操作dom后,若数据双向绑定失效,可以用$digest()来同步一下***  

##8.服务(service)和服务工厂(factory)
- 特点：  

>单例、懒加载、公用函数

- 常用服务：  

> 1.$scope: 全局作用域  
> 2.$state: 获取参数`$state.params`  
> 3.$http: 网络请求(支持promise语法)  

> ````
> $http({url:'test.json', method: 'get'}).then(function(resp){
> 	// success callback
> }, function(){
> 	// error callbck
> })
> ````

> 4.$q: 解决延迟加载,以及提供promise服务  
> 
> ````
> var functionA(){
> 	var def = $q.defer();
> 	setTimeout(function(){
> 		if(true){ // do something right
> 			def.resolve(); // success
> 		}else{
> 			def.reject(); // err
> 		}
> 	}, 1000);
> 	return def.promise;
> }
> 
> var functionB(){
> 	var def = $q.defer();
> 	setTimeout(function(){
> 		if(true){ // do something right
> 			def.resolve(); // success
> 		}else{
> 			def.reject(); // err
> 		}
> 	}, 1000);
> 	return def.promise;
> }
> 
> $q.all([functionA(), functionB()]).then(function(result){
> 	// do something after the functionA and functionB was resoved
> 	// result's value was the functionA's and functionB's translated result
> })
> ````
> 
> 5.$timeout: 等同于js中timeout  
> 6.$interval: 等同于js中interval  
> 7.$rootScope: 定义公共的函数和变量,所有的子级scope都可以访问到

````
angular.module('app', ['ui.router']).run(['$rootScope', function($rootScope){
	$rootScope.im = function(){
		console.log('hello, im');
	}
}]);
````

- 自定义服务：  

> cache:

````
// servie模式
angular.module('app').service('cache', ['$cookies', function ($cookies) {
	this.put = function (key, value) {
		$cookies.put(key, value);	
	};
	this.get = function (key) {
		return $cookies.get(key);
	};
	this.remove = function (key) {
		$cookies.remove(key);
	};
}]);

// 工厂模式: 可以设置私有属性
angular.module('app').factory('cache', ['$cookies', function ($cookies) {
	return {
		put: function (key, value) {
			$cookies.put(key, value);
		},
		get: function (key) {
			return $cookies.get(key);
		},
		remove: function (key) {
			$cookies.remove(key);
		}
	};
}]);
````



