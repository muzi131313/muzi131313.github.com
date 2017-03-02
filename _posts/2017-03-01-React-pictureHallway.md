<style>
a{text-decoration: none;}
a:link{text-decoration: none;}
a:visited{text-decoration: none;}
a:hover{text-decoration: none;}
a:active{text-decoration: none;}
</style>

1.react生命周期:<br/>

2.脚手架工具【yeoman】:<br/>
<a href="http://yeoman.io">官网</a><br/>

3.查看全局generator生成列表:<br/>
<pre>
npm ls -g --depth=1 2>/dev/null | grep generator-
</pre>

4.安装generator-react-webpack:<br/>
<pre>
npm install -g generator-react-webpack
</pre>

4.创建初始化项目:<br/>
<pre>
yo react-webpack your-project-name
</pre>

5.脚手架说明:<br/>
.editorconfig: 不同编辑器统一风格,<a href="http://editorconfig.org">官网</a><br/>
.gitignore: git提交过滤的文件、目录<br/>
.eslintrc:包含jshintrc<br/>
.jshintrc:<br/>
.yo-rc.json:<br/>
karma.conf.js:测试文件<br/>
package.json:node依赖<br/>
webpack.config.js:webpack开发环境配置<br/>
webpack.dist.config.js:webpack生产环境配置<br/>

6.react全局对象:<br/>
<pre>
\_\_REACT\_DEVTOOLS\_GLOBAL\_HOOK\_\_
</pre>

7.webpack配置:<br/>
<a href="webpack.github.io">官网</a><br/>
output:输出<br/>
entry:输入<br/>
resolve:模块解析项<br/>
cache:true: 增量编译<br/>
debug:true: 调试模式<br/>
devtool:'sourcemap': <br/>
stats: {<br/>
	colors: true, // 颜色<br/>
	reasons: true // 为什么被引入<br/>
}: 输入相关<br/>

webpack-dev-server:{
	hot: true, // 热部署
}<br/>
plugins: {<br/>
	DedupePlugin(): 检测相似文件、或者文件中重复内容<br/>
	UglifyJsPlugin(): 压缩输出<br/>
	OccurenceOrderPlugin(): 根据引用频率决定bind-id，越频繁、值越短，达到减小文件目的<br/>
	AggressiveMergingPlugin(): 用来优化生成的代码chunk，合并相同代码，提取公共的相同的代码片段<br/>
	NoErrorsPlugin(): 保证编译不会出错<br/> 
}
>##ps:备注<br/>
>1.dev模式下,output生成在内存中，而非磁盘中<br/>
 2.__dirname:当前目录<br/>
 3.localhost:port/webpack-dev-server:建议访问url
 4.transpiling(相同层级的编译:ES6->ES5)/compiling(不同层级的编译)

8.grunt beginner:
