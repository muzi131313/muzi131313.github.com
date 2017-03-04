<style>
a{text-decoration: none;}
a:link{text-decoration: none;}
a:visited{text-decoration: none;}
a:hover{text-decoration: none;}
a:active{text-decoration: none;}
</style>

1.官网:<br/>
<a href="http://facebook.github.io/react-native/docs/getting-started.html#content">开始react-natvie</a>

2.安装HomeBrew命令:<br/>
<pre>
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
</pre>

3.安装NVM命令:<br/>
<pre>
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
</pre>
或者:<br/>
<pre>
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
</pre>

4.编辑.bash\_profile文件:<br/>
<pre>
export NVM_DIR="/Users/liyanfeng/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
</pre>
5.安装node:<br/>
<pre>
nvm install node && nvm alias default node;
</pre>

6.获取权限:<br/>
<pre>
sudo chown -R $USER /user/local/lib
sudo chown -R $USER /user/local
</pre>

7.安装wathman和flow:<br/>
<pre>
brew install watchman && brew install flow
</pre>
8.安装react-native-cli:<br/>
<pre>
sudo npm install -g react-native-cli
</pre>
ps:react-native全局变量会破坏ReactNatvie环境,查看全局安装的命令:
<pre>
npm list -g
</pre>
9.安装代码检测插件:<br/>
<pre>
npm install -g JSHint
which jshint
</pre>