1.初始化一个React Native项目:<br/>
<pre>
react-native init project1
</pre>
2.初始化完成后，升级项目:<br/>
<pre>
cd project1 && react-native upgrade
</pre>
3.查看版本号:<br/>
<pre>
cd proejct1 && npm list
</pre>
>init后的依赖,在node_modules下载好的,依赖包有新版本的话,不会自动更新

4.使用android手机进行测试:<br/>
>4.1.查看连接是否正常:
<pre>
adb devices
</pre>
4.2.讲调试电脑的8081端口反向代理到测试机上:
<pre>
adb reverse tcp:8081 tcp:8081
</pre>

5.编译项目:
<pre>
react-native run-ios
react-native run-android
</pre>
6.启动项目:
<pre>
react-native start
</pre>
