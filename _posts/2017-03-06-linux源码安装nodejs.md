##nodejs安装
- 下载nodejs:
<pre>wget https://nodejs.org/dist/v6.10.0/node-v6.10.0.tar.gz</pre>
- 解压、编译:
<pre>tar xvf node-v6.10.0.tar.gz && cd node-v6.10.0<br/>./configure<br/>make && make install</pre>
- 出现问题:<em>deps/v8/src/base/logging.h:126: 错误:‘nullptr’在此作用域中尚未声明</em>,解决方法:升级g++:<pre>sudo wget http://gcc.skazkaforyou.com/releases/gcc-4.7.2/gcc-4.7.2.tar.gz<br/>tar -zxvf gcc-4.7.2.tar.gz<br/>cd gcc-4.7.2<br/>sudo ./contrib/download_prerequisites<br/>sudo mkdir gcc\_temp<br/>cd gcc\_temp<br/>sudo ../configure --enable-checking=release --enable-languages=c,c++ --disable-multilib<br/>sudo make && sudo make install<br/>sudo mv(or rm) /usr/bin/{gcc,g++} /tmp<br/>sudo ln -s /usr/local/bin/gcc /usr/bin/gcc <br/>sudo ln -s /usr/local/bin/g++ /usr/bin/g++<br/></pre><em>#--enable-languages表示你要让你的gcc支持那些语言，  
\#--disable-multilib不生成编译为其他平台可执行代码的交叉编译器。  
\#--disable-checking生成的编译器在编译过程中不做额外检查，也可以使用--enable-checking=xxx来增加一些检查；</em><br/>

>ps:参考<a href="http://blog.csdn.net/u010376788/article/details/49027853">linux升级gcc/g++</a>