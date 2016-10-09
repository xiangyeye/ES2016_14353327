#### Description 
> DOL is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform.The DOL consists of basically three parts：DOL Application Programming Interface，DOL Functional Simulation and DOL Mapping Optimization.
 
#### How to install   
* **安装一些必要的环境：**
<pre>
$	sudo apt-get update
$	sudo apt-get install ant
$ 	sudo apt-get install openjdk-7-jdk
$	sudo apt-get install unzip
</pre>



* **下载文件：**
 <pre>
sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
</pre>


* **解压文件**

新建dol的文件夹 

`$	mkdir dol`

将dolethz.zip解压到 dol文件夹中

`$	unzip dol_ethz.zip -d dol`

解压systemc

`$	tar -zxvf systemc-2.3.1.tgz`
***

* **编译systemc**

解压后进入systemc-2.3.1的目录下

`$	cd systemc-2.3.1`

新建一个临时文件夹objdir

`$	mkdir objdir`

进入该文件夹objdir

`$	cd objdir`

运行configure(能根据系统的环境设置一下参数，用于编译)

`$	../configure CXX=g++ --disable-async-updates`

结果如下

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/build.jpg" width = "500" alt="configure" />

编译

`$	sudo make install`

编译完后文件目录如下($ cd ..        $ ls

得到的结果如下：

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/mulu.jpg" width = "500" alt="configure" />

***

*   **编译dol**

进入刚刚dol的文件夹

`$	cd ../dol`

修改build_zip.xml文件,
找到下面这段话，就是说上面编译的systemc位置在哪里，

> property name="systemc.inc" value="YYY/include"/>
> 
> property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>

把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）

然后是编译

`$	ant -f build_zip.xml all`

若成功会显示build successful,接着可以试试运行第一个例子进入build/bin/mian路径下

`$	cd build/bin/main`

然后运行第一个例子

`$	ant -f runexample.xml -Dnumber=1`

成功结果如图


<img src="https://raw.githubusercontent.com/xiangyeye/image/master/result.jpg" width = "300" alt="configure" />
