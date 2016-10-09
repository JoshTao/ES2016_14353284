#DOL配置过程
<br/>
本次实验环境在linux下进行，建议使用虚拟机安装Ubuntu
>**安装必要的环境**

* $	sudo apt-get update
* $	sudo apt-get install ant
* $ 	sudo apt-get install openjdk-7-jdk
* $	sudo apt-get install unzip

>**下载必要的文件**


>**解压文件**

新建dol的文件夹
* $	mkdir dol

将dolethz.zip解压到 dol文件夹中

* $	unzip dol_ethz.zip -d dol

解压systemc
* $	tar -zxvf systemc-2.3.1.tgz

>**编译systemc**

解压后进入systemc-2.3.1的目录下
* $	cd systemc-2.3.1

新建一个临时文件夹objdir
* $	mkdir objdir

进入该文件夹objdir
* $	cd objdir

运行configure(能根据系统的环境设置一下参数，用于编译)
* $	../configure CXX=g++ --disable-async-updates

下图为运行之后的截图：

![pic1.jpg](https://github.com/JoshTao/Picture/blob/master/lab1/pic1.jpg)

编译
* $	sudo make install

编译完文件目录如下($ cd .. $ ls：



记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
* $ pwd

进入刚刚dol的文件夹
* $	cd ../dol

修改build_zip.xml文件
找到下面这段话，就是说上面编译的systemc位置在哪里，

\<property name="systemc.inc" value="YYY/include"/>

\<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>

把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）

然后是编译
* $	ant -f build_zip.xml all

若成功会显示build successful

接着可以试试运行第一个例子
进入build/bin/mian路径下

* $	cd build/bin/main

然后运行第一个例子
* $	ant -f runexample.xml -Dnumber=1



