##LAB2:版本控制&文档##

### DOL框架描述: ###
The distributed operation layer (DOL) is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform. The DOL
consists of basically three parts:

**1. DOL Application Programming Interface**

**2. DOL Functional Simulation**

**3. DOL Mapping Optimization**
### 安装笔记 :###
1.安装必要的环境，使用的系统是ubuntu

- `sudo apt-get update`
- `sudo apt-get install ant`
- `sudo apt-get install openjdk-7-jdk`
- `sudo apt-get install unzip`

2.安装文件


- sudo wget [http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz](http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz)
- sudo wget [http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip](http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip)

3.新建dol文件夹，解压dol_ethz.zip和systemc-2.3.1.tgz

- `mkdir dol`
- `unzip dol_ethz.zip -d dol`
- `tar -zxvf systemc-2.3.1.tgz`

4.编译systemc

- 进入systemc-2.3.1的目录 (`cd system-2.3.1`)
- 新建一个临时文件夹objdir (`mkdir objdir`)
- 进入该文件夹（`cd objdir`）
- 运行configure(`../configure CXX=g++ --disable-async-updates`)
- ![ss](https://github.com/WeaklyChicken/ES2016_14353087/scompile.png)
- 编译（`sudo make install`）
- ![ss](https://github.com/WeaklyChicken/ES2016_14353087/scompile2.png)
- 记录当前工作路径后面有用到（`pwd`),我的结果是
(`/home/humingcongubuntu/systemc-2.3.1`) 

5.编译dol

在此之前我们需要先修改build_zip.xml文件。在该文件中找到

	`<property name="systemc.inc" value="YYY/include"/>`

	`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`

并把YYY改成上面记录到的工作路径。然后编译

	`ant -f build_zip.xml all`
接着运行第一个例子。进入build/bin/main路径

	`cd build/bin/main`
然后运行

	`ant -f runexample.xml -Dnumber=1`
得到如下结果则说明成功

![ss](https://github.com/WeaklyChicken/ES2016_14353087/exampleResult.png)





    
