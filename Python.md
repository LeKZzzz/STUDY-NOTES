# **Python**

------

# 边边角角

##	特性

1. 解释型语言：无编译环节，需要解释器

2. 跨平台的计算机程序设计语言，支持Windows、Linux、Mac
3. 交互式语言：可以再命令提示符“>>>”后直接执行，比如cmd、Python源文件下的交互式命令行程序
4. 面向对象，Python中的一切都是对象



##	安装目录下各文件作用

1. IDLE是python自带的集成开发环境，可以运行调试代码，编写代码并保存等等
2. Python3.x(64-bit)是交互式python环境，这里写的代码不能保存到文件中。命令提示符输入python就是运行了这个文件。
3. Python3.x Module docs打开可以看到本机已安装的各种python的包的信息。



##	Python文件的后缀名

1. .py：

   以 py 扩展名的文件是 Python 源码文件，由 python.exe 解释，可在控制台下运行。可用文本编辑器读写。

2. .py3：

   Python3脚本（Python3脚本通常以.py而不是.py3结尾，很少使用）。

3. .pyc：

   以 pyc 为扩展名的是Python的编译文件。其执行速度快于 py 文件且不能用文本编辑编辑查看。所以 pyc 文件往往代替 py 文件发布。

   Python 在执行时，首先会将 py 文件中的源代码编译成 PyCodeObject 写入 pyc 文件，再由虚拟机执行 PyCodeObject。当 Python 执行 import 时会先寻找对应的 pyc或 pyd（dll）文件，如果没有则将对应的py文件编译写入 pyc 文件。pyc文件也可以通过 `python -m py_compile src.py` 生成。

   .pyc二进制文件可以反编译成.py文件，反编译软件叫Easy Python Decompiler。

4. .pyo：

   pyo 是优化编译后的程序，不能用文本编辑器编辑。 `python -O source.py` 即可将源程序编译为 pyo 文件。

   这是在优化(-O)时创建的*.pyc文件，从Python3.5开始，Python将只使用.pyc而不是.pyo和.pyc。

5. .pyd：

   这基本上是一个Windows DLL文件。

   pyd 一般是 Python 外的其他语言如 C/C++ 编写的 Python 扩展模块，即 Python 的一个动态连接库，与 dll 文件相当。在Linux系统中一般为.so文件

6. .pyi：

   MyPy存根，存根文件（PEP 484）。

7. .pyw：

   用pythonw.exe执行的Windows的Python脚本。

   pyw 文件与 pyc 文件相似，但 pyw 执行的时候不会出控制台窗口。开发（纯图形界面程序）时可以暂时把 pyw 改成 py 以调出控制台窗口调试。

8. .pyx：

   将Cython src转换为C/C++。

9. .pyz：

   Python脚本归档（PEP 441）（这是一个包含标准Python脚本头之后的二进制形式的压缩Python脚本（ZIP）的脚本）。

10. .pywz：

    用于MS-Windows的Python脚本归档（PEP 441）（这是一个包含标准Python脚本头之后的二进制形式的压缩 Python脚本（ZIP）的脚本）。

11. .py [cod]：

    .gitignore中的通配符表示该文件可能是.pyc，.pyo或.pyd。

12. .rpy：

    包含应用程序或框架特定功能的RPython脚本或Python脚本。

13. .pyde：

    处理使用的Python脚本。

14. .pyp：

    Py4D Python插件。

15. .pyt：

    Python声明文件。



## pip

| 序号                               | 语法                                                        |
| ---------------------------------- | ----------------------------------------------------------- |
| 在线安装                           | pip install somepackage                                     |
| 在线安装指定版本                   | pip install robotframework==2.8.7                           |
| 通过whl文件离线安装拓展库          | pip install somepackage.whl                                 |
| 卸载已安装的库                     | pip uninstall package                                       |
| 列出已经安装模块及其版本号         | pip list pip freeze                                         |
| 将已经安装的库列表保存到文本文件中 | pip freeze > path                                           |
| 根据依赖文件批量安装库             | pip install -r requirements.txt                             |
| 显示所安装包的信息                 | pip show package pip show -f package                        |
| 升级指定的包                       | pip install -U package   pip install --upgrade 要升级的包名 |
| 指定pip源                          | pip install somepackage -i url                              |



1. 清华源：https://pypi.tuna.tsinghua.edu.cn/simple/
2. 阿里云源：https://mirrors.aliyun.com/pypi/simple/
3. 中国科技大学源：https://pypi.mirrors.ustc.edu.cn/simple/
3. 豆瓣(douban)： https://pypi.douban.com/simple/
3. 中国科学技术大学：http://pypi.mirrors.ustc.edu.cn/simple/



多个python环境下，在指定的版本下pip安装包:

1. 将要安装的python版本放在环境变量变量前面
2. 指定python 版本安装
   1. python2: py -2 -m pip install lettuce
   2. python3:py -3 -m pip install lettuce
3. 使用全路径安装
   1. python2: C:\Users\LeK\AppData\Local\Programs\Python\Python27\python.exe -m pip install lettuce
   2. python3: C:\Users\LeK\AppData\Local\Programs\Python\Python37\python.exe -m pip install lettuce
4. 修改python.exe的文件名
   1. python2：python2 -m pip install lettuce
   2. python3：python3 -m pip install lettuce



##	GIL(global interpreter lock)

> 由于物理上得限制，各CPU厂商在核心频率上的比赛已经被多核所取代。为了更有效的利用多核处理器的性能，就出现了多线程的编程方式，而随之带来的就是线程间数据一致性和状态同步的困难。即使在CPU内部的Cache也不例外，为了有效解决多份缓存之间的数据同步时各厂商花费了不少心思，也不可避免的带来了一定的性能损失。
>
> Python当然也逃不开，为了利用多核，Python开始支持多线程。而解决多线程之间数据完整性和状态同步的最简单方法自然就是加锁。 于是有了GIL这把超级大锁，而当越来越多的代码库开发者接受了这种设定后，他们开始大量依赖这种特性（即默认python内部对象是thread-safe的，无需在实现时考虑额外的内存锁和同步操作。
>
> 慢慢的这种实现方式被发现是低效的。但当大家试图去拆分和去除GIL的时候，发现大量库代码开发者已经重度依赖GIL而非常难以去除了。有多难？做个类比，像MySQL这样的“小项目”为了把Buffer Pool Mutex这把大锁拆分成各个小锁也花了从5.5到5.6再到5.7多个大版为期近5年的时间，而且仍在继续。MySQL这个背后有公司支持且有固定开发团队的产品走的如此艰难，那又更何况Python这样核心开发和代码贡献者高度社区化的团队呢？
>
> 所以简单的说GIL的存在更多的是历史原因。如果推倒重来，多线程的问题依然还是要面对，但是至少会比目前GIL这种方式会更优雅。

1. GIL的全称是 Global Interpreter Lock，全局解释器锁。之所以叫这个名字，是因为**Python的执行依赖于解释器**。Python最初的设计理念在于，**为了解决多线程之间数据完整性和状态同步的问题，设计为在任意时刻只有一个线程在解释器中运行。**而当执行多线程程序时，由GIL来控制同一时刻只有一个线程能够运行。即**Python中的多线程是表面多线程**，也可以理解为fake多线程，不是真正的多线程。

2. 需要明确的一点是GIL并不是Python的特性，它是在实现Python解析器(CPython)时所引入的一个概念。就好比C++是一套语言（语法）标准，但是可以用不同的编译器来编译成可执行代码。有名的编译器例如GCC，INTEL C++，Visual C++等。Python也一样，同样一段代码可以通过CPython，PyPy，Psyco等不同的Python执行环境来执行。像其中的JPython就没有GIL。然而因为CPython是大部分环境下默认的Python执行环境。所以在很多人的概念里CPython就是Python，也就想当然的把GIL归结为Python语言的缺陷。所以这里要先明确一点：GIL并不是Python的特性，Python完全可以不依赖于GIL。

3. 同一时刻只有一个线程能够运行，那么是怎么执行多线程程序的呢？其实原理很简单：**解释器的分时复用**。即多个线程的代码，轮流被解释器执行，只不过切换的很频繁很快，给人一种多线程“同时”在执行的错觉。聊的学术化一点，其实就是“**并发**”。

4. GIL的优点是显而易见的，GIL可以保证我们在多线程编程时，无需考虑多线程之间数据完整性和状态同步的问题。

   GIL缺点是：我们的多线程程序执行起来是“并发”，而不是“并行”。因此执行效率会很低，会不如单线程的执行效率。

   网上很多人都提到过这样的疑问：”为什么我多线程Python程序运行得比其只有一个线程的时候还要慢?“显然，大家觉得一个具有两个线程的程序要比其只有一个线程时要快。事实上,这个问题是确实存在的，原因在于GIL的存在使得Python多线程程序的执行效率甚至比不上单线程的执行效率。很简单，由于GIL使得同一时刻只有一个线程在运行程序，再加上切换线程和竞争GIL带来的开销，显然Python多线程的执行效率就比不上单线程的执行效率了。

    



#	编写规范

Python中采用PEP 8（Python Enhancement Proposal version 8）作为编写规范

**PEP 8：**

1. 每个import语句只导入一个模块
2. 不要在行尾添加分号"**;**",也不要用分号将两条命令放在同一行
3. 建议每行不超过80个字符，建议使用"**()**"将多行内容隐式连接而不采用反斜杠"\\"（除非是导入模块的语句过长或注释里的URL）
4. 使用必要的空行可以增强代码的可读性，一般在顶级定义之间空两行，方法定义之间空一行
5. 通常情况下，运算符两侧、函数参数之间、"**,**" 两侧建议用空格进行分隔
6. 尽量避免在循环中使用"+"和"+="运算符累加字符串

**生成器表达式为什么不叫生成器推导式：**

PEP 289 —— 生成器表达式 的最后给出了详细的备注，其中指出Raymond Hettinger起初提议使用“生成器推导式（generator comprehension）”一词，后来Peter Norvig提出了“累计显示（accumulation displays）”，后来Tim Peters推荐了“生成器表达式”这个名词。
Guido指出了核心原因：
推导式一开始属于“字面量显示（literal display）”这一概念。而生成器表达式不是一种显示（display）。
Matt Boehm后来找到了Tim Peters提出“生成器表达式”一词的邮件，其中讲述了一些细节：
首先，为什么会使用“推导式”（comprehension）一词？Tim在邮件中指出，这个词来源于集合论中的推导公理（Axiom of Comprehension），它指的是通过对另一个集合的元素应用某个谓词（predicate，即条件）而组成新的集合。这和向另一个序列中的元素应用某个条件从而生成列表的做法非常类似。
EarlGrey：我之前看到很多翻译为“解析”，看到这里才觉得“推导式”才是更准确的说法。
正如Guido所指出的，Python的设计者当时更注重的是显示，而不是条件。“显示”一词在这里意味着代码的语法看上和它将创建的数据结构很像。列表显示（列表推导式）看上去像一个列表。对于集合和字典显示来说，也是一样的道理。但是由于没有生成器字面量语法，因此根本就没有一个生成器显示可以进行对比，也就不存在生成器显示了。
在设计该功能的那封邮件中，“推导式”是“显示”的同义词，由于生成器没有显示，所以也不可能有推导式。
不过Time在他的邮件中也说到，推导式的奇妙之处在于条件。推导公理的核心则是谓语。也许是因为Python推导式中的条件是可选的，关注的焦点被转移到了显示方面。



#	命名规范

1. 模块、函数、类的属性、方法的命名尽量短且全部使用小写字母，可使用下划线分隔多个字母
2. 包名尽量短小且全部使用小写字母，不推荐使用下划线
3. 类名采用单词首字母大写的形式
3. 模块内部的类采用下划线加单词首字母大写的类名组成
3. 常量命名时全部使用大写字母，可以使用下划线
3. 以单下划线"_"开头的模块变量或者函数是受保护的，在使用from xx import *语句从模块导入时这些变量或者函数不能被导入
3. 以双下划线"__" 开头的代表类的私有成员
3. 以双下划线开头和结尾的代表 Python 里特殊方法专用的标识，如"\__init__()" 代表类的构造函数。



#	虚拟环境 virtualenv(venv)

venv是一个虚拟环境管理器，作为非数据科学领域的开发者来说是很实用的。它可以让你每个项目甚至每个脚本配置一个自定义的Python解释器环境，这最大的好处是可以**不污染开发环境**。

如果把包安装在解释器源文件夹中，假设做项目A，用的包版本要是selenium2.48.0 和 lxml=1.0.0，做项目B 必须用包版本是selenium2.50.0 和 lxml =1.2.0，那就要把selenium2.48.0 和 lxml=1.0.0卸载了并安装selenium2.50.0 和 lxml =1.2.0，但是这样换做类似项目A的包版本要求又得把以前的卸载了，装回selenium2.48.0 和 lxml=1.0.0，这样来来去去很麻烦，所以不如创建虚拟环境A装selenium2.48.0 和 lxml=1.0.0和虚拟环境B装selenium==2.50.0 和 lxml =1.2.0，做项目A就用虚拟环境A，项目B用虚拟环境B，互不干扰就方便多了。

venv可以创建任意多个虚拟环境，只要指定当前环境那么pip安装的包就只会在这个环境下，这个环境和操作系统部署的python环境是隔离的，这样可以分门别类常见虚拟环境，互不污染。（如机器学习和爬虫不干涉）其次，一旦我不使用了，可以直接删除虚拟环境，而不用管各种文件残留，关联问题了。



#	conda

如果说venv是虚拟环境管理器，pip是包管理器，那么conda则是两者的结合。
遗憾的是conda的包管理器做的一般且会安装过多依赖，如TensorFlow自动安装cudnn（在主机配置了cudnn的情况下），大多数时候还是使用pip安装包。
但是pip只能安装Python的包，conda可以安装一些工具软件，即使这些软件不是基于Python开发的。
但是conda的虚拟环境管理还是可以的，一般使用venv会在该项目下创建虚拟环境，再不济也会在项目下创建venv的文件夹（含配置文件），当然pycharm下创建虚拟环境另说；然而conda每个虚拟环境不会占用项目文件夹的空间，它创建在用户设定的一个位置，这使得多个项目共享一个虚拟环境更加方便（只是方便，venv也是可以的，但是venv一般占用项目文件夹空间，而且venv命令行使用具有局限性）。
conda虚拟环境是独立于操作系统解释器环境的，即无论操作系统解释器什么版本（哪怕2.7），我也可以指定虚拟环境python版本为3.6（见文章开头所说原博客），而venv是依赖主环境的。
对于科学计算和大数据领域的人，conda是环境自动集成了numpy这样的主流科学计算包的，venv每个包都要自行下载。
conda有图形化环境管理器，venv没有。（虽然开发人员几乎不用图形界面conda）



# Pycharm

https://www.bilibili.com/medialist/play/watchlater/BV1aN411o7Ei

## 快捷键

![](Pictures\Pycharm快捷键1.png)

![image-20220204150042206](Pictures\Pycharm快捷键2.png)

![](Pictures\Pycharm快捷键3.png)

自动调整代码格式的快捷键，默认为	`Alt+Ctrl+L`

pycharm在执行后将光标移到执行界面窗口	`alt+4`



##	Debug

1. 断点所在代码行变蓝，意味着Pycharm程序进程已经到达断点处，但尚未执行断点所标记的代码
2. 步过：单步执行，在函数内遇到子函数时不会进入子函数内，而是将子函数整个执行完再停止，也就是把子函数整个作为一步
3. 步进：单步执行时，遇到子函数就进入并且继续单步执行(包括源代码函数)
4. 单步执行我的代码：在单步执行时，遇到子函数就进入并且继续单步执行，不会进入到源码中
5. 步出：跳出当前函数体
6. 评估表达式：计算表达式
7. 恢复程序：直接运行到下一断点处
8. debug错误：
   1. 关闭Pycharm，删除工程目录下的.idea文件夹并重启
   2. 删除所有的断点。可以点击下图所示的两个叠在一起的红色原点进行操作
   3. 点击Pycharm的File>>Invalidate Caches / Restart…，然后选择Invalidate and Restart。这个操作清空了项目中的缓存信息
   4. 重建整个工程并重新配置



## TODO

待完成代码

```python
#	TODO（“xxx”）
```



##	新建文件模板配置

```python
${PROJECT_NAME} - 当前项目的名称。

${NAME} - 在文件创建过程中在“新建文件”对话框中指定的新文件的名称。

${USER} - 当前用户的登录名。

${DATE} - 当前的系统日期。

${TIME} - 当前系统时间。

${YEAR} - 今年。

${MONTH} - 当月。

${DAY} - 当月的当天。

${HOUR} - 目前的小时。

${MINUTE} - 当前分钟。

${PRODUCT_NAME} - 将在其中创建文件的IDE的名称。

${MONTH_NAME_SHORT} - 月份名称的前3个字母。 示例：1月，2月等

${MONTH_NAME_FULL} - 一个月的全名。 示例：1月，2月等
```



##	pycharm项目中的文件夹

1. .idea文件夹

   这个文件夹的主要作用在于存放项目的控制信息，包括版本信息，历史记录等等，删除它是不会影响代码的正常使用的，但是如果删除就不能使用pycharm进行回溯和复原了

2. venv文件夹

   项目的虚拟环境(virtualenv)设置，存储项目的外部包
   
   其中的.gitignore文件会令venv文件夹无法被Git追踪



#	模块（Module）

为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，在Python中，一个`.py`文件就称之为一个模块。

**相同**名字的函数和变量完全**可以**分别存在不同的模块中，但尽量不要与内置函数名字冲突。

在调用模块中的函数、变量或者类时，需要在其前面加上"**模块名.**"作为前缀

模块名是**区分字母大小写**的，不能以数字开头

推荐先导入标准模块，再导入第三方模块，最后导入自定义模块



##	模块导入

用 **import** 或者 **from...import** 来导入相应的模块。

在导入模块时可以使用as关键字为其设置一个别名，方便调用模组

==**导入模块时会自动在搜索路径中寻找对应的模块，如果发现就会立即导入，然后运行这个模块的源码并进行初始化**==

在使用import语句导入模块时，每执行一条import语句都会创建一个命名空间(namespace)并且在该命名空间中执行与模块相关的所有语句，如果不想在每次导入模块时都创建一个命名空间可以使用**from...import**语句，该语句可以将具体的定义导入到当前的命名空间中，调用时**无须添加前缀**可直接进行访问，但需保证导入的定义在当前的命名空间中是唯一的，否则后导入的同名定义会覆盖先导入的

> ​	命名空间命名空间是一个包含了变量名称们（键）和它们各自相应的对象们（值）的字典，可以理解为记录对象名字和对象之间对应关系的空间

1. 将整个模块(somemodule)导入

   ```python
   import modulename [as alias]
   ```

   >[as alias]：给模块起的别名

   同时导入多个模块可以使用"**,**"分隔

2. 从某个模块中导入某个定义

   ```python
   from modulename import somefunction [as alias]
   ```

   同时导入多个函数可以使用"**,**"分隔

4. 将某个模块中的全部定义导入

   ```python
   from modulename import *
   ```
   
   使用通配符*导入全部定义后可以通过显示dir()函数的值查看具体导入了哪些定义，dir() 函数一个排好序的字符串列表，内容是一个模块里定义过的名字，返回的列表容纳了在一个模块里定义的所有模块，变量和函数。
   该方法引入的模块(包)的子模块(包)无法引入



##	模块搜索目录

使用import语句导入模块时，默认情况下会按照一定顺序对模块进行查找

> 1. 在当前目录下查找(即执行的Python脚本文件所在目录)
> 2. 在 shell 变量PYTHONPATH(环境变量)下的每一个目录中查找
> 3. 在Python的默认安装目录下查找
>
> 以上各个目录的具体位置保存在标准模块sys的sys.path变量中

1. 临时添加

   ```python
   import sys
   sys.path.append("file path")
   ```

   该方法只在执行当前文件的窗口中有效，窗口关闭后即失效

2. 增加.pth文件

   在Python安装目录下的Lib\site-packages子目录中创建一个拓展名为.pth的文件，在该文件中添加要导入模块所在的目录

   创建.pth文件后需要重新打开要执行导入模块的Python文件

   通过该方法添加的目录只在当前版本的Python中有效

3. 在PYTHONPATH环境变量中添加

   需要重新打开要执行导入模块的Python文件

   通过该方法添加的目录可以在不同版本中共享



##	以主程序运行
在Python程序中，`__name__`属性可以识别程序的入口，可以判断该程序是作为模块被导入还是作为主程序运行，如果作为模块被导入，则其属性的值会被自动设置为模块名；如果作为程序直接运行，则其属性的值被自动设置为字符串`"__main__"`

为了导入模块时不执行模块中的某些操作，可以使用以主程序运行的方法，即在模块中将其放入一个if语句中

```python
if __name__ == "__main__":
    block
```

添加该语句后，只有以模块本身为入口才会执行函数体

> ​	每个模块的定义中都包含一个记录模块名称的变量\__name__，程序可以检查这个变量以确定它们是在那个模块中执行
>
> ​	顶级模块的`__name__`变量的值为`__main__`



##	引用标准模块和第三方模块

1. 内置标准模块，又称为标准库，如 sys、time、math、json 模块等。内置 Python 模块一般都位于安装目录下 Lib 文件夹中

   标准库：https://blog.csdn.net/weixin_43413451/article/details/120170568

   帮助文档：Python安装路径下的Doc目录，拓展名为.chm的文件

2. 第三方模块可以在Python官方推出的https://pypi.org/ 中找到

   下载和安装第三方模块可以使用pip命令实现

   ```python
   pip <command> [modulename]
   ```

   > command：指定要执行的命令，如install、uninstall、list





#	包（Package）

为了避免模块名冲突，Python又引入了按目录来组织模块的方法，称为**包（Package）**。

包是一个分层次的目录结构，它将一组功能相近的模块组织在一个目录下

假设我们的`abc`和`xyz`这两个模块名字与其他模块冲突了，于是我们可以通过包来组织模块，避免冲突。方法是选择一个顶层包名，比如`mycompany`，按照如下目录存放：

> mycompany
>
> > \__init__.py
> >
> > abc.py
> >
> > xyz.py

引入了包以后，只要顶层的包名不与别人冲突，那所有模块都不会与别人冲突。现在，`abc.py`模块的名字就变成了`mycompany.abc`，类似的，`xyz.py`的模块名变成了`mycompany.xyz`。（类似于C语言中的结构体，abc.py、xyz.py变成了结构体中的成员）



##	创建包

创建包实际上就是创建一个文件夹，并且在该文件夹中创建一个名称为"\__init__.py"的Python文件。

在\__init__.py文件中可以不编写任何代码

在\__init__.py文件中所编写的代码会在导入包时自动执行，相当于初始化模块文件



##	使用包

在包中创建相应模块之后就可以使用import语句从包中加载模块

1. import+完整包名+模块名

   ```python
   import settings.size
   ```

   使用该形式导入模块后，调用模块时需要带包前缀

2. from+完整包名+import+模块名

   ```python
   from settings import size
   ```

   使用该形式导入模块后，调用模块时可不带包前缀

3. from+完整包名+模块名+import+定义名

   ```python
   from settings.size import a,b
   ```

   使用该形式导入定义后，可直接使用定义

   可使用通配符*导入全部定义





#	输入输出

1. 使用input()输入

   xx=input("提示文字")

   1. 在Python 3.x中该函数输入均视为字符串读取
   2. 在Python 2.x中该函数可直接输入数值，输入字符串需要将字符串用双引号括起来

2. 使用print(value,...,sep='',end='',file='',flush=False)输出

   1. 输出类型：

      1. 变量(字符串需要用引号括起来)
      2. 含有运算符的表达式

   2. 默认输出是换行的，如果要实现不换行可在变量末尾加上 **,end=" "**

      print( x, end=" "，sep=" " )

   3. 输出多个变量可用"**,**"分隔
   
   4. 格式化输出形同C语言
   
      ```python
      print("%_"%(_))
      ```
   
      ![](Pictures\Python格式化操作符辅助指令.png)
   
      ![Python格式化输入输出](Pictures\Python格式化输入输出.png)
      
   5. 多行输入
   
      1. 利用异常处理机制实现
   
         ```Python
         lines=[]
         while True:
             try:
                 lines.append(input())
             except:
                 break 
         print(lines)
         ```
   
         当输入最后一行并回车后，按组合键ctrl+D，表示EOF，即End of File、文件尾的意思。此时，input()函数会遇到EOF的异常。Python的异常处理机制将捕获到此异常，执行except部分的语句，此语句为break，因此，立即跳出while循环。
   
      2. 利用标准输入文件对象sys.stdin的readlines()函数实现
   
         ```python
         import sys
         lines=sys.stdin.readlines()
         print(lines)
         ```
   
         当输入最后一行并回车后，按组合键ctrl+D，表示EOF，即End of File、文件尾的意思。
   
         这种方式2与方式1的输出结果有细微差别，每行末尾有'\n'字符（即回车符）



#	文件及目录操作

在Python中内置了File(文件)对象

| 序号 | 方法及描述                                                   |
| :--- | :----------------------------------------------------------- |
| 1    | file.close()关闭文件。关闭后文件不能再进行读写操作。         |
| 2    | file.flush()刷新文件内部缓冲，直接把内部缓冲区的数据立刻写入文件, 而不是被动的等待输出缓冲区写入。 |
| 3    | file.fileno()返回一个整型的文件描述符(file descriptor FD 整型), 可以用在如os模块的read方法等一些底层操作上。 |
| 4    | file.isatty()如果文件连接到一个终端设备返回 True，否则返回 False。 |
| 5    | file.next()**Python 3 中的 File 对象不支持 next() 方法。**返回文件下一行。 |
| 6    | file.read([size\])从文件读取指定的字节数，如果未给定或为负则读取所有。 |
| 7    | file.readline([size\])读取整行，包括 "\n" 字符。             |
| 8    | file.readlines([sizeint\])读取所有行并返回列表，若给定sizeint>0，返回总和大约为sizeint字节的行, 实际读取值可能比 sizeint 较大, 因为需要填充缓冲区。 |
| 9    | file.seek(offset[, whence\])移动文件读取指针到指定位置       |
| 10   | file.tell()返回文件当前位置。                                |
| 11   | file.truncate([size\])从文件的首行首字符开始截断，截断文件为 size 个字符，无 size 表示从当前位置截断；截断之后后面的所有字符被删除，其中 windows 系统下的换行代表2个字符大小。 |
| 12   | file.write(str)将字符串写入文件，返回的是写入的字符长度。    |
| 13   | file.writelines(sequence)向文件写入一个序列字符串列表，如果需要换行则要自己加入每行的换行符。 |

1. 创建和打开文件

   open() 方法用于打开一个文件，并返回文件对象，默认为文本模式，如果该文件无法被打开，会抛出 OSError

   ```python
   file=open(filename[,mode[,buffering]])
   
   完整的语法格式为：
   open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
   ```

   > file：被创建的文件对象
   >
   > filename：要创建或打开的文件名称，需要使用单引号或者双引号括起来。如果要打开的文件和当前文件在同一目录下可直接填写文件名，否则需要指定完整路径
   >
   > mode：可选参数，用于指定文件的打开模式，默认为只读
   >
   > buffering：可选参数，用于指定读写文件的缓冲模式，值为0表示不缓存，值为1表示缓存，值大于1表示缓冲区的大小，默认为缓存模式
   >
   > encoding: 默认为GBK，一般使用UTF-8
   >
   > errors: 报错级别
   >
   > newline: 区分换行符
   >
   > closefd: 传入的file参数类型
   >
   > opener: 设置自定义开启器，开启器的返回值必须是一个打开的文件描述符。

   | mode参数 | 描述                                                         |
   | :------- | :----------------------------------------------------------- |
   | t        | 文本模式 (默认)。                                            |
   | x        | 写模式，新建一个文件，如果该文件已存在则会报错。             |
   | b        | 二进制模式。                                                 |
   | +        | 打开一个文件进行更新(可读可写)。                             |
   | U        | 通用换行模式（**Python 3 不支持**）。                        |
   | r        | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
   | rb       | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。 |
   | r+       | 打开一个文件用于读写。文件指针将会放在文件的开头。           |
   | rb+      | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。 |
   | w        | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
   | wb       | 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
   | w+       | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
   | wb+      | 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
   | a        | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
   | ab       | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
   | a+       | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。 |
   | ab+      | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写 |

2. 关闭文件

   关闭后文件不能再进行读写操作

   使用 open() 方法一定要保证关闭文件对象，即调用 close() 方法

   ```python
   file.close()
   ```

   > close()方法会先刷新缓冲区中还没有写入的信息，然后再关闭文件

3. with语句

   **with** 语句用于异常处理，封装了 **try…except…finally** 编码范式，提高了易用性

   如果在调用 write 的过程中，出现了异常，则 close()方法将无法被执行，因此资源就会一直被该程序占用而无法被释放，导致无法关闭

   使用with语句时，无论是否抛出异常都能保证with语句执行完毕后关闭已经打开的文件

   ```python
   with expression as target:
   	with-body
   ```

   > expression：指定一个表达式
   >
   > target：指定一个变量，将expression的结果保存在该变量中
   >
   > with-body：指定with语句体，可以是执行with语句后相关的一些操作，也可以用pass语句代替

   ```python
   file = open('./test_runoob.txt', 'w')
   file.write('hello world !')
   file.close()
   
   file = open('./test_runoob.txt', 'w')
   try:
       file.write('hello world')
   finally:
       file.close()
   
   with open('./test_runoob.txt', 'w') as file:
       file.write('hello world !')
   ```

   使用 **with** 关键字系统会自动调用 f.close() 方法， with 的作用等效于 try/finally 语句是一样的

   >with 语句实现原理建立在上下文管理器之上
   >
   >上下文管理器是一个实现 `__enter__` 和`__exit__`方法的类
   >
   >使用 with 语句确保在嵌套块的末尾调用 `__exit__` 方法
   >
   >这个概念类似于 try...finally 块的使用
   >
   > 首先调用 `__enter__ `方法，然后执行 with 语句中的代码，最后调用 `__exit__` 方法。 即使出现错误，也会调用 `__exit__` 方法，也就是会关闭文件流

4. 写入文件内容

   ```python
   file.write(string)
   
   file.writelines()		#将字符串列表写入文件，但是不添加换行符
   ```
   
   > 在写入文件内容时，操作系统不会立刻把数据写入文件，而是先缓存起来，可以调用close()方法将缓存中的数据写入文件并关闭文件，也可以使用flush()方法将缓冲区的内容写入文件而不关闭文件
   
5. 读取文件

   ```python
   file.read([size])
   
   file.readline()		#每次读取一行数据
   
   file.readlines()	#读取全部行，返回的是一个字符串列表，每个元素为文件的一行内容
   ```

   > file：打开的对象
   >
   > size：可选参数，指定读取的字符个数，默认一次性读取所有内容

   read()方法从文件的开头读取

   读取部分内容需要先用seek()方法将文件的指针移动到指定位置

   ```python
   file.seek(offset[,whence])
   ```

   >offset：指定移动的字符个数
   >
   >whence：指定起始位置，值为0表示从文件头开始，值为1表示从当前位置开始，值为2表示从文件尾开始，默认为0

   对于whence参数，如果在打开文件时没有使用"b"模式，那么只允许从文件头开始计算相对位置

   > 在使用seek方法时，如果采用GBK编码，那么offset的值是按一个汉字(包括中文标点符号)占两个字符计算，而采用UTF-8编码，则一个汉字占3个字符，这**与read()方法不同**
   
6. 目录操作

   目录也称文件夹，用于分层保存文件。在Python没有提供直接操作目录的函数和对象，需要使用内置的os和os.path模块实现

   > os模块时Python内置的与操作系统功能和文件系统相关的模块，其执行结果通常与操作系统有关，因此在不同操作系统上可能会有不同的结果。

   1. os和os.path模块

      | 序号 | 方法及描述                                                   |
      | :--- | :----------------------------------------------------------- |
      | 1    | os.access(path, mode) 检验权限模式                           |
      | 2    | os.chdir(path) 改变当前工作目录                              |
      | 3    | os.chflags(path, flags) 设置路径的标记为数字标记。           |
      | 4    | os.chmod(path, mode) 更改权限                                |
      | 5    | os.chown(path, uid, gid) 更改文件所有者                      |
      | 6    | os.chroot(path) 改变当前进程的根目录                         |
      | 7    | os.close(fd) 关闭文件描述符 fd                               |
      | 8    | os.closerange(fd_low, fd_high) 关闭所有文件描述符，从 fd_low (包含) 到 fd_high (不包含), 错误会忽略 |
      | 9    | os.dup(fd) 复制文件描述符 fd                                 |
      | 10   | os.dup2(fd, fd2) 将一个文件描述符 fd 复制到另一个 fd2        |
      | 11   | os.fchdir(fd) 通过文件描述符改变当前工作目录                 |
      | 12   | os.fchmod(fd, mode) 改变一个文件的访问权限，该文件由参数fd指定，参数mode是Unix下的文件访问权限。 |
      | 13   | os.fchown(fd, uid, gid) 修改一个文件的所有权，这个函数修改一个文件的用户ID和用户组ID，该文件由文件描述符fd指定。 |
      | 14   | os.fdatasync(fd) 强制将文件写入磁盘，该文件由文件描述符fd指定，但是不强制更新文件的状态信息。 |
      | 15   | os.fdopen(fd[, mode[, bufsize\]]) 通过文件描述符 fd 创建一个文件对象，并返回这个文件对象 |
      | 16   | os.fpathconf(fd, name) 返回一个打开的文件的系统配置信息。name为检索的系统配置的值，它也许是一个定义系统值的字符串，这些名字在很多标准中指定（POSIX.1, Unix 95, Unix 98, 和其它）。 |
      | 17   | os.fstat(fd) 返回文件描述符fd的状态，像stat()。              |
      | 18   | os.fstatvfs(fd) 返回包含文件描述符fd的文件的文件系统的信息，Python 3.3 相等于 statvfs()。 |
      | 19   | os.fsync(fd) 强制将文件描述符为fd的文件写入硬盘。            |
      | 20   | os.ftruncate(fd, length) 裁剪文件描述符fd对应的文件, 所以它最大不能超过文件大小。 |
      | 21   | os.getcwd() 返回当前工作目录                                 |
      | 22   | os.getcwdb() 返回一个当前工作目录的Unicode对象               |
      | 23   | os.isatty(fd) 如果文件描述符fd是打开的，同时与tty(-like)设备相连，则返回true, 否则False。 |
      | 24   | os.lchflags(path, flags) 设置路径的标记为数字标记，类似 chflags()，但是没有软链接 |
      | 25   | os.lchmod(path, mode) 修改连接文件权限                       |
      | 26   | os.lchown(path, uid, gid) 更改文件所有者，类似 chown，但是不追踪链接。 |
      | 27   | os.link(src, dst) 创建硬链接，名为参数 dst，指向参数 src     |
      | 28   | os.listdir(path) 返回path指定的文件夹包含的文件或文件夹的名字的列表。 |
      | 29   | os.lseek(fd, pos, how) 设置文件描述符 fd当前位置为pos, how方式修改: SEEK_SET 或者 0 设置从文件开始的计算的pos; SEEK_CUR或者 1 则从当前位置计算; os.SEEK_END或者2则从文件尾部开始. 在unix，Windows中有效 |
      | 30   | os.lstat(path) 像stat(),但是没有软链接                       |
      | 31   | os.major(device) 从原始的设备号中提取设备major号码 (使用stat中的st_dev或者st_rdev field)。 |
      | 32   | os.makedev(major, minor) 以major和minor设备号组成一个原始设备号 |
      | 33   | [os.makedirs(path, mode\]) 递归文件夹创建函数。像mkdir(), 但创建的所有intermediate-level文件夹需要包含子文件夹。 |
      | 34   | os.minor(device) 从原始的设备号中提取设备minor号码 (使用stat中的st_dev或者st_rdev field )。 |
      | 35   | [os.mkdir(path, mode\]) 以数字mode的mode创建一个名为path的文件夹.默认的 mode 是 0777 (八进制)。 |
      | 36   | [os.mkfifo(path, mode\]) 创建命名管道，mode 为数字，默认为 0666 (八进制) |
      | 37   | [os.mknod(filename, mode=0600, device\]) 创建一个名为filename文件系统节点（文件，设备特别文件或者命名pipe）。 |
      | 38   | [os.open(file, flags, mode\]) 打开一个文件，并且设置需要的打开选项，mode参数是可选的 |
      | 39   | os.openpty() 打开一个新的伪终端对。返回 pty 和 tty的文件描述符。 |
      | 40   | os.pathconf(path, name) 返回相关文件的系统配置信息。         |
      | 41   | os.pipe() 创建一个管道. 返回一对文件描述符(r, w) 分别为读和写 |
      | 42   | os.popen(command[, mode[, bufsize\]]) 从一个 command 打开一个管道 |
      | 43   | os.read(fd, n) 从文件描述符 fd 中读取最多 n 个字节，返回包含读取字节的字符串，文件描述符 fd对应文件已达到结尾, 返回一个空字符串。 |
      | 44   | os.readlink(path) 返回软链接所指向的文件                     |
      | 45   | os.remove(path) 删除路径为path的文件。如果path 是一个文件夹，将抛出OSError; 查看下面的rmdir()删除一个 directory。 |
      | 46   | os.removedirs(path) 递归删除目录。                           |
      | 47   | os.rename(src, dst) 重命名文件或目录，从 src 到 dst          |
      | 48   | os.renames(old, new) 递归地对目录进行更名，也可以对文件进行更名。 |
      | 49   | os.rmdir(path) 删除path指定的空目录，如果目录非空，则抛出一个OSError异常。 |
      | 50   | os.stat(path) 获取path指定的路径的信息，功能等同于C API中的stat()系统调用。返回值为一个对象，可以访问对象属性获得文件基本信息。 |
      | 51   | [os.stat_float_times(newvalue\]) 决定stat_result是否以float对象显示时间戳 |
      | 52   | os.statvfs(path) 获取指定路径的文件系统统计信息              |
      | 53   | os.symlink(src, dst) 创建一个软链接                          |
      | 54   | os.tcgetpgrp(fd) 返回与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组 |
      | 55   | os.tcsetpgrp(fd, pg) 设置与终端fd（一个由os.open()返回的打开的文件描述符）关联的进程组为pg。 |
      | 56   | os.tempnam([dir[, prefix]]) **Python3 中已删除。**返回唯一的路径名用于创建临时文件。 |
      | 57   | os.tmpfile() **Python3 中已删除。**返回一个打开的模式为(w+b)的文件对象 .这文件对象没有文件夹入口，没有文件描述符，将会自动删除。 |
      | 58   | os.tmpnam() **Python3 中已删除。**为创建一个临时文件返回一个唯一的路径 |
      | 59   | os.ttyname(fd) 返回一个字符串，它表示与文件描述符fd 关联的终端设备。如果fd 没有与终端设备关联，则引发一个异常。 |
      | 60   | os.unlink(path) 删除文件路径                                 |
      | 61   | os.utime(path, times) 返回指定的path文件的访问和修改的时间。 |
      | 62   | os.walk(top[, topdown=True[, onerror=None[, followlinks=False\]]])输出在文件夹中的文件名通过在树中游走，向上或者向下。 |
      | 63   | os.write(fd, str) 写入字符串到文件描述符 fd中. 返回实际写入的字符串长度 |
      | 64   | os.path 模块 获取文件的属性信息。                            |
      | 65   | os.pardir() 获取当前目录的父目录，以字符串形式显示目录名。   |
      | 66   | os.name 获取操作系统类型，nt为Windows，posix为Linux、Unix或Mac |
      | 67   | os.linesep 获取当前操作系统上的换行符                        |
      | 68   | os.sep 获取当前操作系统所使用的路径分隔符                    |

      | 方法                                | 说明                                                         |
      | :---------------------------------- | :----------------------------------------------------------- |
      | os.path.abspath(path)               | 返回绝对路径                                                 |
      | os.path.basename(path)              | 返回文件名                                                   |
      | os.path.commonprefix(list)          | 返回list(多个路径)中，所有path共有的最长的路径               |
      | os.path.dirname(path)               | 返回文件路径                                                 |
      | os.path.exists(path)                | 路径存在则返回True,路径损坏返回False                         |
      | os.path.lexists                     | 路径存在则返回True,路径损坏也返回True                        |
      | os.path.expanduser(path)            | 把path中包含的"\~"和"~user"转换成用户目录                    |
      | os.path.expandvars(path)            | 根据环境变量的值替换path中包含的"$name"和"${name}"           |
      | os.path.getatime(path)              | 返回最近访问时间（浮点型秒数）                               |
      | os.path.getmtime(path)              | 返回最近文件修改时间                                         |
      | os.path.getctime(path)              | 返回文件 path 创建时间                                       |
      | os.path.getsize(path)               | 返回文件大小，如果文件不存在就返回错误                       |
      | os.path.isabs(path)                 | 判断是否为绝对路径                                           |
      | os.path.isfile(path)                | 判断路径是否为文件                                           |
      | os.path.isdir(path)                 | 判断路径是否为目录                                           |
      | os.path.islink(path)                | 判断路径是否为链接                                           |
      | os.path.ismount(path)               | 判断路径是否为挂载点                                         |
      | os.path.join(path1[, path2[, ...]]) | 把目录和文件名合成一个路径，拼接时不会检测该路径是否真实存在，若存在多个绝对路径，则以从左到右为序最后一次出现的路径为准，且该路径之前的参数都将被忽略 |
      | os.path.normcase(path)              | 转换path的大小写和斜杠                                       |
      | os.path.normpath(path)              | 规范path字符串形式                                           |
      | os.path.realpath(path)              | 返回path的真实路径                                           |
      | os.path.relpath(path[, start])      | 从start开始计算相对路径                                      |
      | os.path.samefile(path1, path2)      | 判断目录或文件是否相同                                       |
      | os.path.sameopenfile(fp1, fp2)      | 判断fp1和fp2是否指向同一文件                                 |
      | os.path.samestat(stat1, stat2)      | 判断stat tuple stat1和stat2是否指向同一个文件                |
      | os.path.split(path)                 | 把路径分割成 dirname 和 basename，返回一个元组               |
      | os.path.splitdrive(path)            | 一般用在 windows 下，返回驱动器名和路径组成的元组            |
      | os.path.splitext(path)              | 分割路径中的文件名与拓展名                                   |
      | os.path.splitunc(path)              | 把路径分割为加载点与文件                                     |
      | os.path.walk(path, visit, arg)      | 遍历path，进入每个目录都调用visit函数，visit函数必须有3个参数(arg, dirname, names)，dirname表示当前目录的目录名，names代表当前目录下的所有文件名，args则为walk的第三个参数 |
      | os.path.supports_unicode_filenames  | 设置是否支持unicode路径名                                    |

   2. 路径

      用于定位一个文件或者目录的字符串

      1. 相对路径

         相对路径依赖于当前工作目录，以当前工作目录为起点

         > 在Python中指定文件路径时需要对路径分隔符"`\`"进行转义，即将路径中的"`\`"替换为"`\\`"，也可以采用"`/`"代替，或在表示路径的字符串前面加上字母r/R

      2. 绝对路径

         绝对路径是指在使用文件时指定文件的实际路径，不依赖当前工作目录

   3. 创建目录

      1. 创建一级目录

         只能创建指定路径的最后一级目录，如果该目录的上一级不存在则抛出异常

         ```python
         os.mkdir(path [,mode=0o77])
         ```

         > path：指定要创建的目录
         >
         > mode：指定数值模式，默认值为0777，仅在Unix系统上有效

      2. 创建多级目录

         ```python
         os.makedirs(path [,mode=0o77])
         ```

   4. 删除目录

      1. 删除空目录

         ```python
         os.rmdir(path)
         ```

      2. 删除非空目录

         ```python
         import shutil
         shutil.rmtree(path)
         ```

   5. 遍历目录

      ```python
      os.walk(top[, topdown][, onerror][, followlinks])
      ```

      > top：指定要遍历内容的根目录
      >
      > topdown：可选参数，指定遍历的顺序，值为True表示自上而下遍历(即先遍历根目录)，值为False表示自下而上遍历(即先遍历最后一级子目录)，默认值为True
      >
      > onerror：可选参数，指定错误处理方式，默认为忽略
      >
      > followlinks：可选参数，将该参数值设定为True表示指定在支持的系统上访问由符号链接指向的目录
      >
      > 返回值：返回一个包括三个元素(dirpath,dirnames,filenames)的元组生成器对象，dirpath表示当前遍历的路径(一个字符串)，dirnames表示当前路径下包含的子目录(一个列表)，filenames表示当前路径下包含的文件(一个列表)
      >
      > 



#	基础语法

##	保留字

保留字是Python中一些已经被赋予特殊意义的单词，不能把这些保留字作为变量、函数、类、模块和其他对象的名称来使用

Python中所有的保留字是区分字母大小写的

查看保留字可使用keyword模块

```python
import keyword
keyword.kwlist
```

![](Pictures\Python保留字.png)

错误代码：“invalid syntax”



##	标识符

标识符可以简单地理解成一个名字，主要用来标识变量、函数、类、模块和其他对象的名称

1. 标识符由字母、数字以及下划线(_)组成，但不能以数字开头
2. 不能使用保留字
3. **区分大小写**
4. 以下划线开头的标识符是有特殊意义的
   1. 以单下划线"_"开头的模块变量或者函数是受保护的，在使用from xx import *语句从模块导入时这些变量或者函数不能被导入
   2. 以双下划线开头的代表类的私有成员
   3. 以双下划线开头和结尾的代表 Python 里特殊方法专用的标识，如 \__init__() 代表类的构造函数
5. 可以同一行显示多条语句，方法是用分号 **;**分开



##	运算符

1. 算数运算符

   ![image-20220220232641177](Pictures\Python算数运算符.png)

   除数不能为0，取模时如果除数为负数则结果也为负值

   Python 3.x中整数相除计算结果为浮点数

2. 赋值运算符

   ![image-20220220233852935](Pictures\Python赋值运算符.png)

3. 比较(关系)运算符

   ![image-20220220234034532](Pictures\比较运算符.png)

   判断一个变量是否介于两个值之间可采用"值1<变量<值2"的形式

4. 逻辑运算符

   | 运算符 |  含义  |    用法     | 结合方向 |
   | :----: | :----: | :---------: | :------: |
   |  and   | 逻辑与 | op1 and op2 | 从左到右 |
   |   or   | 逻辑或 | op1 or op2  | 从左到右 |
   |  not   | 逻辑非 |   not op    | 从右到左 |

5. 位运算符

   ![image-20220220235234232](Pictures\Python位运算符.png)

   左端为高位端，右端为低位端

6. 成员运算符

   ![image-20220221000905312](Pictures\Python成员运算符.png)

7. 身份运算符

   ![image-20220221001117806](Pictures\Python身份运算符.png)

8. 集合运算符

   | 运算符 | 描述                       |
   | ------ | -------------------------- |
   | &      | 交集运算                   |
   | \|     | 并集运算，自动去除重复元素 |
   | ^      | 对称差集                   |
   | -      | 差集运                     |

8. 运算符的优先级

   优先级高的运算先执行，同一优先级的操作从左到右进行，可使用()优先执行

   ![image-20220221001836009](Pictures\Python运算符优先级.png)



##	注释

1. 单行注释用 **#** 
2. 多行注释可以用一对 **'''** 和 **"""**
2. 中文编码声明注释 **# -\*- coding:编码 -\*-**



##	代码组

缩进相同的一组语句构成一个代码块，称之代码组

首行以关键字开始，以冒号( : )结束

首行及后面的代码组称为一个子句(clause)



##	 命令行参数

1. Python 提供了 **getopt** 模块来获取命令行参数

   ```python
   getopt.getopt(args, options[, long_options])
   
   args: 要解析的命令行参数列表。
   options: 以字符串的格式定义，options 后的冒号 : 表示该选项必须有附加的参数，不带冒号表示该选项不附加参数
   long_options: 以列表的格式定义，long_options 后的等号 = 表示如果设置该选项，必须有附加的参数，否则就不附加参数
   ```

2. Python 中也可以所用 **sys** 的 **sys.argv** 来获取命令行参数

   ```python
   sys.argv 是命令行参数列表
   len(sys.argv) 计算命令行参数个数
   sys.argv[0] 表示脚本名
   
   eg：
   import sys
   print ('参数个数为:', len(sys.argv), '个参数。')
   print ('参数列表:', str(sys.argv))
   print ('脚本名:', str(sys.argv[0]))
   ```

   



#	常用函数/方法/模块

1. type()用于获取变量数据类型

2. id()用于获取变量在内存中的地址

3. range(start, end, step)用于生成一系列连续的整数，返回的是一个**可迭代对象**（类型是对象），而不是列表类型， 所以打印的时候不会打印列表
   1. start 指定计数的起始值，可以省略，如果省略则从0开始
   2. end  指定计数的结束值(**但不包括该值**，即**左闭右开**，反向输出的时候同理)，不能省略，函数必须含有该值
   3. step 指定步长，即两个数之间的间隔，可以省略
   
4. reversed()用于反向序列中的元素

5. enumerate(iterable[,start])用于将序列组合成一个索引序列，多用在for循环中，返回包含元素形式为(0,iterable[0])的迭代器对象，start表示索引的起始值

6. random()模块

   1. **random.random** 

      random.random()用于生成一个0到1的随机浮点数: 0 <= n < 1.0

   2. **random.uniform**

      random.uniform(a, b)，用于生成一个指定范围内的随机符点数，两个参数其中一个是上限，一个是下限。

      如果a < b，则生成的随机数n: b>= n >= a。

      如果 a >b，则生成的随机数n: a>= n >= b。

   3. **random.randint**

      random.randint(a, b)，用于生成一个指定范围内的整数。其中参数a是下限，参数b是上限，生成的随机数n: a <= n <= b

   4. **andom.randrange**

      random.randrange([start], stop[, step])，从指定范围内，按指定基数递增的集合中 获取一个随机数。

   5. **random.choice**

      random.choice()从序列中获取一个随机元素。其函数原型为：random.choice(sequence)。参数sequence表示一个有序类型。

   6. **random.shuffle**

      random.shuffle(x[, random])，用于将一个列表中的元素打乱。

   7. **random.sample**

      random.sample(sequence, k)，从指定序列中随机获取指定长度的片断。sample函数不会修改原有序列。
   
7. eval(s[,globals[,locals]])，计算并返回字符串s中表达式的值

8. filter(func,seq)，返回filter对象，其中包含序列seq中使得单参数函数func返回值为True的那些元素，如果函数func为None则返回包含seq中等价于True的元素的filter对象

9. globals()，返回包含当前作用域内全局变量及其值的字典

10. locals()，返回包含当前作用域内局部变量及其值的字典

11. map(func,*iterables)，返回包含若干函数值的map对象，函数func的参数分别来自于iterables指定的一个或多个迭代对象，把函数func依次映射到序列的每个元素上，map对象中每个元素是原序列中元素经过函数func处理后的结果，map函数不对原序列做任何修改

12. next(iterator[,default])，返回可迭代对象x中的下一个元素，允许指定迭代结束之后继续迭代时返回的默认值

13. zip(seq1[,seq2[...]])，返回zip对象，其中元素为(seq1[i],seq2[i],...)形式的元组，最终结果中包含的元素个数取决于所有参数序列或可迭代对象中最短的那个，zip对象只能遍历一次，访问过的元素就不存在了





#	标准数据类型

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

##	变量

1. 可理解为值在内存中的"标签"

2. 在Python中不需要先声明变量名及其类型，直接赋值即可创建各种类型的变量，且赋值以后该变量才会被创建

3. 在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型

4. 变量的类型可以随时变化

5. 变量名需慎用小写字母l和大写字母O

6. 应选择有意义的单词作为变量名

7. 使用内置函数type()可以返回变量类型
8. Python变量并不直接存储值，而是存储了值的内存地址或引用，这也是变量类型随时可以改变的原因



## 多个变量赋值

1. a = b = c = 1

   这种赋值方法使变量都指向同一个内存地址

2. a, b, c = 1, 2, "runoob"

##	Number （数字）

数字类型是不可改变的，如果修改数字类型变量的值，那么会先把该值存在内存中，然后修改变量让其指向新的内存地址
Python3.6以上支持在数字**中间**添加单个下划线_进行分割

1. **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long

   1. 十进制整数不能以0作为开头
   1. 二进制整数以0b开头
   2. 八进制整数以0o/0O开头
   3. 十六进制整数以0x/0X开头

2. **bool** (布尔), 表示真值或假值，在Python中标识符True和False被解释为布尔值

   布尔值可以转化为数值，True表示1，False表示0

   布尔类型可以进行数值运算，但不建议使用

   所有的对象都可以进行真值测试，只有以下几种情况得到的值为假：

   1. False或None
   2. 数值中的0
   3. 空序列
   4. 自定义对象的实例，该对象的\__bool_\_方法返回False或者\__len__方法返回0

3. **float** (浮点数), 如 1.23、3E-2，应尽量避免直接比较两个浮点数相等

4. **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

   由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型



##	Sequence（序列）

序列是一块用于存放多个值的连续内存空间，每一个值(称为元素)都分配一个数字，称为**索引**或位置，类似C语言中的数组下标

![image-20220216223523384](Pictures\字符串索引和截取.png)

1. 索引(indexing)：从左往右以 **0** 开始，从右往左以 **-1** 开始

2. 切片(sliceing)：访问一定范围内的元素，左闭右开

   `[start:end:step]`

   第一个元素和最后一个元素为**：**，从左往右以 **1** 开始，从右往左以 **-1** 开始，**sequencename[start:stop"step]**，如果第三个参数为负数表示逆向读取，复制整个序列可以将头下标和尾下标省略只保留"**:**"(xx[:])

   1. print(str[2:5])       =>cde       输出从==第三个==开始到==第五个==的字符
   2. print(str[2:])         =>cdef      输出从==第三个==开始后的==所有==字符
   3. print(str[1:5:2])    =>bd         输出从==第二个==开始到==第五个==且==每隔一个==的字符（步长为2,即数组下标+2）

3. 序列相加(adding)：Python中支持两种**相同类型**的序列相加操作，即使用加(+)运算符实现

4. 乘法(multiplying)：Python中使用数字n乘以一个序列会生成原序列被重复n次的新序列

   可初始化指定长度的列表：emptylist=[None]*x
   
5. 序列解包

   ```python
   x, y, z = 1, 2, 3	# 多个变量同时赋值
   v_tuple = (False, 3.5, 'exp')
   x, y, z = v_tuple
   x, y = y, x	# 交换两个变量的值
   x, y, z = range(3)
   x, y, z = map(str, range(3))
   
   s = {'a':1, 'b':2, 'c':3}
   b, c, d = s.items	# 对字典的元素进行解包
   b, c, d = s	# 对字典的键进行解包
   b, c, d = s.values()	# 对字典的值进行解包
   ```

   



###	String（字符串）

1. 有两种常用的字符串类型，分别为str和bytes，str表示Unicode字符(ASCII码或其他)，bytes表示二进制数据(包括编码的文本)，这两种类型的字符串不能拼接在一起使用，通常情况下，str在内存中以Unicode表示，一个字符对应若干个字节，但如果在网络上传输或存储到磁盘上则需要把str转换为bytes类型

1. 单引号 **'** 和双引号 **"** 使用完全相同

2. 使用三引号(**'''** 或 **"""**)可以指定一个多行字符串

3. 需要表示复杂的字符串时，还可以嵌套使用引号

4. 转义符 **\\**

   ![image-20220220230311929](Pictures\Python转义字符.png)

5. 反斜杠可以用来转义，使用 **r或R** (指 raw)可以让反斜杠不发生转义

    如 **r"this is a line with \n"** 则 **\n** 会显示，并不是换行

8. 字符串==不能改变==(相当于C语言中的字符串常量)

7. Python 没有单独的字符类型，一个字符就是长度为 1 的字符串

8. 拼接字符串

    使用"+"运算符可以完成对多个字符串的拼接

    ```python
    print("abc"+"123")
    ```

    不允许与其他类型的数据拼接，可用str()函数转换为字符串类型后进行拼接

9. 使用len()函数计算字符串长度

    通过len()函数计算字符串长度时所有字符都按一个字符算

    获取字符串实际所占字节数可使用encode()方法进行编码后再进行获取

    ```python
    str1="LeK"
    # UTF-8编码
    length=len(str1.encode())
    
    # GBK编码
    length=len(str1.encode("GBK"))
    ```

10. 分割字符串

    将字符串分割成列表

    字符串的split()方法可以实现字符串的分割，将字符串按照指定的分隔符切分成字符串列表，列表元素中不包括分隔符

    ```python
    str.split(sep,maxsplit)
    ```

    > sep：用于指定分隔符，可以包含多个字符，默认为None，即所有空字符(包括空格、换行"\n"、制表符"\t"等)
    >
    > maxsplit：可选参数，用于指定分割的次数，如果不指定或指定为-1则分割次数没有限制，否则返回结果列表的元素个数，个数最多为maxsplit+1
    
    返回值：分割后的字符串列表
    
    如果不指定sep参数，就不能指定maxsplit参数
    
    如果采用默认空白符进行分割，则连续的空白符作为一个分隔符进行分割，如果指定一个分隔符切该分隔符连续出现时，就会每个分隔一次，没有得到内容的将产生一个空元素
    
    ```python
    str="111 >>> 222"
    print(str.split(">"))
    
    ["111 ","",""," 222"]
    ```

11. 合并字符串

     将字符串列表合并为字符串

     使用字符串对象的join()方法将多个字符串采用固定的分隔符连接在一起

     ```python
     strnew=string.join(iterable)
     
     eg:
         strnew="*".join(listname)
     ```

    > string：字符串类型，用于指定合并时的分隔符
    >
    > iterable：可迭代对象，该迭代对象中的所有元素(字符串表示)将被合并成一个新的字符串

​		使用join()方法时，第一个元素前不加分隔符

12. 检索字符串

     1. count()方法

         检索指定字符串在另一个字符串中出现的次数，如果检索的字符串不存在则返回0，否则返回出现的次数

         ```python
         str.count(sub, start= 0,end=len(string))
         ```

         > str：原字符串
         >
         > sub：要检索的子字符串
         >
         > start：可选参数，表示检索范围的起始位置的索引，如果不指定则从头开始检索
         >
         > end：可选参数，表示检索范围的结束位置的索引，如果不指定则一直检索到结尾
         
          2. find()方法
         
              检索是否包含指定子字符串，如果不存在则返回-1，否则返回首次出现该字符串时的索引
         
              ```python
              str.find(sub, start= 0,end=len(string))
              ```
         
              如果只是想判断字符串是否存在可以使用成员运算符"in"
         
              rfind()方法作用与find()类似，只是从字符串右端开始查找
         
          3. index()方法
         
              与find()方法类似，也是用于检索是否包含指定的子字符串，但该方法当指定的字符串不存在时会抛出异常
         
              ```python
              str.index(sub, start= 0,end=len(string))
              ```
         
              rindex()方法作用与index()类似，只是从字符串右端开始查找
         
          4. startswith()方法
         
              用于检索字符串是否以指定子字符串开头，如果是则返回True，否则返回False
         
              ```python
              str.startswith(prefix,start=0,end=len(string))
              ```
         
          5. endswith()方法
         
              用于检索字符串是否以指定子字符串结尾，如果是则返回True，否则返回False
         
              ```python
              str.endswith(prefix,start=0,end=len(string))
              ```

13. 字母的大小写转换

     1. lower()方法

         将字符串中的大写字母转换为小写字母

     2. upper()方法

         将字符串中的小写字母转换为大写字母

14. 去除字符串中的空格和特殊字符

     1. lstrip()方法

         用于去掉字符串左侧的空格和特殊字符

         ```python
         str.lstrip([chars])
         ```

         > chars：可选参数，用于指定要去除的字符，可以指定多个

     2. rstrip()方法

         用于去掉字符串右侧的空格和特殊字符

         ```python
         str.rstrip([chars])
         ```

         > chars：可选参数，用于指定要去除的字符，可以指定多个

     3. strip()方法

         用于去掉字符串左右两侧的空格和特殊字符,即在 string 上执行 lstrip()和 rstrip()

         ```python
         str.strip([chars])
         ```

         > chars：可选参数，用于指定要去除的字符，可以指定多个

15. 格式化字符串

     格式化字符串是指先制定一个模板，在这个模板中预留几个空位，然后再根据需要填上相应的内容。这些空位需要通过指定的占位符标记，而这些符号并不会显示出来

     1. 使用"%"操作符

         ```python
         "%[+][-][0][m][.n]格式化字符"%exp
         ```

         >+：可选参数，用于指定右对齐，正数前方加正号，负数前方加负号
         >
         >-：可选参数，用于指定左对齐，正数前方无符号，负数前方加负号
         >
         >0：可选参数，表示右对齐，正数前方无符号，负数前方加负号，用0填充空白处
         >
         >m：可选参数，表示占有宽度
         >
         >.n：可选参数，表示小数点后保留的位数
         >
         >exp：要转换的项，如果指定的项有多个则需要通过元组的形式进行指定
         
          格式化字符：用于指定类型
         
          ![](Pictures\Python格式化操作符辅助指令.png)
         
          ![Python格式化输入输出](Pictures\Python格式化输入输出.png)

     2. format()方法

         ```python
         str.format(args)
         ```

         > format：用于指定字符串的显示模板
         >
         > args：用于指定要转换的项，如果有多项要用逗号进行分隔

         创建模板时要用"{}" ":"指定占位符

         ```
         {[index][: [[fill]align] [sign] [#] [width] [.precision] [type] ]}
         ```

         > index：可选参数，用于指定要设置格式的对象在参数列表中的索引位置，索引值从0开始，默认根据值的先后顺序自动分配
         >
         > fill：可选参数，用于指定空白处填充的字符
         >
         > align：可选参数，用于指定对齐方式("<"表示内容左对齐，">"表示内容右对齐，"="表示内容右对齐且符号放在填充内容的最左侧且只对数字类型有效，"^"表示内容居中)，需要配合width一起使用
         >
         > sign：可选参数，"+"表示正数加正号负数加负号，"-"表示正数不变负数加负号，" "表示正数加空格负数加负号
         >
         > #：可选参数，对于二进制、八进制、十六进制数，会显示0b/0o/0x前缀
         >
         > width：可选参数，用于指定所占宽度
         >
         > .precision：可选参数，用于指定保留的小数位数
         >
         > type：可选参数，用于指定类型

         当一个模板中出现多个占位符时，指定索引位置的规范需统一，即全部采用手动指定或全部采用自动指定
    
17. 编码转换

      1. 使用encode()方法编码

          用于将字符串转换为bytes，也称为"编码"

          ```python
          str.encode([encoding="xxx"],[errors="yyy"])
          ```

          > encoding=" "：可选参数，用于指定进行转码时采用的字符编码，默认为UTF-8，当只有这一个参数时可以省略前面的"coding="直接写编码
          >
          > errors=" "：可选参数，用于指定错误处理方式，可选择值有"strict"(遇到非法字符就抛出异常)、"ignore"(忽略非法字符)、"replace"(用"?"替换非法字符)或"xmlcharrefreplace"(使用XML的字符引用)等，默认值为strict
          
          使用encode()方法不会修改原字符串

    

      2. 使用decode()方法解码

          用于将bytes转换为字符串，也称为"解码"
    
          ```python
          bytes.decode([encoding="xxx"],[errors="yyy"])
          ```

          在设置解码采用的字符编码时应与编码时采用的字符编码一致
    
          使用decode()方法不会修改原字符串
          




###	List（列表）

1. 列表中元素的类型可以不相同(但不建议这么做)，它支持数字、字符串、嵌套列表等任何类型，元素之间没有任何关系

2. 列表是写在方括号 [ ] 之间、用逗号分隔开的元素列表

3. 和字符串一样，列表同样可以被索引和切片，列表被截取后返回一个包含所需元素的新列表

4. ==与字符串不一样的是，列表中的元素是可以改变的==

5. ==与C语言数组不一样的是，列表中的元素可以赋空值的==（a[x:y] = []）

5. 列表中存储的实际上为指向某一块内存的地址，类似于C语言中的指针数组

6. 创建：

   1. 使用赋值运算符直接创建列表

   2. 创建空列表（a[x:y] = [ ]    listname=[ ])

   3. 创建数值列表

      list(data)用于将序列、对象等转换为列表

7. 删除：del listname

   并不常用，Python自带的垃圾回收机制会自动销毁不用的列表
   
8. 遍历

   1. 直接使用for循环实现

      ```python
      for item in listname
      #	输出item
      ```

      item保存获取到的元素值

   2. for循环和enumerate()函数实现

      ```python
      for index,item in enumerate(listname)
      #	输出index和item
      ```

      index保存元素的索引，item保存获取到的元素值
   
9. 使用append()方法在列表末尾添加元素

   ```python
   listname.append(abj)
   ```

   使用insert()方法在列表指定位置添加元素

   ```python
   listname.insert(index, obj)
   ```

   使用extend()方法将一个列表中的所有元素添加到另一个列表末尾

   ```python
   listname.extend(seq)
   ```

10. 删除元素

    1. 根据索引删除
    


```python
del listname[index]
```

​		  2.根据元素值删除


```python
listname.remove(obj)	# 删除列表中第一个值与指定值相等的元素
```

11. 获取指定元素出现的次数

    ```python
    listname.count(obj)
    ```

    返回值为元素在列表中出现的次数

12. 获取指定元素首次出现的下标

    ```
    listname.index(obj)
    ```

    返回值为首次出现时的索引值

13. 统计数值列表的元素和

    ```python
    sum(iterable[],start)
    ```

    > iterable：要统计的列表
    >
    > start：即将统计结果加上start所指定的数，默认为0

14. 排序

    1. 使用列表对象的sort()方法

       ```python
       listname.sort(cmp[, key=None[, reverse=False]])
       ```

       **原列表中的元素顺序将发生改变**

       > cmp：排序时进行比较的函数，可以指定一个函数或者lambda函数
       >
       > key:可选参数，表示指定从每个元素中提去一个用于比较的键(例如设置"key=str.lower"表示在排序时不区分字母大小写)，指定取待排序元素的哪一项进行排序
       >
       > reverse:可选参数，如果将其值指定为True，则表示降序排列；如果为False，则表示升序排列，默认为升序排列
       
    2. 使用Python内置的sorted()函数实现

       ```python
       sorted(iterable,cmp,key=None,reverse=False)
       ```

       **使用该函数排序后原列表的元素顺序不变**，返回一个排序后的新对象

15. listname.pop([index])删除并返回列表中下标为index的元素，默认值为-1

15. 列表推导式

    1. 生成指定范围的数值列表

       ```python
       list=[expression for var in range]
       
       eg:
           list=[random.randint for i in range(10)]
       ```

       > expression:表达式，用于计算新列表的元素
       >
       > var:循环变量
       >
       > range:采用range()函数生成的range对象
       
    2. 根据列表生成指定需求的列表
    
       ```python
       newlist=[expression for var in list]
       
       eg:
           newlist=[int(x*0.5) for x in oldlist]
       ```
    
       > list:用于生成新列表的原列表
    
    3. 从列表中选择符合条件的元素组成新的列表
    
       ```python
       newlist=[expression for var in list if condition]
       
       eg:
           newlist=[x for x in oldlist if x>5000]
       ```
    
       > condition:条件表达式，用于指定筛选条件

16. 二维列表的使用

    1. 使用嵌套的for循环创建

       ```python
       arr=[]
       for i in range(4):
           arr.append([])
           for j in range(5):
               arr[i].append(j)
       ```

    2. 使用列表推导式创建

       ```python
       arr=[[j for j in range(5)] for i in range(4)]
       ```

       

###	Tuple（元组）

1. `tuple`中存储的是元素所对应的==内存地址==

2. 元组（tuple）与列表类似，不同之处在于元组的元素==不能修改==。元组写在小括号 **()** 里，元素之间用逗号隔开

3. 字符串可看作一种特殊的元组

4. 元组也可以被索引和切片

5. 虽然tuple的元素不可改变，但它可以包含可变的对象，比如list、变量

5. Python内部实现对元组做了大量优化，访问和处理速度比列表快

5. 元组可用作字典的键和集合的元素，而列表则永远都不能当做字典键使用

6. **构造包含 0 个或 1 个元素的元组比较特殊**

   ```python
   tup1 = ()    # 空元组
   tup2 = (20,) # 一个元素，需要在元素后添加逗号
   ```
   
   空元组可应用在为函数传递一个空值或返回空值时
   
9. 创建数值元组

   ```python
   tuple(data)
   ```

   data表示可转换为元组的数据，其类型是可迭代的数据

10. 删除元组

   ```python
   del tuplename
   ```

11. 修改元组元素

    元组是不可变序列，所以不能进行当个元素的修改，但可以对元组进去整体的重新赋值，也可以对元组进行连接组合

12. 生成器表达式

    生成器表达式生成的结果并不是一个元组或者列表，而是一个生成器对象，这一点是和列表推导式不同的

    若直接打印生成器推导式的创建结果，则会显示该对象的存储地址

    1. 使用tuple()函数将其转换为元组

    ```python
    eg:
    import random
    randomnumber=(random.randint(10,100) for i in range(10))
    randomnumber=tuple(randomnumber)
    ```

    2. 遍历

       只能从前往后正向访问每个元素，没有任何方法可以再次访问已访问过的元素，也不支持使用下标访问其中的元素。当所有元素访问结束以后，如果需要重新访问其中的元素，必须重新创建该生成器对象

       1. 使用\__next__()方法进行遍历

       ```python
       eg:
       number=(i for i in range(5))
       print(number.__next__())
       ```

       2. 使用for循环进行遍历

       ```
       eg:
       number=(i for i in range(4))
       for i in number:
       	print(i)
       ```

       

###	Dictionary（字典）

1. 字典是无序的对象集合,字典当中的元素是通过键来存取的，有时也称为关联数组或者散列表(hash)

2. 字典是一种**映射**类型，字典用 **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合
3. 键是惟一的，而值可以有多个，如果出现两次同样的键，则后一个值会被记住
4. 键只能使用不可变的数据类型充当
5. 通过键而不是通过索引来读取

```python
dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]     = "2 - 菜鸟工具"

tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}


print (dict['one'])       # 输出键为 'one' 的值
print (dict[2])           # 输出键为 2 的值
print (tinydict)          # 输出完整的字典
print (tinydict.keys())   # 输出所有键
print (tinydict.values()) # 输出所有值
```

6. 创建

   1. 创建空字典

      ```python
      1.	dictionary={}
      2.	dictionary=dict()
      ```

   2. 通过映射函数创建字典

      ```python
      dictionary=dict(zip(list1,list2))
      ```

      > zip()函数用于将多个列表和元组对应位置的元素组合为元组，并返回包含这些内容的zip对象
      >
      > list1用于指定要生成字典的键
      >
      > list2用于指定要生成字典的值

      如果list1和list2长度不同，则与最短的列表长度相同

   3. 通过给定的**键-值对**创建字典

      ```python
      dictionary=dict(key1=value1,key2=value2,....)
      ```

   4. 使用dict对象的fromkeys()方法创建值为空的字典

      ```python
      dictionary=dict.fromkeys(list1)
      ```

      > list1是作为字典的键的列表

   5. 删除字典的全部元素

      ```python
      dictionary.clear()
      ```

      除此之外还可以使用pop()方法删除并返回指定"键"的元素，使用popitem()方法返回最后插入键值对

   6. 通过键值对访问字典

      ```python
      dictionary[key]
      ```

   7. 使用get()方法获取指定键的值

      ```python
      dictionary.get(key,[default])
      ```

      > key为指定的键
   
   
   default为可选项，用于指定当键不存在时，返回一个默认值，默认为None
   
   8. 使用items()方法遍历
   
      ```python
      for item in dictionary.items():
          print(item)
          
      for key,value in dictionary.items():
          print(key,value)
      ```
   
      返回值为可遍历的键值对的元组列表
   
      还可以使用keys() values()方法获取字典的键和值
   
   9. 添加元素
   
      ```python
      dictionary[key]=value
      ```
   
      如果新添加的元素的键与原有键重复，那么新的值会代替原来的值
   
      ```python
      dict1.update(dict2)
      ```
   
      将另一个字典的键值对一次性全部添加到当前字典对象，如果两个字典中存在相同的键，则以另一个字典为准对当前字典进行更新
   
   10. 字典推导式
   
       ```python
       import random
       dictionary={i:random.randint(10,100) for i in range(5)}
       
       dictionary={i:j for i,j in zip(list1,list2)}
       ```



###	Set（集合）

集合（set）是由一个或数个形态各异的大小整体组成的，构成集合的事物或对象称作元素或是成员，与数学中的集合概念类似，用于保存不重复元素，有可变集合(set)和不可变集合(frozenset)两种

1. 可以使用大括号 **{ }** 或者 **set()** 函数创建集合，注意：创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典

   ```python
   parame = {element1,element2,...}
   
   setname=set(iteration)
   ```

   > iteration为可迭代对象，若该对象为字符串则返回的集合将包含全部不重复字符的集合

2. 使用add()方法添加元素

   ```python
   setname.add(element)
   ```

   > element只能使用**字符串、数字及布尔类型的True/False**

3. 删除

   可以使用del命令删除整个集合，也可以使用pop()或者remove()方法删除一个元素，或者使用clear()方法清空集合

4. 基本功能是进行**成员关系测试**和**删除重复元素**

   1. ```python
      sites = {'Google', 'Taobao', 'Runoob', 'Facebook', 'Zhihu', 'Baidu'}
      
      print(sites)   # 输出集合，重复的元素被自动去掉
      ```

   2. ```python
      # 成员测试
      if 'Runoob' in sites :
          print('Runoob 在集合中')
      else :
          print('Runoob 不在集合中')
      ```

5. 并集、交集、差集运算

   ```python
   a = set('abracadabra')
   b = set('alacazam')
   
   print(a)
   
   print(a - b)     # a 和 b 的差集
   
   print(a | b)     # a 和 b 的并集
   
   print(a & b)     # a 和 b 的交集
   
   print(a ^ b)     # a 和 b 中不同时存在的元素
   ```

   

#	数据类型转换

![image-20220220231948606](Pictures\Python数据类型转换函数.png)

转换后原变量数据类型不变



#	选择结构

选择语句主要有3种形式，分别为if语句、if...else语句和if...elif...else语句

```python
if 表达式:
	语句块
elif 表达式:
    语句块
else 表达式:
    语句块
```



#	循环结构

分为计数循环(for)和条件循环(while)

1. **while**

   ```python
   while 条件表达式:
   	循环体
   ```

2. **for**

   ```python
   for 迭代变量 in 对象:
   	循环体
   ```

   迭代变量用于保存读取出的值；对象为要遍历或迭代的对象，该对象可以是任何有序的**序列**对象

   可遍历数字、序列、集合、字典等

3. **else**

   else 中的语句会在循环正常执行完（即不是通过 break 跳出而中断的）的情况下执行，可用于for和while

4. 结束循环

   1. **break**

      终止当前的循环代码组

   2. **continue**

      终止本次循环，进行下一次循环

5. **pass**

   不做任何事情，起占位作用



#	生成器表达式

```python
(i for i in range(10))
```

生成器表达式使用圆括号()作为定界符

生成器表达式生成的结果并不是一个元组或者列表，而是一个生成器对象，这一点是和列表推导式不同的

若直接打印生成器推导式的创建结果，则会显示该对象的存储地址

生成器表达式具有惰性求值的特点，只在需要时生成新元素，比列表推导式具有更高的速率，空间占用非常少

可以使用生成器对象的`__next__()`方法或者内置函数next()进行遍历

遍历生成器对象只能从前往后正向访问每个元素，没有任何方法可以访问已访问过的元素，必须重新创建该生成器对象，其他迭代器对象也具有同样的特点







#	正则表达式

 在查找符合某些复杂规则的字符串时，正则表达式就是用于描述这些规则的工具，即记录文本规则的代码，正则表达式使用预定的模式去匹配一类具有共同特征的字符串，可以快速、准确地完成复杂的查找、替换等处理请求，比字符串自身提供的方法具有更强大的处理功能。

1. 元字符

   正则表达式由元字符及其不同组合来构成

   | 字符         | 描述                                                         |
   | :----------- | :----------------------------------------------------------- |
   | \            | 将下一个字符标记为一个特殊字符、或一个原义字符、或一个 向后引用、或一个八进制转义符。例如，'n' 匹配字符 "n"。'\n' 匹配一个换行符。序列 '\\\' 匹配 "\\" 而 "\(" 则匹配 "("。 |
   | ^            | 匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性，^ 也匹配 '\n' 或 '\r' 之后的位置。 |
   | $            | 匹配输入字符串的结束位置。如果设置了RegExp 对象的 Multiline 属性，$ 也匹配 '\n' 或 '\r' 之前的位置。 |
   | *            | 匹配前面的子表达式零次或多次。例如，zo* 能匹配 "z" 以及 "zoo"。* 等价于{0,}。 |
   | +            | 匹配前面的子表达式一次或多次。例如，'zo+' 能匹配 "zo" 以及 "zoo"，但不能匹配 "z"。+ 等价于 {1,}。 |
   | ?            | 匹配前面的子表达式零次或一次。例如，"do(es)?" 可以匹配 "do" 或 "does" 。? 等价于 {0,1}。 |
   | {n}          | n 是一个非负整数。匹配确定的 n 次。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。 |
   | {n,}         | n 是一个非负整数。至少匹配n 次。例如，'o{2,}' 不能匹配 "Bob" 中的 'o'，但能匹配 "foooood" 中的所有 o。'o{1,}' 等价于 'o+'。'o{0,}' 则等价于 'o*'。 |
   | {n,m}        | m 和 n 均为非负整数，其中n <= m。最少匹配 n 次且最多匹配 m 次。例如，"o{1,3}" 将匹配 "fooooood" 中的前三个 o。'o{0,1}' 等价于 'o?'。请注意在逗号和两个数之间不能有空格。 |
   | ?            | 当该字符紧跟在任何一个其他限制符 (*, +, ?, {n}, {n,}, {n,m}) 后面时，匹配模式是非贪婪的。非贪婪模式尽可能少的匹配所搜索的字符串，而默认的贪婪模式则尽可能多的匹配所搜索的字符串。例如，对于字符串 "oooo"，'o+?' 将匹配单个 "o"，而 'o+' 将匹配所有 'o'。 |
   | .            | 匹配除换行符（\n、\r）之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用像"**(.\|\n)**"的模式。 |
   | (pattern)    | 改变限定符的作用范围、分组。匹配 pattern 并获取这一匹配。所获取的匹配可以从产生的 Matches 集合得到，在VBScript 中使用 SubMatches 集合，在JScript 中则使用 $0…$9 属性。要匹配圆括号字符，请使用 '\(' 或 '\)'。 |
   | (?:pattern)  | 匹配 pattern 但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用。这在使用 "或" 字符 (\|) 来组合一个模式的各个部分是很有用。例如， 'industr(?:y\|ies) 就是一个比 'industry\|industries' 更简略的表达式。 |
   | (?=pattern)  | 正向肯定预查（look ahead positive assert），在任何匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如，"Windows(?=95\|98\|NT\|2000)"能匹配"Windows2000"中的"Windows"，但不能匹配"Windows3.1"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。 |
   | (?!pattern)  | 正向否定预查(negative assert)，在任何不匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如"Windows(?!95\|98\|NT\|2000)"能匹配"Windows3.1"中的"Windows"，但不能匹配"Windows2000"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。 |
   | (?<=pattern) | 反向(look behind)肯定预查，与正向肯定预查类似，只是方向相反。例如，"`(?<=95|98|NT|2000)Windows`"能匹配"`2000Windows`"中的"`Windows`"，但不能匹配"`3.1Windows`"中的"`Windows`"。 |
   | (?<!pattern) | 反向否定预查，与正向否定预查类似，只是方向相反。例如"`(?<!95|98|NT|2000)Windows`"能匹配"`3.1Windows`"中的"`Windows`"，但不能匹配"`2000Windows`"中的"`Windows`"。 |
   | x\|y         | 匹配 x 或 y。例如，'z\|food' 能匹配 "z" 或 "food"。'(z\|f)ood' 则匹配 "zood" 或 "food"。 |
   | [xyz]        | 字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。 |
   | [^xyz]       | 负值字符集合。匹配未包含的任意字符。例如， '\[^abc]' 可以匹配 "plain" 中的'p'、'l'、'i'、'n'。 |
   | [a-z]        | 字符范围。匹配指定范围内的任意字符。例如，'[a-z]' 可以匹配 'a' 到 'z' 范围内的任意小写字母字符。 |
   | [^a-z]       | 负值字符范围。匹配任何不在指定范围内的任意字符。例如，'\[^a-z]' 可以匹配任何不在 'a' 到 'z' 范围内的任意字符。 |
   | \b           | 匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。 |
   | \B           | 匹配非单词边界。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。 |
   | \cx          | 匹配由 x 指明的控制字符。例如， \cM 匹配一个 Control-M 或回车符。x 的值必须为 A-Z 或 a-z 之一。否则，将 c 视为一个原义的 'c' 字符。 |
   | \d           | 匹配一个数字字符。等价于 [0-9]。                             |
   | \D           | 匹配一个非数字字符。等价于 \[^0-9]。                         |
   | \f           | 匹配一个换页符。等价于 \x0c 和 \cL。                         |
   | \n           | 匹配一个换行符。等价于 \x0a 和 \cJ。                         |
   | \r           | 匹配一个回车符。等价于 \x0d 和 \cM。                         |
   | \s           | 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v]。 |
   | \S           | 匹配任何非空白字符。等价于 \[^ \f\n\r\t\v]。                 |
   | \t           | 匹配一个制表符。等价于 \x09 和 \cI。                         |
   | \v           | 匹配一个垂直制表符。等价于 \x0b 和 \cK。                     |
   | \w           | 匹配字母、数字、下划线。等价于'[A-Za-z0-9_]'。               |
   | \W           | 匹配非字母、数字、下划线。等价于 '\[^A-Za-z0-9_]'。          |
   | \xn          | 匹配 n，其中 n 为十六进制转义值。十六进制转义值必须为确定的两个数字长。例如，'\x41' 匹配 "A"。'\x041' 则等价于 '\x04' & "1"。正则表达式中可以使用 ASCII 编码。 |
   | \num         | 匹配 num，其中 num 是一个正整数。对所获取的匹配的引用。例如，'(.)\1' 匹配两个连续的相同字符。 |
   | \n           | 标识一个八进制转义值或一个向后引用。如果 \n 之前至少 n 个获取的子表达式，则 n 为向后引用。否则，如果 n 为八进制数字 (0-7)，则 n 为一个八进制转义值。 |
   | \nm          | 标识一个八进制转义值或一个向后引用。如果 \nm 之前至少有 nm 个获得子表达式，则 nm 为向后引用。如果 \nm 之前至少有 n 个获取，则 n 为一个后跟文字 m 的向后引用。如果前面的条件都不满足，若 n 和 m 均为八进制数字 (0-7)，则 \nm 将匹配八进制转义值 nm。 |
   | \nml         | 如果 n 为八进制数字 (0-3)，且 m 和 l 均为八进制数字 (0-7)，则匹配八进制转义值 nml。 |
   | \un          | 匹配 n，其中 n 是一个用四个十六进制数字表示的 Unicode 字符。例如， \u00A9 匹配版权符号 (?)。 |

   ```python
   eg:
   	[^a-zA-Z]
   ```

2. 正则表达式从左到右进行计算，并遵循优先级顺序，这与算术表达式非常类似。

   相同优先级的从左到右进行运算，不同优先级的运算先高后低。

3. re模块

   1. 匹配字符串

      1. match()方法

         从字符串的开始处进行匹配，如果在起始位置匹配成功，则返回Match对象，否则返回None,第一个字母不符合条件时则不再进行匹配

         ```python
         re.match(pattern, string, [flags=0])
         
         eg:
             import re
             pattern=r"mr_\w+"
             string="MR_SHOP mr_shop"
             match=re.match(pattern,string,re.I)
         ```

         > pattern：模式字符串，由要匹配的正则表达式转换而来
         >
         > string：要匹配的字符串
         >
         > flags：可选参数，表示标志位，用于控制匹配方式
         
         | 修饰符 | 描述                                                         |
         | :----- | :----------------------------------------------------------- |
         | re.I   | 使匹配对大小写不敏感                                         |
         | re.L   | 做本地化识别（locale-aware）匹配                             |
         | re.A   | 对于\w \W \b \B \d \D \s \S 值进行ASCII匹配                  |
         | re.M   | 多行匹配，影响 ^ 和 $                                        |
         | re.S   | 使 . 匹配包括换行在内的所有字符                              |
         | re.U   | 根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B.      |
         | re.X   | 忽略模式字符串中未转义的空格和注释，该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。 |
         
           match对象中包含了匹配值的位置和匹配数据:
         
           1. start()方法获取匹配值的起始位置
           2. end()方法获取匹配值的结束位置
           3. span()方法返回匹配位置的元组
           4. string()方法获取要匹配的字符串
           5. group()方法获取匹配的子字符串

      2. search()方法

         在整个字符串中搜索第一个匹配的值，如果在起始位置匹配成功，则返回Match对象，否则返回None

         ```python
         re.search(pattern, string, [flags=0])
         ```

      3. findall()方法

         在整个字符串中搜索所有符合正则表达式的字符串，并以列表的形式返回。如果匹配成功，则返回包含匹配结构的列表，否则返回空列表。

         ```python
         re.findall(pattern, string, [flags=0])
         ```

         如果在指定的模式字符串中包含分组，则返回与分组匹配的文本列表

   2. 使用sub()方法替换字符串

      ```python
      re,sub(pattern,repl,string,count,flags)
      ```

   >pattern：模式字符串
   >
   >repl：替换的字符串
   >
   >string：要被查找替换的原始字符串
   >
   >count：可选参数，表示模式匹配后替换的最大次数，默认值为0，表示替换所有的匹配
   >
   >flags：可选参数，表示标志位，用于控制匹配方式

   3. 使用split()方法分割字符串

      根据正则表达式分割字符串，并以列表的形式返回

      ```python
      re.split(parttern,string,[maxsplit],[flags])
      ```

      > maxsplit：可选参数，表示最大的拆分次数

      

#	函数

1. 创建函数

   ```python
   def functionname([parameterlist]):
       ['''comments''']
       [functionbody]
   ```

   > parameterlist：可选参数，用于指定向函数中传递的参数，不需要说明形参类型
   >
   > comments：可选参数，表示为函数指定注释，如果指定了comments参数，那么在调用函数输入函数名称及左侧小括号时会显示该函数的帮助信息
   >
   > functionbody：可选参数，用于指定函数体，如果有返回值可以使用return语句返回

   即使函数没有参数也必须保留一对空的"()"

   functionbody和comments必须保持一定的缩进

2. 参数传递

   1. 当实参为**不可变对象**时进行值传递，改变形参的值不影响实参；当实参为**可变对象**时进行引用传递，形参和实参同时改变

   2. 位置参数也称为必备参数，必须按照正确的顺序传到函数中，即调用时的数量和位置必须与定义时一样
   
   3. 关键字参数是指使用形参的名字来确定输入的参数值，这种方式不需要与形参位置完全一致
   
   4. 默认值参数是在定义函数时可以直接指定形参的默认值，在没有实参传入时会直接使用该默认值而不会抛出异常，**指定默认的形参必须在所有参数的最后**(可使用\__defaults__方法查看函数的默认值参数的当前值)
   
   5. 最好使用None作为可变对象的默认值，再加上必要的检查代码
   
   6. 可变参数：
   
      可变参数也称不定长参数，即传入函数中的实参可以是任意多个
   
      1. *parameter
   
         这种形式表示接收任意多个实参并将其放到一个**元组**中
   
      2. **parameter
   
         这种形式表示接收任意多个类似**关键字参数**一样显示赋值的实参，并将其放到一个**字典**中
   
   7. 参数列表中的/与*
   
      如有函数定义
   
      ```python
      def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
      ```
   
      - `pos1` 和`pos2`只能以位置的形式传参，而不能以关键字的形式传参。
      - `pos_or_kwd`可以以位置和关键字的形式传参
      - `kwd1`和`kwd2`只能以关键字的形式传参
   
   8. 函数参数中的冒号与箭头
   
      函数参数中的冒号是参数的类型建议符，告诉函数调用者希望传入的实参的类型
   
      函数后面跟着的箭头是函数返回值的类型建议符，用来说明该函数返回的值是什么类型
   
      **值得注意的是，类型建议符并非强制规定和检查，也就是说即使传入的实际参数与建议参数不符，也不会报错**
   
   7. 传递参数时的序列解包
   
      1. 调用含有多个位置参数的函数时，如果想要使用一个已经存在的可迭代对象作为函数的实参，可以在可迭代对象的名称前加`*`
      2. 调用含有多个位置参数的函数时，如果想使用一个已经存在的字典作为函数的实参，可以在字典的名称前加`**`，该方法会将字典转换为类似于关键字参数的形式进行参数传递，该方法要求实参字典中的所有键都必须是函数的形参名称或者与函数中两个星号的可变长度参数相对应
   
   8. 返回值：
   
      返回值可以是任意类型，无论return语句出现在函数的什么位置，只要得到执行，就会直接结束函数的运行
   
      ```python
      result=return[value]
      
      return value
      ```
   
      > result：用于保存返回结果，如果返回一个值，该值可以为任意类型；如果返回多个值，那么保存的是一个元组
      >
      > value：可选参数，用于指定要返回的值，可以返回一个值也可以返回多个值
   
      当函数中没有return语句或省略了return语句的参数时将返回None，即返回空值
   
   9. 变量的作用域：
   
      1. 局部变量
   
         在函数内部定义并使用的变量，只在函数内部有效
   
      2. 全局变量
   
         在函数体外定义的变量
   
         在函数体内定义并且用global关键字修饰
   
      在局部变量和全局变量重名时，对函数体的变量进行赋值不影响函数体外的变量
   
      Python 会假设任何在函数内赋值的变量都是局部的，因此，如果要在函数内部使用全局变量，必须先用global 语句声明
   
   10. 匿名函数(lambda)
   
      匿名函数是指没有名字的函数，这样的函数只能使用一次
   
      ```python
      result=lambda [arg1 [,arg2,...,argn] ]:expression
      
      eg:
          list.sort(key=lambda x:x[1] , reverse=False)
          f = lambda x,y,z : x+y+z
      ```
   
      > result：用于调用lambda表达式，接收lambda的返回值
      >
      > [arg1 [,arg2,...,argn] ]：可选参数，用于指定向要传递的参数列表
      >
      > expression：必选参数，指定一个实现具体功能的表达式，表达式的计算结果作为返回值
   
      表达式只能有一个，即只能返回一个值，且不能出现其他非表达式语句(如for或while)，但可以调用其他函数
   
      首要用途是指定短小的回调函数
   
   11. 函数内定义的函数称为内部函数，内部函数的创建过程在外部函数的执行过程中，外部不可直接调用内部函数，可以通过return内部函数的方式在外部执行
   
   12. 生成器函数
   
       包含yield语句的函数可以用来创建生成器对象，这样的函数也称为生成器函数。yield语句与return语句的作用相似，都是用来从函数中返回值，但是yield语句返回一个值后会暂停或挂起后面代码的执行，在下一次通过生成器对象的`__next__()`方法、内置函数next()、for循环遍历生成器对象元素或其他方式显式"索要"数据时恢复执行，具有惰性求值的特点。
   
       ```python
       def f():
           a, b = 1, 1
           while True:
               yield a
               a, b = b, a + b
       
       
       c = f()
       for i in range(10):
           print(c.__next__(), end=' ')
       # 1 1 2 3 5 8 13 21 34 55 
           
       for i in f():
           if i > 100:
               print(i, end=' ')
               break
       # 144 
       ```
   
       



#	面向对象(Object  Oriented)

1. 概述

   1. 对象(Object)：一个抽象概念，表示任意存在的事物，通常将对象划分为静态部分和动态部分。静态部分被称为"属性"，任何对象都有自身属性；动态部分被称为"行为"，即对象执行的动作

   2. 类(Class)：类是封装对象的属性和行为的载体，即具有相同属性和行为的一类实体被称为类。在Python中，类是一种抽象概念，对象是类的实例

   3. 面向对象程序设计的特点：

      1. 封装

         面向对象编程的核心思想，将对象的属性和行为封装起来，其载体就是类，类通常会对用户隐藏其细节，这就是封装的思想。

         采用封装思想保证了类内部数据结构的完整性，用户仅能执行类允许公开的数据，避免了外部对内部数据的影响，提高程序的可维护性。

      2. 继承

         继承是实现重复利用的重要手段，子类通过继承复用了父类的属性和行为同时添加了子类特有的属性和行为

      3. 多态

         父类衍生出不同的子类，子类继承父类特征的同时也具有了自己的特征，且能够实现不同的效果

2. 类(Class)

   类是用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。

   在使用类时，需要先定义类，再创建类的实例，通过类的实例就可以访问类中的属性和方法了

   1. 定义类

      ```python
      class Classname:
      	'''
      	类的帮助信息
      	'''
      	statement
      ```

      > Classname：用于指定类名，一般使用大写字母开头，如果类名中包括两个单词，则第二个单词也用大写字母开头，即"驼峰式命名法"
      >
      > statement：类体，主要由类变量(或类成员)、方法和属性等定义语句组成，也可以使用pass语句代替

   2. 创建类的实例

      ```python
      ClassName(parameterlist)
      ```

      > ClassName：必选参数，指定具体的类
      >
      >  parameter：可选参数，当创建一个类时，如果没有创建\__init__()方法或该方法只有一个self参数，parameterlist可以省略

   3. 创建\__init__()方法

      该方法是一个特殊的方法，被称为类的构造函数或初始化方法，当创建了这个类的实例时就会调用该方法

      \__init__()方法必须包含一个self参数，且必须是第一个参数，self 在定义类的方法时是必须有的

      self参数是一个指向实例本身的引用，用于访问类中的属性和方法，在方法调用时会自动传递实际参数self

   4. 创建类的成员并访问

      类的成员主要由成员方法和数据成员组成

      1. 成员方法

         类中定义的函数，该函数是在类的实例上操作的函数

         1. 实例方法
         
         ```python
         def functionname(self,paramentlist):
         	block
         ```
         
         > functionname：指定方法名，一般使用小写字母开头
         >
         > self：必要参数，表示当前的实例，且必须是方法的第一个形参，在调用方法时并不需要传递这个参数而是会把对象隐式绑定到self参数
         >
         > block：方法体，实现具体的功能
         
         方法调用：
         
          ```python
         instanceName.functionname(parameterlist)
          ```
         
         > instanceName：类的实例的名称
         
         2. 静态方法和类方法
         
            静态方法和类方法都可以通过类名和对象名调用，但这两种方法中不能直接访问属于对象的成员，只能访问属于类的成员。一半以cls作为类方法的第一个参数表示该类自身，在调用类方法时不需要为该参数传递值；静态方法可以不接受任何参数
         
            ```python
            @classmethod	# 装饰器，声明类方法
            def functionname(cls):
                block
                
            @staticmethod	# 装饰器，声明静态方法
            def functionname():
                block
            ```
         
            
         
           2. 数据成员
         
              类中定义的变量，即属性，根据定义位置分为类变量和实例变量
         
              1. 类变量
         
                 定义在类中且在方法外的变量，在类的所有实例中共享值，可以通过类名称或实例名访问
         
                 可以动态地为类和对象添加修改变量，结果作用于所有实例
         
                 对类变量的修改应使用`类名.类变量名`的方式进行修改，若用`实例名.类变量名`进行修改会自动创建一个同名的实例变量
         
              2. 实例变量
         
                 定义在类的方法中的变量，只作用于当前实例中，只能通过实例名访问
              
                 实例变量主要在构造方法中定义
                 
                 实例变量可以通过实例名称更改 ，且更改后不影响该类的另一个实例中对应的实例变量的值

   5. 访问限制

      为了保证类内部某些属性和方法不被外部所访问，可以在属性或者方法名前面添加单下划线、双下划线、或首尾添加双下划线从而限制访问权限

      1. 首尾双下划线(\__foo__)：定义特殊方法，一般为系统定义名字
      2. 单下划线(_foo)：表示保护(protected)类型的成员，只允许类本身和子类进行访问，能通过实例名访问，但不能使用"from module import *"语句导入
      3. 双下划线(\__foo)：表示私有(private)类型的成员，只允许定义该方法的类本身进行访问，不能通过类的实例直接进行访问，但可以通过"instancename.\_ClassName__xxx"方式访问

3. 属性(Property)

   属性是一种特殊形式的成员方法，综合了公开数据成员和成员方法二者的优点，既可以像成员方法一样对值进行必要的检查，又可以想数据成员一样灵活地访问。不同于类的数据成员，属性不返回存储的值，访问它时将计算它的值。

   通过`@property`装饰器或`property`函数将方法转换为属性，实现用于计算的属性

   将方法转换为属性之后可以直接通过方法名来访问方法而不需要再添加一对小括号"()"

   通过属性可以实现安全保护机制

   ```python
   @property
   def methodname(self):
       block
   ```

   > block：方法体，通常以return语句结束用以返回计算结果

   1. 创建一个可读取但不能修改的属性，可以使用`@property`实现只读属性，使其无法修改其值，无法删除对象属性，也无法为对象增加与属性同名的新成员。

      ```python
      class Test:
          def __init__(self, value):
              self.__value = value
      
          @property
          def value(self):  # 读取私有数据成员的值
              return self.__value
      
      
      t = Test(3)
      print(t.value)	# 3
      ```

   2. 创建一个可读、可修改而不允许删除的属性

      ```python
      class Test:
          def __init__(self, value):
              self.__value = value
      
          def __get(self):  # 读取私有数据成员的值
              return self.__value
      
          def __set(self, v):  # 修改私有数据成员的值
              self.__value = v
      
          value = property(__get, __set)  # 可读可写属性，指定相应的读写方法
      
          def show(self):
              print(self.__value)
      
      
      t = Test(3)
      print(t.value)  # 3
      t.show()  # 3
      
      t.value = 5
      t.show()  # 5
      ```

   3. 创建一个可读、可修改、可删除的属性

      ```python
      class Test:
          def __init__(self, value):
              self.__value = value
      
          def __get(self):  # 读取私有数据成员的值
              return self.__value
      
          def __set(self, v):  # 修改私有数据成员的值
              self.__value = v
      
          def __del(self):  # 删除对象的私有数据成员
              del self.__value
      
          value = property(__get, __set, __del)  # 可读可写可删除属性，指定相应的读写方法
      
          def show(self):
              print(self.__value)
      
      
      t = Test(3)
      print(t.value)  # 3
      t.show()  # 3
      
      t.value = 5
      t.show()  # 5
      
      del t.value
      t.show()    # 'Test' object has no attribute '_Test__value'
      ```

4. 继承

   继承表示这个类拥有它继承的类的所有公有成员和受保护成员，被继承的类称为父类或基类，新的类称为子类或派生类

   .号表示对.号前的对象调用其方法或访问其成员，而这个访问的过程，就是从继承搜索树的叶子节点，即子类开始寻找.号后面的函数或成员，如果能找到，就停止搜索；如果找不到，就往上的父类找。

   1. 基本语法

      ```python
      class ClassName(baseclasslist):
          statement
      ```

      > baseclasslist：指定要继承的基类，可以有多个，如果不指定将使用所有Python对象的根类

   2. 方法重写

      当基类中的某个方法不完全适用于派生类时，就需要在派生类中重写基类的方法

   3. 如果需要在派生类中调用基类的方法，可以使用内置函数`super()`或者通过`基类名.方法名()`的方式来实现

      在子类中定义\__init__()方法时，不会自动调用父类的初始化方法，因此调用父类的初始化方法需要进行必要的初始化

      ```python
      super(Child,self).__init__()
      
      Parent.__init__(self)
      ```
      
   4. Python支持多继承，如果父类中有相同的方法名，而在子类中使用时没有指定父类名，则Python解释器将从左向右按顺序进行搜索，使用第一个匹配的成员
   
5. 特殊方法

   https://docs.python.org/3/reference/datamodel.html#special-method-names



#	异常处理

当程序运行时，发生了未处理的异常，Python就将终止执行程序，并以堆栈回溯（Traceback，也 称向后追踪）的形式显示异常发生的上下文。

1. 标准异常

   | 异常名称                  | 描述                                               |
   | :------------------------ | :------------------------------------------------- |
   | BaseException             | 所有异常的基类                                     |
   | SystemExit                | 解释器请求退出                                     |
   | KeyboardInterrupt         | 用户中断执行(通常是输入^C)                         |
   | Exception                 | 常规错误的基类                                     |
   | StopIteration             | 迭代器没有更多的值                                 |
   | GeneratorExit             | 生成器(generator)发生异常来通知退出                |
   | StandardError             | 所有的内建标准异常的基类                           |
   | ArithmeticError           | 所有数值计算错误的基类                             |
   | FloatingPointError        | 浮点计算错误                                       |
   | OverflowError             | 数值运算超出最大限制                               |
   | ZeroDivisionError         | 除(或取模)零 (所有数据类型)                        |
   | AssertionError            | 断言语句失败                                       |
   | AttributeError            | 对象没有这个属性                                   |
   | EOFError                  | 没有内建输入,到达EOF 标记                          |
   | EnvironmentError          | 操作系统错误的基类                                 |
   | IOError                   | 输入/输出操作失败                                  |
   | OSError                   | 操作系统错误                                       |
   | WindowsError              | 系统调用失败                                       |
   | ImportError               | 导入模块/对象失败                                  |
   | LookupError               | 无效数据查询的基类                                 |
   | IndexError                | 序列中没有此索引(index)                            |
   | KeyError                  | 映射中没有这个键                                   |
   | MemoryError               | 内存溢出错误(对于Python 解释器不是致命的)          |
   | NameError                 | 未声明/初始化对象 (没有属性)                       |
   | UnboundLocalError         | 访问未初始化的本地变量                             |
   | ReferenceError            | 弱引用(Weak reference)试图访问已经垃圾回收了的对象 |
   | RuntimeError              | 一般的运行时错误                                   |
   | NotImplementedError       | 尚未实现的方法                                     |
   | SyntaxError               | Python 语法错误                                    |
   | IndentationError          | 缩进错误                                           |
   | TabError                  | Tab 和空格混用                                     |
   | SystemError               | 一般的解释器系统错误                               |
   | TypeError                 | 对类型无效的操作                                   |
   | ValueError                | 传入无效的参数                                     |
   | UnicodeError              | Unicode 相关的错误                                 |
   | UnicodeDecodeError        | Unicode 解码时的错误                               |
   | UnicodeEncodeError        | Unicode 编码时错误                                 |
   | UnicodeTranslateError     | Unicode 转换时错误                                 |
   | Warning                   | 警告的基类                                         |
   | DeprecationWarning        | 关于被弃用的特征的警告                             |
   | FutureWarning             | 关于构造将来语义会有改变的警告                     |
   | OverflowWarning           | 旧的关于自动提升为长整型(long)的警告               |
   | PendingDeprecationWarning | 关于特性将会被废弃的警告                           |
   | RuntimeWarning            | 可疑的运行时行为(runtime behavior)的警告           |
   | SyntaxWarning             | 可疑的语法的警告                                   |
   | UserWarning               | 用户代码生成的警告                                 |

2. 异常处理语句

   1. try...except语句

      ```python
      try:
          block1
      except [ExceptionName [as alias]]:
          block2
      ```

      > block1：表示可能出现错误的代码块
      >
      > ExceptionName [as alias]：可选参数，用于指定要捕获的异常，
      >
      > as alias：可选参数，表示为当前的异常指定一个别名，即接收错误信息的变量

      >- 首先，执行 try 子句（在关键字 try 和关键字 except 之间的语句）。
      >- 如果没有异常发生，忽略 except 子句，try 子句执行后结束。
      >- 如果在执行 try 子句的过程中发生了异常，那么 try 子句余下的部分将被忽略。如果异常的类型和 except 之后的名称相符，那么对应的 except 子句将被执行。
      >- 如果一个异常没有与任何的 except 匹配，那么这个异常将会传递给上层的 try 中。

      如果不指定异常名称则表示捕获全部异常

      要捕获多个异常可使用多个except语句或将异常放在一个括号里成为一个元组

      只执行最先匹配的一个except

      最后一个except子句可以忽略异常的名称，它将被当作通配符使用

   2. try...except...else语句

      else语句用于指定当try语句无异常时的要执行的语句块

      如果使用这个子句，那么必须放在所有的 except 子句之后

   3. try...except...finally语句

      无论程序中有无异常产生，finally代码块中的代码都会执行

      此功能通常在释放外部资源时出现

      如果一个异常在 try 子句里（或者在 except 和 else 子句里）被抛出，而又没有任何的 except 把它截住，那么这个异常会在 finally 子句执行后被抛出

   4. raise语句

      自行触发异常，触发异常后，后面的代码不会执行

      ```Python
      raise [Exception [, args [, traceback]]]
      
      eg:
          x = 10
      	if x > 5:
          	raise Exception('x 不能大于 5。x 的值为: {}'.format(x))
      ```

      > Exception：异常的类型，指定其名称
      >
      > args：自己提供的异常参数
      >
      > traceback：跟踪异常对象，用于异常的回溯对象

      为了能够捕获异常，"except"语句必须有用相同的异常来抛出类对象或者字符串

   5. 自定义异常

      创建一个新的异常类来拥有自己的异常。异常类继承自 Exception 类，可以直接继承，或者间接继承

      当创建一个模块有可能抛出多种不同的异常时，一种通常的做法是为这个包建立一个基础异常类，然后基于这个基础类为不同的错误情况创建不同的子类

      大多数的异常的名字都以"Error"结尾，就跟标准的异常命名一样

   6. assert语句

      用于对程序某个时刻必须满足的条件进行验证

      ```python
      assert expression [,reason]
      ```

      > expression：条件表达式，如果该表达式的值为真则pass，值为假则抛出AssertionError异常
      >
      > reason：可选参数，用于对判断条件进行描述

      通常与异常处理语句结合使用

      assert语句只在调试阶段有效

      可以通过在执行Python命令时加入-O参数来关闭assert语句





#	闭包(Closure)

> 内部函数对外部函数作用域里变量的引用

闭包内的闭包函数私有化了变量，完成了数据的封装，类似于面向对象

通过返回内部函数的方式，一个代表函数的变量可以封装该内部函数及该内部函数在其对应的外部函数中调用的变量

函数做闭包的时候，外层的变量会被销毁，而在调用内层函数的时候会重新创建一个值和引用相同的变量

```python
def func(obj):  # 外部函数
    a = 1  # 外部函数的变量

    def func1():  # 内部函数
        obj[0] += a
        print(obj)

    return func1  # 返回内部函数


var = func([3, 2, 1, 0])  # 调用外部函数，通过返回值使变量var可以调用闭包函数
# 闭包函数封装了传递进去的数值，并且可以重复调用，调用后变化的数值仍然封装在闭包函数中供下一次调用
var()  # [4, 2, 1, 0]
var()  # [5, 2, 1, 0]
var()  # [6, 2, 1, 0]
```





#	装饰器/语法糖(Decorators)

```python 
def func1(func):  # 外部闭包函数的参数时被装饰的函数对象
    def func2():
        print("This is the function 2.")
        return func()  # 返回被装饰函数的调用，即函数执行的结果

    return func2    # 返回闭包函数对象名


@func1
def myprint():
    print("This is the original function.")


myprint()

'''
This is the function 2.
This is the original function.
'''
```

装饰器会自动实现闭包调用，而在这个闭包函数中最后返回值时会执行一次被装饰的函数，通过这种方式实现在不改变原函数的基础上添加额外的功能，即函数的入口变成了在装饰函数中

装饰器函数带参数，可以在最外层多一层包装来接收装饰器的参数

被装饰函数带参数时，可以在最内部函数传入参数

多个装饰器的装饰过程是: 离函数最近的装饰器先装饰，然后外面的装饰器再进行装饰，由内到外的装饰过程

```python
def func1(type):
    def func2(func):
        def func3(x, y):
            if type == 1:
                print('各+5')
                x += 5
                y += 5
            else:
                print('各+10')
                x += 10
                y += 10
            return func(x, y)

        return func3

    return func2


@func1(type=1)
def myprint1(x, y):
    print(x, y)


@func1(type=2)
def myprint2(x, y):
    print(x, y)


myprint1(5, 5)
myprint2(5, 5)

'''
各+5
10 10
各+10
15 15
'''
```



#	数据库操作

> 为了对数据库进行统一的操作，在Python Database API 2.0 规范中定义了Python数据库API接口的各个部分，如模块接口、连接对象、游标对象、类型对象和构造器、DB API的可选拓展以及可选的错误处理机制等。

![](Pictures\数据库操作通用流程-16577780132491.jpg)

1. 数据库编程接口

   1. 连接对象

      > 数据库连接对象(Connection Object)主要提供获取数据库游标对象和提交、回滚事务的方法，以及关闭数据库连接

      1. 使用connect()函数获取连接对象

         | 参数     | 说明                                 |
         | -------- | ------------------------------------ |
         | dsn      | 数据源名称，给出该参数表示数据库依赖 |
         | user     | 用户名                               |
         | password | 用户密码                             |
         | host     | 主机名                               |
         | database | 数据库名称                           |

         ```python
         conn = pymysql.connect(host='localhost',
                                user='user',
                                password='passwd',
                                db='test',
                                charset='utf8',
                                cursorclass=pymysql.cursors.DictCursor)
         ```

         **参数使用时要以具体的数据库模块为准**

      2. 连接对象的方法

         | 方法名     | 说明                                                    |
         | ---------- | ------------------------------------------------------- |
         | close()    | 关闭数据库连接                                          |
         | commit()   | 提交事务                                                |
         | rollback() | 回滚事务                                                |
         | cursor()   | 获取游标对象，操作数据库，如执行DML操作，调用存储过程等 |

         > commit()方法用于提交事务，事务主要用于处理数据量大、复杂度高的数据，可维护数据库的完整性。

         > 事务(Transaction)是由一系列对系统中数据进行访问与更新的操作所组成的一个程序执行逻辑单元。
         >
         > 对数据库的数据进行批量或连表操作时，为了保证数据的一致性和正确性，我们需要添加事务管理机制进行管理。当对数据库的数据进行操作失败时，事务管理可以很好保证所有的数据回滚到原来的数据，如果操作成功，则保证所有需要更新的数据持久化。

   2. 游标对象

      > 游标对象(Cursor Object)代表数据库中的游标，，用于指示抓取数据操作的上下文，主要提供执行SQL语句、调用存储过程、获取查询结果等方法。
      >
      > 
      >
      > **游标和对象的区别分别是：**
      >
      > **1、游标是：**游标范例并非特定于Python，而是databases themselves中的一个频繁数据结构。并且根据底层实现，可以生成几个游标共享与数据库相同的连接。
      >
      > 关闭游标应释放与查询关联的资源，包括从不从数据库中提取的任何结果（或者提取但未使用），但不会消除与数据库本身的连接，因此可以在同一数据库上获得新的游标而无需再次验证。
      >
      > **2、对象是：**连接对象是您与数据库的连接，当您完全与数据库完成对话时，请关闭连接对象。游标对象是对查询结果集的迭代器。当你完成这个结果集时关闭这些。
      >
      > 并且Connect()是网络连接到数据库，它只是真正的用途是返回游标。 PEP-249，其中指定了DBApi 2.0，没有明确定义连接或游标是什么，也不明确每个方法必须执行哪些操作。
      >
      > 
      >
      > **游标的作用是：**
      >
      > 游标在数据库的事务回滚中有非常重要的作用。由于对数据库的操作会暂时存放在游标中，只要不提交，就可以根据游标中的内容进行回滚。这样有利于数据库的安全。
      >
      > 
      >
      > **游标的类型是：**
      >
      > **1、隐式游标：**增删改等操作oracle都会自动创建游标，暂时保存操作结果，也就是说能够回滚的操作都会引发游标的创建。
      >
      > **2、显式游标：**由开发人员通过程序显示控制，用于从表中取出多行数据，并将多行数据一行一行的单独进行处理。
      
      > 游标对象属性：
      >
      > description：数据库列类型和值的描述信息
      >
      > rowcount：回返结果的行数统计信息，如SELECT/UPDATE/CALLPROC

      | 方法名                               | 说明                                                 |
      | ------------------------------------ | ---------------------------------------------------- |
      | callproc(procname,[,parameters]      | 调用存储过程，需要数据库支持                         |
      | close（）                            | 关闭当前游标                                         |
      | excute（operation[,parameters]）     | 执行数据库操作，SQL语句或者数据库命令                |
      | excutemany（operation,seq_of_params] | 批量操作数据库，如批量更新                           |
      | fetchone（）                         | 获取查询结果集中的下一条记录                         |
      | fetchmany(size）                     | 获取指定数量的记录                                   |
      | fetchall()                           | 获取结果集的所有记录                                 |
      | nextset()                            | 跳至下一个可用的结果集                               |
      | arraysize                            | 指定fetchmany()获取的行数，默认为1                   |
      | setinputsize(sizes)                  | 设置在调用execute*()方法时分配的内存区域大小         |
      | setoutputsize(sizes)                 | 设置列缓冲区大小，对大数据列(如LONGS和BLOBS)尤其有效 |
      
   
2. SQLite

   > 与许多其他数据库管理系统不同，SQLite不是一个客户端/服务器结构的数据库引擎，而是一种嵌入式数据库，它的数据库就是一个文件。SQLite将整个数据库，包括定义、表、索引以及数据本身，作为一个单独的、可跨平台使用的文件储存在主机中。
   >
   > 由于SQLite本身是C写的，而且体积很小，所以经常被集成到各种应用程序中。
   >
   > Python中内置了SQLite3，因此不需要安装任何模块直接使用SQLite。

   1. 创建数据库文件

      ```Python
      import sqlite3
      
      conn = sqlite3.connect('mrsoft.db')
      cursor = conn.cursor()
      cursor.execute('create table user(id int(10) primary key, name varchar(20))')
      cursor.close()
      conn.close()
      ```

   2. 操作SQLite

      1. 新增数据

         ```sql
         insert into tablename(字段名1，字段名2...) values(字段值1，字段值2...)
         ```

         sql语句执行后需使用commit()函数将游标中的事务提交

      2. 查询数据

         ```sql
         select 字段名1，字段名2... from tablename where 查询条件
         ```

         以上sql语句的查询结果存储在游标中，还需要游标对象的方法将结果提取出来

         1. fetchone()：获取查询结果集中的下一条记录

            ```python
            import sqlite3
            
            conn = sqlite3.connect('mrsoft.db')
            cursor = conn.cursor()
            
            cursor.execute('select * from user')
            result =cursor.fetchone()
            print(result)
            
            cursor.close()
            conn.close()
            ```

            该方法返回的result为一个元组

         2. fetchmany(size)：获取指定数量的数据

            ```python
            import sqlite3
            
            conn = sqlite3.connect('mrsoft.db')
            cursor = conn.cursor()
            
            cursor.execute('select * from user')
            result =cursor.fetchmany(2)
            print(result)
            
            cursor.close()
            conn.close()
            ```

            size默认值为1，返回的result为一个列表

         3. fetchall()：获取结构集的所有记录

            ```python
            import sqlite3
            
            conn = sqlite3.connect('mrsoft.db')
            cursor = conn.cursor()
            
            cursor.execute('select * from user')
            result =cursor.fetchall()
            print(result)
            
            cursor.close()
            conn.close()
            ```

            返回的result为一个列表，列表中包含所有user表中数据组成的元组

         使用占位符替代具体的数值然后使用一个元组来替换占位符可以避免SQL注入的风险

         ```python
         cursor.execute('select * from user where id > ?',(1,))
         ```

      3. 修改数据

         ```sql
         update tablename set 字段名 = 字段值 where 查询条件
         ```

      4. 删除数据

         ```sql
         delete from tablename where 查询条件
         ```



#	GUI

> GUI (Graphical User Interface)：图形用户界面，又称图形用户接口，是指采用图形方式显示的计算机操作用户界面。
>
> 图形用户界面是一种人与计算机通信的界面显示格式，允许用户使用鼠标等输入设备操纵屏幕上的图标或菜单选项，以选择命令、调用文件、启动程序或执行其它一些日常任务。与通过键盘输入文本或字符命令来完成例行任务的字符界面相比，图形用户界面有许多优点。图形用户界面由窗口、下拉菜单、对话框及其相应的控制机制构成，在各种新式应用程序中都是标准化的，即相同的操作总是以同样的方式来完成，在图形用户界面，用户看到和操作的都是图形对象，应用的是计算机图形学的技术。



| 常用GUI工具包 | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| wxPython      | 它是Python编程语言中的跨平台图形用户界面。该工具包允许程序员创建高效，功能强大的Python用户界面。WxPython快速，简便，简单。WxPython是Python扩展模块的一部分，该模块绑定了著名的wxWidget跨平台库的GUI元素。这些元素是用C ++语言编写的。WxPython是开源的。可以根据需要查看和修改源代码。它还允许志愿者贡献，修复或改进设计。 |
| Kivy          | Kivy GUI框架是更有趣的Python项目，因为它是MIT许可的，并且基于OpenGL ES2。OpenGL ES 2是第一个移动图形API，并且仍然是最可用的3D图形API。它是一个开放源代码的Python库，用于创建新的用户界面和快速开发Web应用程序。Kivy是针对Python的最佳GUI库之一，它是围绕主循环创建的，从而使其与游戏开发兼容。此应用程序是专业设计和维护的，主要用作商业产品。该框架可与Kivy的图形引擎保持稳定，并使用现代和快速的图形管线。Kivy Python GUI构建器几乎支持所有平台，例如Windows，Linux，OS X和Android。而且，Kivy是一个更有用的GUI库，因为它对移动和桌面应用程序使用相同的代码。此外，Kivy是一个开源Python GUI工具包，用于移动应用程序和其他多点触控应用程序。 |
| Flexx         | Flexx 是一个纯 Python 工具包，用来创建图形化界面应用程序。其使用 Web 技术进行界面的渲染。可以用 Flexx来创建桌面应用，同时也可以导出一个应用到独立的 HTML 文档。因为使用纯 Python 开发，所以 Flexx 是跨平台的。只需要有 Python和浏览器就可以运行。如果是使用桌面模式运行，推荐使用 Firefox 。 |
| PyQt          | PyQt是Qt的Python UI框架，Qt是由挪威一家私营公司拥有的，用C ++语言编写的流行的跨平台GUI框架应用程序之一。它是Qt绑定，由Riverbank Computing Limited开发。PyQT支持Windows，OS X，Linux，iOS和Android。PyQT有两个版本，一个是针对QT 4.x构建的PyQT4。另一个是针对QT 5.x构建的PyQT5。但是，它主要用于桌面应用程序。该版本均与Python 2和3兼容。它的许可证在GPL版本3下。您可以尝试使用其免费版本，但其中某些功能不可用。同时QT的商业版本价格不菲，此外，如果您正在使用的应用程序是开源的，那么您将使用具有免费许可证的PyQT。PyQT结合了QT和Python的优点，并证明自己是图形用户界面。有时，它不只是Python GUI工具包。 |
| Tkinter       | Tkinter通常使用Tk和Python的标准GUI框架与Python捆绑在一起。它以其简单性和图形用户界面而受欢迎。它是开源的，并且在Python许可下可用。在其他Python GUI工具包中，Tkinter是Python中最常用的GUI框架。Django框架也使用Tkinter GUI制作网页。选择Tkinter的优点之一是，由于它是默认设置，因此有大量资源，包括代码和参考书。同样，在已建立且活跃的社区中，有很多用户可以在任何疑问的情况下为您提供帮助。 |
| Pywin32       | Pywin32有三种很重要的模块，分别是win32api、win32gui和win32con，能够实现访问windows的API。 |
| PyGTK         | PyGTK真正具有跨平台性,它能不加修改地,稳定运行各种操作系统之上,如Linux,Windows,MacOS等.除了简单易用和快速的原型开发能力外,PyGTK还有一流的处理本地化语言的独特功能.PyGTK是自由软件,所以你能几乎没有任何限制的使用，修改，分发，研究它，它是基于LGPL协议发布的．底层的GTK+提供了各式的可视元素和功能,如果需要,你能开发在GNOME桌面系统运行的功能完整的软件。GTK+是用C语言开发的，具有跨平台的GUI库，它是GNOME桌面系统和GIMP图象编辑器的开发工具箱． |
| pyui4win      | pyui4win是一个开源的采用自绘技术的界面库。支持C和python。pyui4win有所见即所得界面设计器，让C开发人员和python开发人员直接用设计工具设计界面，而不用关心界面如何生成和运行，可以显著缩短界面开发时间。在pyui4win中，界面甚至可以完全交给美工去处理，开发人员可以只负责处理业务逻辑，把开发人员彻底从繁杂的界面处理中解放出来。 |
| Delphi VCL    | 该 可视化组件库 （VCL）是用于开发的Microsoft Windows应用程序的用户界面的视觉基于组件的面向对象的框架。它以对象Pascal编写。VCL是一组可视化组件，用于以Delphi和C ++语言快速开发Windows应用程序。VCL包含各种可视，非可视和实用程序类，用于执行诸如构建Windows应用程序，Web应用程序，数据库应用程序和控制台应用程序之类的任务。VCL中的所有类均来自TObject。TObject引入了实现基本行为的方法，例如构造，销毁和消息处理。通过使用用于Delphi的Python（P4D）将其与Python集成，您可以轻松地执行Python脚本，创建新的Python模块和新的Python类型。您可以将Python扩展创建为DLL等。P4D使使用Python作为Delphi应用程序的脚本语言变得非常容易。它还附带了广泛的演示和教程，可随时使用和开发以解决现实问题。 |



> 应用程序对象：管理主事件循环，主事件循环是wxPython程序的动力，如果没有应用程序对象，wxPython应用程序将不能运行。
>
> > 1. 事件循环一般用exec()函数开启。QApplicaion::exec()、QMessageBox::exec()都是事件循环。其中前者又被称为主事件循环。
> >
> >    >事件循环首先是一个无限“循环”，程序在exec()里面无限循环，能让跟在exec()后面的代码得不到运行机会，直至程序从exec()跳出。从exec()跳出时，事件循环即被终止。QEventLoop::quit()能够终止事件循环。
> >    >
> >    >其次，之所以被称为“事件”循环，是因为它能接收事件，并处理之。当事件太多而不能马上处理完的时候，待处理事件被放在一个“队列”里，称为“事件循环队列”。当事件循环处理完一个事件后，就从“事件循环队列”中取出下一个事件处理之。当事件循环队列为空的时候，它和一个啥事也不做的永真循环有点类似，但是和永真循环不同的是，事件循环不会大量占用CPU资源。
> >    >
> >    >事件循环的本质就是以队列的方式再次分配线程时间片。
> >
> > 2. 事件循环是可以嵌套的，一层套一层，子层的事件循环执行exec()的时候，父层事件循环就处于中断状态；当子层事件循环跳出exec()后，父层事件循环才能继续循环下去。另外，子层事件循环具有父层事件循环的几乎所有功能。Qt会把事件送到当前生效的那个事件循环队列中去，其中包括Gui的各种事件。所以用户在主线程中执行各种exec()（如QMessageBox::exec()，QEventLoop::exec()）的时候，虽然这些exec()打断了main()中的QApplication::exec()，但是Gui界面仍然能够正常响应。   
> >
> > 3. 如果某个子事件循环仍然有效，但其父循环被强制跳出，此时父循环不会立即执行跳出，而是等待子事件循环跳出后，父循环才会跳出。
> >
> > 3. mainloop()方法允许程序循环执行，并进入等待和处理事件。mainloop()方法的作用是监控每个组件，当组件发生变化或触发事件时，会立即更新窗口。
>
> 
>
> 顶级(top-level)窗口：通常用于管理最重要的数据，控制并呈现给用户，是一个不带有WM_CHILD属性的窗口。
>
> > top-level窗口和子窗口不同，一个top-level窗口可以被显示在屏幕的任何位置，而子窗口一般只能显示在它的父窗口的客户区。
> >
> > 一个top-level窗口可以被或者不被拥有，但是它永远也不可能是一个子窗口。我们可以说一个窗口有一个拥有者，但是它没有一个父窗口。
> >
> > top-level窗口可以是一个重叠(Overlapped)窗口(带有WS_OVERLAPPED属性，通常作为应用程序主窗口), 也可以是一个弹出式窗口(带有WM_POPUP属性，通常用于各类弹出消息框)。

![](Pictures\界面坐标.png)



##		wxPython

1. 创建wx.App的子类

   1. 定义这个子类
   2. 在定义的子类中写一个OnInit()初始化方法
   3. 在程序的主要部分创建这个类的一个实例
   4. 调用应用程序实例的MainLoop()方法，这个方法将程序的控制权转交给wxPython

   ```python
   import wx
   
   
   class App(wx.App):
       # 初始化方法
       def OnInit(self):
           frame = wx.Frame(parent=None, title='Heelo wxpython')  # 创建窗口
           frame.Show()  # 显示窗口
           return True  # 这一条返回无论写 return false 还是不写，都会报错 OnInit returned false, exiting...。 而当不写返回语句时，还会有TypeError ：方法限定的返回值为 bool 类型，返回了 None 。
       def OnExit(self):
           print("程序结束")
           return 0	# 重写了在 App 类关闭时调用的方法 OnExit （注：这条在实际开发中一般不加，这里加上仅是为了体现 print("程序结束") ）；return 0 这里似乎返回一个 int 即可，返回其他的数也没有标注或报错。
   
   
   if __name__ == '__main__':
       app = App()  # 创建App类的实例
       app.MainLoop()  # 调用App类的MainLoop()主循环方法
   ```

   >`__init__()`方法在实例化一个对象的时候被自动调用，无需人工调用。__
   >
   >而`__OnInit__()`方法则是在应用程序开始时到主事件循环开始前被自动调用，是wxpython所特有的一个方法。`__OnInit__()`要至少一个参数和返回一个True的布尔值，只有当有至少一个参数并且返回一个True布尔值时才能正确执行程序.

   直接使用wx.App：如果在系统中只有一个窗口可以不创建wx.App子类，可以直接使用wx.App，这个类提供了一个最基本的OnInit()初始化方法。

2. 容器

   1. Frame(框架)

      > 在GUI中框架通常也称为窗口。框架是一个容器，通常包含标题栏、菜单等，用户可以将它在屏幕上任意移动，并可以对它进行缩放。
      >
      > **属于容器，不可作为组件添加至其他容器中**

      在wxPython中，wx.Frame是所有框架的父类。创建wx.Frame的子类时，子类应该调用其父类的构造器wx.Frame.\__init__()。

      ```python
      wx.Frame(parent=None, id=None, title=None, pos=None, size=None, style=None, name=None)
      ```

      >parent：框架的父窗口。如果是顶级窗口，这个值是None。
      >
      >id：关于新窗口的wxPython ID号。通常设为-1，此举可使wxPython自动生成一个新的ID。
      >
      >title：窗口的标题。
      >
      >pos：一个wx.Point对象，它指定这个新窗口的**左上角**在屏幕中的位置，在GUI中，，通常(0,0)是显示器的左上角，该对象的默认值(-1,-1)将让系统决定窗口的位置。
      >
      >size：一个wx.Size对象，它指定这个窗口的初始尺寸。该对象的默认值(-1,-1)将让系统决定窗口的初始尺寸。
      >
      >style：指定窗口的类型的常量。可以使用或运算来组合它们。
      >
      >name：框架内在的名字。可以使用它来寻找这个窗口。

      ```python
      import wx
      
      
      class MyFrame(wx.Frame):
          def __init__(self, parent, id):
              wx.Frame.__init__(self, parent, id, title='创建Frame', pos=(100, 100), size=(300, 300))
      
      
      if __name__ == '__main__':
          app = wx.App()  # 初始化应用
          frame = MyFrame(parent=None, id=-1)  # 实例MyFrame类并传递参数
          frame.Show()  # 显示窗口
          app.MainLoop()  # 调用MainLoop()主循环方法
          
          
      # 在主程序中调用MyFrame类并且传递2个参数，在MyFrame类中自动执行__init__()初始化方法接收参数，然后调用父类wx.Frame的__init__()初始化方法
      ```

   2.  Panel(面板)

      >**可以作为组件被添加至容器中**，一般来说， wxPython 中控件一般放在内容面板而非直接添加到 Frame 里。

      ```python
      wx.panel(parent=None, id=None, pos=None, size=None, style=None, name=None)
      ```

      > parent：父容器
      >
      > style：Panel 可设置的 style 也是 wx.Windows 的 Style ，所有控件都可以设置，可以参见 [帮助文档](https://docs.wxpython.org/wx.Window.html#styles-window-styles)，当有许多个 style 需要设的时候，可以使用位或运算`|`连接各个 style 。

      ```python
      import wx
      class MyFrame(wx.Frame):  # 该对象继承于wx.Frame框架
      	def __init__(self):
      		super().__init__(parent=None,title="窗口",size=(400,300),pos=(100,100))
      		panel = wx.Panel(parent=self)	# 将父级容器定义为窗口（就是这个当前窗口对象self）
      		wx.StaticText(parent=panel,label='文字1',pos=(20,20))	# 文字标签
      
      class App(wx.App):        # 该对象继承于wx.App框架
      	def OnInit(self):     # 直接实例化该对象并调用此函数，相当于显示，然后直接在main中进入主事件循环
      		frame = MyFrame()	# 执行窗口定义
      		frame.Show()
      		return True
      	def OnExit(self):     # 可以在这里释放一些资源
      		print("应用程序退出")
      		return 0
      
      if __name__ == '__main__':	# 判断是否是主进程
      	app=App()
      	app.MainLoop()         # 在这里调用主事件循环
          
      
      ```

3. 控件

   > 控件是集显示和功能一体的可视部件，即按钮、文本、输入框、单选框等
   >
   > 
   >
   > 图片类
   > 图片（Image），主要关注显示。
   >
   > 按钮类
   > 按钮(Button)，主要关注功能，关键点：按钮显示图片 文本和点击后的响应
   > 单选按钮(CheckBox),主要关注功能，关键点：多组选择仅可选一个
   > 复选按钮（CheckBox），主要关注功能，关键点：多组选择可选多个
   >
   > 文本类
   > 文本标签(Label),主要关注显示，关键点：玩家不可以编辑
   > 编辑文本（Edit）,主要关注功能，关键点：玩家可以输入
   > 富本文(RichLabel),主要关注显示，关键点：文本中可以显示图片
   > 富文本编辑（RichEdit）,主要关注功能，关键点：输入文本可以有图片
   >
   > 容器类
   > 列表框(ListBox),主要关注功能， 关键点：条目
   > 组合框（ComboBox）,主要关注显示，关键点：条目
   > 选项卡(TabView),主要关注功能，关键点：选项
   > 树视图(TreeView),主要关注显示，关键点：条目
   > 窗口（Window），主要关注显示，关键点：布局
   > 对话框(Dialog),主要关注功能，关键点:交互
   > 菜单（Menu），主要关注功能，关键点：条目
   > 工具栏（ToolBar），主要关注功能，关键点:条目
   >
   > 工具类
   > 进度条(ProgressBar),主要关注功能
   > 滚动条（ScrollBar）,主要关注功能

   1. Font字体类

      ```python
      Font(fontInfo)
      Font(pointSize, family, style, weight, underline=False, faceName="", encoding=FONTENCODING_DEFAULT)	# (常用)
      Font()
      Font(font)
      Font(pixelSize, family, style, weight, underline=False, faceName="", encoding=FONTENCODING_DEFAULT)
      Font(nativeInfoString)
      Font(nativeInfo)
      ```

      >pointSize ：文字大小，单位为磅：float
      >family ：字体系列，快速指定一个字体而不需要知道该字体的实际名字：FontFamily
      >style ：文字样式，是否斜体：FontStyle
      >weight ：文字粗细：FontWeight
      >underline ：是否下划线，仅在Windows系统下有效：bool
      >faceName ：字体名：string
      >encoding ：文字编码：FontEncoding
      >
      >>FontFamily
      >
      >>>FONTFAMILY_DEFAULT ：默认字体
      >>>FONTFAMILY_DECORATIVE ： 装饰字体
      >>>FONTFAMILY_ROMAN ：衬线字体
      >>>FONTFAMILY_SCRIPT ：手写体
      >>>FONTFAMILY_SWISS ： 无衬线字体
      >>>FONTFAMILY_MODERN ： 等距字体
      >>>FONTFAMILY_TELETYPE ：打字机字体
      >
      >>FontStyle
      >
      >>> FONTSTYLE_NORMAL：普通，没有倾斜
      >>>
      >>> FONTSTYLE_ITALIC：（意大利）斜体
      >>>
      >>> FONTSTYLE_SLANT：（罗马）斜体
      >
      >>FontWeight
      >
      >>>FONTWEIGHT_THIN ：最细字体
      >>>FONTWEIGHT_EXTRALIGHT ：极细字体
      >>>FONTWEIGHT_LIGHT ：细体
      >>>FONTWEIGHT_NORMAL ：正常字重
      >>>FONTWEIGHT_MEDIUM ：中等字重（比 FONTWEIGHT_NORMAL 稍粗）
      >>>FONTWEIGHT_SEMIBOLD ：稍粗字体
      >>>FONTWEIGHT_BOLD ：粗体
      >>>FONTWEIGHT_EXTRABOLD ：较粗字体
      >>>FONTWEIGHT_HEAVY ：极粗字体
      >>>FONTWEIGHT_EXTRAHEAVY ：最粗字体
      >
      >>FontEncoding
      >
      >>> FONTENCODING_SYSTEM ：系统默认编码
      >>>
      >>> FONTENCODING_DEFAULT ：应用默认编码
      >
   
   2. StaticText文本类
   
      ```python
      wx.StaticText(parent, id=None, label=None, pos=None, size=None, style=0, name=None)
      ```
   
      >parent：父窗口部件
      >
      >id：标识符，使用-1可以自动创建一个唯一的标识
      >
      >label：显示在静态控件中的文本内容
      >
      >pos：一个wx.Point对象或一个Python元组，它指定这个窗口部件的位置
      >
      >size：一个wx.Size对象或一个Python元组，他指定这个窗口部件的尺寸
      >
      >style：样式标记
      >
      >name：对象的名字
   
      ```python
      from wx import *
      
      
      class MyFrame(Frame):
      
          def __init__(self):
              super(MyFrame, self).__init__(None, title="第一个wxPython程序", size=(600, 400), pos=(300, 225))
      
              self.panel = Panel(self)
      
              self.inPanelA = Panel(self.panel, style=BORDER_SIMPLE, pos=(0, 0))
              self.textA = StaticText(self.inPanelA, label="A")
      
              self.inPanelB = Panel(self.panel, style=BORDER_SUNKEN, pos=(50, 0))
              self.textB = StaticText(self.inPanelB, label="B")
      
              self.inPanelC = Panel(self.panel, style=BORDER_RAISED, pos=(100, 0))
              self.textC = StaticText(self.inPanelC, label="C")
      
              self.inPanelD = Panel(self.panel, style=BORDER_STATIC, pos=(150, 0))
              self.textD = StaticText(self.inPanelD, label="D")
      
              self.inPanelE = Panel(self.panel, style=BORDER_THEME, pos=(200, 0))
              self.textE = StaticText(self.inPanelE, label="E")
      
              self.inPanelF = Panel(self.panel, style=BORDER_NONE, pos=(250, 0))
              self.textF = StaticText(self.inPanelF, label="F")
      
      
      class MyApp(App):
      
          def OnInit(self):
              frame = MyFrame()
              frame.Show()
      
              return True
      
      
      if __name__ == "__main__":
          app = MyApp()
      
          app.MainLoop()
      ```
   
   3. TextCtrl输入文本类
   
      ```python
      wx.TextCtrl(parent=None, id=None, value=None, pos=None, size=None, style=0, validator=None, name=None)
      ```
   
      > style：文本样式
      >
      > > 单行文本样式：
      > >
      > > >wx.TE_CENTER：控件中的文本居中
      > > >
      > > >wx.TE_LEFT：控件中的文本左对齐。默认
      > > >
      > > >wx.TE_RIGHT：控件中的文本右对齐。
      > > >
      > > >wx.TE_NOHIDESEL：文本始终高亮显示，只适用于Windows。
      > > >
      > > >wx.TE_PASSWORD：不显示所键入的文本，代替以星号显示。
      > > >
      > > >wx.TE_PROCESS_ENTER：如果使用了这个样式，那么当用户在控件内按下回车 键时，一个文本输入事件被触发。
      > > >
      > > >wx.TE_PROCESS_TAB：如果指定了这个样式，那么通常的字符事件在Tab键按下 时创建（一般意味一个制表符将被插入文本）。否则，tab由对话框来管理，通常是 控件间的切换。
      > > >
      > > >wx.TE_READONLY：文本控件为只读，用户不能修改其中的文本。
      > >
      > > 多行文本样式：
      > >
      > > > wx.TE_LINEWRAP：对于太长的行，以字符为界换行。某些操作系统可能会忽略该样式
      > > >
      > > > wx.TE_MULTILINE：文本控件将显示多行
      > > >
      > > > wx.TE_WORDWRAP：对于太长的行，以单词为界换行。许多操作系统会忽略该样式。
      >
      > value：显示在该控件中的初始文本
      >
      > validator：常用于过滤数据以确保只能键入要接受的数据
   
   4. Button按钮类
   
      > 按钮是GUI界面中应用最为广泛的控件，它常用于捕获用户生成的单击事件，其最明显的用途是触发绑定到一个处理函数
   
      ```python
      wx.Button(parent=None, id=None, label=None, pos=None, size=None, style=0, validator=None, name=None)
      ```
   
      > style
      >
      > >- `wx.BU_LEFT`: 左对齐标签。仅限 Windows 和 GTK+。
      > >- `wx.BU_TOP`：将标签与按钮顶部对齐。仅限 Windows 和 GTK+。
      > >- `wx.BU_RIGHT`: 右对齐位图标签。仅限 Windows 和 GTK+。
      > >- `wx.BU_BOTTOM`：将标签与按钮底部对齐。仅限 Windows 和 GTK+。
      > >- `wx.BU_EXACTFIT`：默认情况下，所有按钮都至少由标准按钮大小组成，即使它们的内容小到可以放入较小的大小。这样做是为了保持一致性，因为大多数平台在本机对话框中使用相同大小的按钮，但可以通过指定此标志来覆盖。如果给定了，则按钮将变得足够大以容纳其内容。请注意，在 MSW 下，如果按钮具有非空标签，即使使用此样式，按钮仍将至少具有标准高度。
      > >- `wx.BU_NOTEXT`：禁用按钮中文本标签的显示，即使它有一个或它的 id 是具有关联标签的标准股票 id 之一：不使用这种样式的按钮应该只显示位图但使用标准 id也会显示一个标签。
      > >- `wx.BORDER_NONE`: 创建一个没有边框的按钮。这目前在 MSW、GTK2 和 OSX/Cocoa 中实现。
   
4. BoxSizer布局

   > sizer(尺寸器)是用于自动布局一组窗口控件的算法。sizer被附加到一个容器，通常是一个框架或面板，在父容器中创建的子窗口控件必须被分别添加到sizer，当sizer被附加到容器后，它就可以管理它所包含的子布局。

   | sizer名称      | 描述                                                         |
   | -------------- | ------------------------------------------------------------ |
   | BoxSizer       | 在一条水平或垂直线上的窗口部件的布局。当尺寸改变时，控制窗口部件的行为上很灵活，通常用于嵌套的样式，可用于几乎任何类型的布局。 |
   | StaticBoxSizer | 一个标准的BoxSizer，带有标题和环线                           |
   | GridSizer      | 一个十分基础的网格布局，放置的窗口部件都是同样尺寸且整齐布局时可以使用。容器划分成表格，单元格和单元格之间的长和高完全一致，也就是说改变其中一个单元格的长度，所有单独格的长度都要改；进来的元素挨着填进单元格 |
   | FlexGridSizer  | 与GridSizer类似，但可以改变网格尺寸，即表格每一列的长度、每一行的高度都可以单独定义 |
   | GridBagSizer   | GridSizer系列中最灵活的成员，支持合并单元格，使得网格中的窗口部件可以随意放置 |

   一个BoxSizer是是个垂直列或水平行，窗口部件在其中从左至右或从上到下布置在一条线上，每个sizer都是一个独立的实体，相互之间嵌套sizer的能力可以在每行每列放置不同数量的项目。

   尺寸器会管理组件的尺寸，只要将部件添加到尺寸器上，在添加一些布局参数，就可以让尺寸器自行管理父组件的尺寸。

   ```python
   wx.BoxSizer(orient)
   ```

   > orient：BoxSizer的方向，参数可为wx.HORIZONTAL(水平)和wx.VERTICAL(垂直)，默认为水平

   使用Add()方法可将控件加入sizer

   ```python
   Box.Add(control,proportion,flag,border)
   ```

   > control：要添加的控件
   >
   > proportion：所添加控件在定义的定位方式所代表方向上占据的空间比例。
   >
   > flag：flag参数与border参数结合使用可以指定边距宽度，即控件之间的边界，可以使用"**|**"来联合使用这些标志，还可以与proportion参数结合以指定空间本身的对齐(排列)方式
   >
   > >wx.LEFT：左边距
   > >
   > >wx.RIGHT：右边距
   > >
   > >wx.BOTTOM：底边距
   > >
   > >wx.TOP：上边距
   > >
   > >wx.ALL：上下左右4个边距
   > >
   > >
   > >
   > >wx.ALIGN_LEFT：左边对齐
   > >
   > >wx.ALIGN_RIGHT：右边对齐
   > >
   > >wx.ALIGN_TOP：顶部对齐
   > >
   > >wx.ALIGN_BOTTOM：底边对齐
   > >
   > >wx.ALIGN_CENTER_VERTICAL：垂直对齐
   > >
   > >wx.ALIGN_CENTER_HORIZONTAL：水平对齐
   > >
   > >wx.ALIGN_CENTER：居中对齐
   > >
   > >wx.EXPAND：所添加控件将占有sizer定位方向上所有的控件
   > >
   > >> **wx.LEFT是指控件边框左边是否留空，该常量的定义在_core.py源文件中**
   > >>
   > >> **wx.ALIGN_LEFT是控件本身居左对齐，该常量定义也在_core.py源文件中**
   > >>
   > >> **wx.TE_LEFT是控件光标居左对齐，该常量定义在_controls.py源文件中**
   >
   > boder：控制所添加控件的边距，就是在部件之间添加一些像素的空白
   
5. 事件(Event)处理

   ```python
   Bind(event, handler, source=None, id=-1, id2=-1)
   ```

   > event：事件类型
   >
   > handler：方法名，事件发生时执行该方法
   >
   > source：默认为None，表示当前的Frame，也可以将此事件绑定在特定的wxpython的窗口部件中



##	PyQt5

> PyQt是Qt框架的Python语言实现，由Riverbank Computing开发，是最强大的GUI库之一。PyQt提供了一个设计良好的窗口控件集合，每一个PyQt控件都对应一个Qt控件，因此PyQt的API接口与Qt的API接口很接近，但PyQt不再使用QMake系统和Q_OBJECT宏。
> PyQt5提供GPL版和商业版证书，自由开发者可以使用免费的GPL许可，如果需要将PyQt用于商业应用，则必须购买商业许可。
>
> PyQt5特性如下：
> （1）基于高性能的Qt的GUI控件集。
> （2）能够跨平台运行在Linux、Window和Mac OS系统上。
> （3）使用信号槽机制进行通信。
> （4）对Qt库进行完全封装。
> （5）可以使用成熟的IDE进行界面设计，并自动生成可执行的Python代码。
> （6）提供一整套种类齐全的窗口控件。
>
> - **QtCore模块**涵盖了包的核心的非GUI功能，此模块被用于处理程序中涉及到的 time、文件、目录、数据类型、文本流、链接、mime、线程或进程等对象。
> - **QtGui模块**涵盖多种基本图形功能的类; 包括但不限于：窗口集、事件处理、2D图形、基本的图像和界面 和字体文本。
> - **QtWidgets模块**包含了一整套UI元素组件，用于建立符合系统风格的classic界面，非常方便，可以在安装时选择是否使用此功能。
> - **QtMultimedia模块**包含了一套类库，该类库被用于处理多媒体事件，通过调用API接口访问摄像头、语音设备、收发消息（radio functionality）等。
> - **QtBluetooth模块**包含了处理蓝牙活动的类库，它的功能包括：扫描设备、连接、交互等行为。
> - **QtNetwork模块**包含用于网络编程的类库，这组类程序通过提供便捷的TCP/IP 及 UDP 的 c/s 程式码集合，使得基于Qt的网络编程更容易。
> - **QtPositioning模块**用于获取位置信息，此模块允许使用多种方式达成定位，包括但不限于：卫星、无线网、文字信息。此应用一般用于网络地图定位系统。
> - **Enginio模块**用于构建客户端的应用程式库，用于在运行时访问 Qt Cloud 服务器托管的应用程序。
> - **QtWebSockets模块**包含了一组类程序，用以实现websocket协议。
> - **QtWebKit**包含了用于实现基于webkit2的网络浏览器的类库。
> - **QtWebKitWidgets模块**包含用于基于WebKit1的Web浏览器实现的类，用于基于QtWidgets的应用程序
> - **QtXml模块**包含了用于处理XML的类库，此模块为SAX和DOM API 的实现提供了方法。
> - **QtSvg模块**通过一组类，为显示矢量图形文件的内容提供了方法。
> - **QtSql模块**提供了数据库对象的接口以供使用
> - **QtTest模块**包含了可以通过单元测试，以调试PyQt5应用程式的功能。

1. 要在界面上 创建一个控件 ，就需要在程序代码中 创建 这个 控件对应类 的一个 实例对象。

   在 Qt 系统中，控件（widget）是 层层嵌套 的，除了最顶层的控件，其他的控件都有父控件。

2. 界面动作处理 (signal 和 slot)

   1. 在 Qt 系统中， 当界面上一个控件被操作时，比如 被点击、被输入文本、被鼠标拖拽等， 就会发出 信号 ，英文叫 signal 。就是表明一个事件（比如被点击、被输入文本）发生了。
   2. 我们可以预先在代码中指定 处理这个 signal 的函数，这个处理 signal 的函数 叫做 slot (槽函数)

3. 如果要设计稍微复杂一些的程序，就会出现太多的控件对应的变量名，而且这样也不利于 代码的模块化，所以，我们通常应该把 一个窗口和其包含的控件，对应的代码全部封装到类中

4. 对于Qt Designer生成的ui文件，可进行动态加载或pyuic转换为Python代码

   1. 动态加载ui文件

      ```python
      from PyQt5 import uic
      self.ui = uic.loadUi("main.ui")
      ```

   2. 转化UI文件为Python代码

      ```
      python -m PyQt5.uic.pyuic FileName -o FileName.py
      ```

5. `QApplication` 提供了整个图形界面程序的底层管理功能，比如：初始化、程序入口参数的处理，用户事件（对界面的点击、输入、拖拽）分发给各个对应的控件，等等…

   所以，我们必须在任何界面控件对象创建前，先创建它

6. 

#	Pygame

> Pygame是跨平台的Python模块，专为电子游戏设计(包含图像、声音)，创建在SDL(Simple DirectMedia Layer)开发库的基础上，允许实时电子游戏研发而不被低级语言束缚。基于这个设想，所有需要的游戏功能和理念(主要是图像方面)都完全简化为游戏逻辑本身，所有的资源结构都可以由高级语言提供。

1. display模块

   常用方法：

   | 方法名                     | 功能                                                   |
   | -------------------------- | ------------------------------------------------------ |
   | pygame.display.init        | 初始化display模块                                      |
   | pygame.display.quit        | 结束display模块                                        |
   | pygame.display.get_init    | 如果display模块已经被初始化则返回True                  |
   | pygame.display.set_mode    | 初始化一个准备显示的界面，返回一个Surface对象          |
   | pygame.display.get_surface | 获取当前的Surface对象                                  |
   | pygame.display.flip        | 更新整个待显示的Surface对象到屏幕上                    |
   | pygame.display.update      | 更新部分内容显示到屏幕上，如果没有参数则与flip功能相同 |

2. Surface对象

   >Surface是用来代表图片的pygame对象，可以对一个Surface对象进行涂画、变形、复制等各种操作。事实上，屏幕也是一个surface，pygame.display.set_mode()就返回了一个屏幕Surface对象。

   常用方法：

   | 方法名                       | 功能                                    |
   | ---------------------------- | --------------------------------------- |
   | pygame.Surface.blit          | 将一个图像画到另一个图像上              |
   | pygame.Surface.convert       | 转换图像的像素格式                      |
   | pygame.Surface.convert_alpha | 转换图像的像素格式，包含alpha通道的转换 |
   | pygame.Surface.fill          | 使用颜色填充Surface                     |
   | pygame.Surface.get_rect      | 获取Surface的矩形区域，返回一个Rect对象 |

3. 实例1(小球碰撞)

   ```python
   # -*- coding: UTF-8 -*- 
   # 创建者：LeK
   # 创建日期：2022/7/24
   
   import sys
   import pygame
   
   pygame.init()  # 初始化pygame
   size = width, height = 640, 480  # 设置窗口
   screen = pygame.display.set_mode(size)  # 显示窗口，返回一个Surface对象
   color = (0, 0, 0)  # 设置颜色
   
   ball = pygame.image.load(r'ball.png')  # 加载图片，返回一个Surface对象
   ballrect = ball.get_rect()  # 获取矩形区域，返回一个Rect对象
   
   speed = [5, 5]  # 设置移动的X轴、Y轴距离
   clock = pygame.time.Clock()
   
   while True:
       clock.tick(60)  # 每秒执行60次
       for event in pygame.event.get():
           if event.type == pygame.QUIT:  # 获取点击pygame窗口退出事件
               sys.exit()
   
       ballrect = ballrect.move(speed)  # 移动小球
       # 碰撞检测
       if ballrect.left < 0 or ballrect.right > width:
           speed[0] = -speed[0]  # x轴上碰到边界，将运动方向转为相反方向
       if ballrect.top < 0 or ballrect.bottom > height:
           speed[1] = -speed[1]  # y轴上碰到边界，将运动方向转为相反方向
   
       screen.fill(color)  # 填充颜色
       screen.blit(ball, ballrect)  # 将图片划到窗口上
       pygame.display.flip()  # 更新全部显示
   
   pygame.quit()  # 退出pygame
   
   ```

4. 实例2(Flappy Bird)

   ```python
   # -*- coding: UTF-8 -*- 
   # 创建者：LeK
   # 创建日期：2022/7/25
   
   import sys
   import pygame
   import random
   
   
   class Bird(object):
       def __init__(self):
           self.birdrect = pygame.Rect(124, 50, 48, 48)  # 创建鸟的矩形
           self.birdstatus = [pygame.image.load(r'flappybird\bird0_0.png'),
                              pygame.image.load(r'flappybird\bird0_1.png'),
                              pygame.image.load(r'flappybird\bird0_2.png'),
                              pygame.image.load(r'flappybird/medals_0.png')]  # 鸟不同状态读取的图片
           self.status = 1  # 鸟的状态，默认为0
           self.birdY = 236  # 鸟的Y坐标
           self.jump = False  # 鸟是否跳跃，默认为降落
           self.jumpspeed = 10  # 初始化鸟跳跃的高度
           self.gravity = 5  # 初始化重力
           self.dead = False  # 鸟的生命状态，默认为活着
   
       def birdupdate(self):  # 鸟的位置
           if self.jump and self.jumpspeed >= 0:
               self.jumpspeed -= 1  # 设置鸟向上的速度，速度为递减的等差数列
               self.birdY -= self.jumpspeed  # 设置鸟的Y轴坐标，总移动距离为等差数列和
           else:
               self.gravity += 0.2  # 设置鸟向下的速度，速度为递增的等差数列
               self.birdY += self.gravity  # 设置鸟的Y轴坐标，总移动距离为等差数列和
               self.jump = False
   
           self.birdrect[1] = self.birdY  # 设置鸟的矩形Y轴坐标
   
   
   class Pipeline(object):
       def __init__(self):
           self.wallx = 300  # 设置管道起始位置
           self.basis = random.randint(-320, 0)
           self.upwally = self.basis
           self.distance = random.randint(150, 192)
           self.downwally = self.upwally + 320 + self.distance
           self.pineup = pygame.image.load(r'flappybird\pipe_down.png')
           self.pinedown = pygame.image.load(r'flappybird\pipe_up.png')
           self.uprect = pygame.Rect(self.wallx, self.upwally,
                                     self.pineup.get_width() - 10,
                                     self.pinedown.get_height())  # 设置上管道矩形
           self.downrect = pygame.Rect(self.wallx, self.downwally,
                                       self.pinedown.get_width() - 10,
                                       self.pinedown.get_height())  # 设置下管道矩形
   
       def updatePipeline(self):
           global score
           self.wallx -= 5  # 将管道X坐标向左移动
           self.upwally = self.basis
           self.downwally = self.upwally + 320 + self.distance
           self.uprect = pygame.Rect(self.wallx, self.upwally,
                                     self.pineup.get_width() - 10,
                                     self.pinedown.get_height())
           self.downrect = pygame.Rect(self.wallx, self.downwally,
                                       self.pinedown.get_width() - 10,
                                       self.pinedown.get_height())
           if self.wallx < -80:
               self.wallx = 300  # 重置管道X坐标
               self.basis = random.randint(-320, 0)
               self.distance = random.randint(150, 192)
           if self.wallx == -80:
               score += 1  # 设置得分点
   
   
   def CreateMap(color, background):  # 绘制整体图像
       screen.fill(color)  # 屏幕填充颜色
       screen.blit(background, (0, 0))  # 屏幕填充背景图片
   
       if Bird.dead:  # 鸟死亡的状态
           Bird.status = 3
       elif Bird.jump:  # 鸟跳跃的状态
           Bird.status = 2
       else:
           Bird.status = 0  # 鸟降落的状态
       screen.blit(Bird.birdstatus[Bird.status], (124, Bird.birdY))  # 在鸟的位置放置鸟的图像
       Bird.birdupdate()  # 更新下一次屏幕刷新时鸟的位置
   
       screen.blit(Pipeline.pineup, (Pipeline.wallx, Pipeline.upwally))  # 在管道的位置放置管道的图像
       screen.blit(Pipeline.pinedown, (Pipeline.wallx, Pipeline.downwally))
       Pipeline.updatePipeline()  # 更新下一次刷新屏幕时管道的位置
   
       pygame.display.update()  # 更新显示
   
   
   def checkdead():
       # 判断鸟与管道的碰撞
       if Pipeline.uprect.colliderect(Bird.birdrect) or Pipeline.downrect.colliderect(Bird.birdrect):
           Bird.dead = True
       # 判断鸟与屏幕的碰撞
       if 0 < Bird.birdrect[1] < height:  # 判断鸟的矩形是否在屏幕内
           return False
       else:
           Bird.dead = True
           return True
   
   
   def getresult():
       final_text1 = 'GAME OVER'
       final_text2 = 'YOUR FINAL SCORE IS:  ' + str(score)
       ft1_font = pygame.font.SysFont('Arial', 30)  # 设置字体
       ft1_surf = ft1_font.render(final_text1, 1, (242, 3, 36))  # 设置颜色
       ft2_font = pygame.font.SysFont('Arial', 20)
       ft2_surf = ft2_font.render(final_text2, 1, (253, 177, 6))
   
       screen.blit(ft1_surf, [screen.get_width() / 2 - ft1_surf.get_width() / 2, 100])
       screen.blit(ft2_surf, [screen.get_width() / 2 - ft2_surf.get_width() / 2, 200])
   
       pygame.display.flip()
   
   
   if __name__ == '__main__':
       pygame.init()
   
       size = width, height = 288, 512
       screen = pygame.display.set_mode(size)  # 设置屏幕尺寸
       clock = pygame.time.Clock()
       Bird = Bird()
       Pipeline = Pipeline()
       score = 0
   
       color = (255, 255, 255)
       background = pygame.image.load(r'flappybird\bg_day.png')
   
       while True:
           clock.tick(60)  # 设置每秒循环的次数
           for event in pygame.event.get():
               if event.type == pygame.QUIT:
                   sys.exit()
               if (event.type == pygame.KEYDOWN or event.type == pygame.MOUSEBUTTONDOWN) and not Bird.dead:
                   # 设置鸟的状态为跳跃，重置向上跳跃的高度和重力的初值
                   Bird.jump = True
                   Bird.gravity = 5  # 重置重力
                   Bird.jumpspeed = 10  # 重置跳跃高度
           if checkdead():  # 满足与屏幕边缘或管道碰撞且鸟的矩形与屏幕边缘碰撞
               getresult()  # 显示得分界面且在该画面一直停留
           else:
               CreateMap(color, background)  # display画面，传入背景颜色和背景图片
   
       pygame.quit()
   ```
   



#	爬虫

> 网络爬虫（又称为网页蜘蛛，网络机器人，在FOAF社区中间，更经常的称为网页追逐者），是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。另外一些不常使用的名字还有蚂蚁、自动索引、模拟程序或者蠕虫。网络爬虫按照系统结构和实现技术，大致可以分为以下几种类型：通用网络爬虫（General Purpose Web Crawler）、聚焦网络爬虫（Focused Web Crawler）、增量式网络爬虫（Incremental Web Crawler）、深层网络爬虫（Deep Web Crawler）。 实际的网络爬虫系统通常是几种爬虫技术相结合实现的。

| **get**    | **发送一个请求常用来获取服务器资源**                         |
| ---------- | ------------------------------------------------------------ |
| **post**   | **向URL指定的资源提交数据或附加新的数据**                    |
| **put**    | **跟POST方法很像，也是像服务器提交数据进行处理请求。但是，它们之间有不同。PUT指定了资源在服务器上的位置，而POST没有。一般用于修改资源** |
| **delete** | **请求服务器删除指定的资源**                                 |

1. Python的网络请求

   1. urllib模块

      | 子模块             | 描述                                                         |
      | ------------------ | ------------------------------------------------------------ |
      | urllib.request     | 该模块定义了打开URL(主要是HTTP)的方法和类，例如身份验证、重定向、cookie等 |
      | urllib.error       | 该模块中主要包含异常类，基本的异常类是URLError               |
      | urllib.parse       | 该模块定义的功能分为两大类：URL解析和URL引用                 |
      | urllib.robotparser | 该模块用于解析robots.txt文件                                 |

      1. 通过get请求方式获取网页内容

         ```python
         import urllib.request
         
         respone = urllib.request.urlopen('http://www.baidu.com')	# 打开指定需要爬取的网页
         html = response.read()	# 读取页面代码
         print(html)
         ```

      2. 通过post请求方式获取网页内容

         ```python
         import urllib.parse
         import urllib.request
         
         # 将数据使用urlencode编码处理后，再使用encoding设置为utf-8编码
         data = bytes(urllib.parse.urlencode({'word': 'hello'}), encoding='utf8')
         # 打开指定需要爬取的网页
         response = urllib.request.urlopen('http://httpbin.org/post', data=data)
         html = response.read()
         print(html)
         ```

   2. Urllib3模块

      > Urllib3是一个功能强大，条理清晰，用于HTTP客户端的Python库，许多Python的原生系统已经开始使用Urllib3，Urllib3提供了许多Python标准库里所没有的重要特性：
      >
      > 1. 线程安全
      > 2.  连接池
      > 3. 客户端SSL/TLS验证
      > 4. 文件分部编码上传
      > 5.  协助处理重复请求和HTTP重定位
      > 6. 支持压缩编码
      > 7. 支持HTTP和SOCKS代理
      > 8. 100%测试覆盖率

      ```python
      import urllib3
      
      # 创建PoolManager对象，用于处理与线程池的连接以及线程安全的所有细节
      http = urllib3.PoolManager()
      # 对需要爬取的网页发送请求
      response = http.request('GET', 'https://www.baidu.com/')
      print(response.data)
      
      post请求实现：
      response=http.request('POST','http://httpbin.org/post',firlds={'word':'hello'})
      ```

   3. requests模块

      > requests是Python中实现HTTP请求的一种方式，requests是第三方模块，该模块在实现HTTP请求时要比urllib模块简化很多，操作更加人性化。
      
      | 属性或方法            | 说明                                                         |
      | :-------------------- | :----------------------------------------------------------- |
      | apparent_encoding     | 编码方式                                                     |
      | close()               | 关闭与服务器的连接                                           |
      | content               | 返回响应的内容，以字节为单位                                 |
      | cookies               | 返回一个 CookieJar 对象，包含了从服务器发回的 cookie         |
      | elapsed               | 返回一个 timedelta 对象，包含了从发送请求到响应到达之间经过的时间量，可以用于测试响应速度。比如 r.elapsed.microseconds 表示响应到达需要多少微秒。 |
      | encoding              | 解码 r.text 的编码方式                                       |
      | headers               | 返回响应头，字典格式                                         |
      | history               | 返回包含请求历史的响应对象列表（url）                        |
      | is_permanent_redirect | 如果响应是永久重定向的 url，则返回 True，否则返回 False      |
      | is_redirect           | 如果响应被重定向，则返回 True，否则返回 False                |
      | iter_content()        | 迭代响应                                                     |
      | iter_lines()          | 迭代响应的行                                                 |
      | json()                | 返回结果的 JSON 对象 (结果需要以 JSON 格式编写的，否则会引发错误) |
      | links                 | 返回响应的解析头链接                                         |
      | next                  | 返回重定向链中下一个请求的 PreparedRequest 对象              |
      | ok                    | 检查 "status_code" 的值，如果小于400，则返回 True，如果不小于 400，则返回 False |
      | raise_for_status()    | 如果发生错误，方法返回一个 HTTPError 对象                    |
      | reason                | 响应状态的描述，比如 "Not Found" 或 "OK"                     |
      | request               | 返回请求此响应的请求对象                                     |
      | status_code           | 返回 http 的状态码，比如 404 和 200（200 是 OK，404 是 Not Found） |
      | text                  | 返回响应的内容，unicode 类型数据                             |
      | url                   | 返回响应的 URL                                               |
      
      ```python
      import requests
      
      response = requests.get('http://www.baidu.com')
      print(response.status_code)  # 打印状态码
      print(response.url)  # 打印请求URL
      print(response.headers)  # 打印头部信息
      print(response.cookies)  # 打印cookie信息
      print(response.text)  # 以文本形式打印网页源码
      print(response.content)  # 以字节流形式打印网页源码
      
      
      post请求方式：
      data = {'word': 'hello'}  # 表单参数
      # 对需要爬取的网页发送请求
      response = requests.post('http://httpbin.org/post', data=data)
      print(response.content)  # 以字节流形式打印网页源码
      
      其余请求方式：
      requests.put('http://httpbin.org/put', data={'key': 'value'})
      requests.delete('http://httpbin.org/delete')
      requests.head('http://httpbin.org/get')
      requests.options('http://httpbin.org/get')
      ```
      
      > 如果发现请求的URL地址中参数是跟在"?"后面的，例如"httpbin.org/get?key=val"，requests模块提供了传递参数的方法，允许使用params关键字参数，以一个字符串字典来提供这些参数。
      >
      > ```python
      > payload = {'key1': 'value1', 'key2': 'value2'}
      > response = requests.get('http://httpbin.org/get', params=payload)
      > ```
   
2. 请求headers处理

   > 有时在请求一个网页内容时会发现无论通过get或是post以及其他请求方式都会出现403错误，这是由于该网页为了防止恶意采集信息而使用了反爬虫设置从而拒绝了用户的访问，此时可以通过模拟浏览器的头部信息来进行访问。
   >
   > 在 HTTP协议中，服务器端的回答(response)内容包括两部分：头信息(header) 和体内容，这里的头信息不是HTML中的部分，同样，体内容也不是< /BODY>。头信息是用户看不见的，里面包含了很多项，包括：服务器信息、日期、内容的长度等。而体内容就是整个HTML，也就是你所能看见的全部东西。
   >
   > 头信息的作用很多，最主要的有下面几个：1、跳转：当浏览器接受到头信息中的 Location: xxxx 后，就会自动跳转到 xxxx 指向的URL地址，这点有点类似用 js 写跳转。但是这个跳转只有浏览器知道，不管体内容里有没有东西，用户都看不到。2、指定网页的内容： 同样一个XML文件，如果头信息中指定：Content-type: application/xml 的话，浏览器会将其按照XML文件格式解析。但是，如果头信息中是：Content-type: text/xml 的话，浏览器就会将其看作存文本解析。（浏览器不是按照扩展名解析文件的）3、附件：不知道大家有没 有注意，有些时候在一些网站下载东西，点下载连接以后，结果浏览器将这个附件当成网页打开了，里面显示的都是乱码，这个问题也和头信息有关。有时候浏览器 根据Content-type 来判断是打开还是保存，这样有时就会判断错误（主要是网站设计者忘记写Content-type）。其实，还有一个可以来指定该内容为附件、需要保存，这 个就是：Content-Disposition: attachment; filename=”xxxxx”

   ```python
   import requests
   
   url = 'https://www.baidu.com/'  # 创建需要爬取网页的地址
   # 创建头部信息
   headers = {
       'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36 '}
   response = requests.get(url, headers=headers)  # 发送网络请求
   print(response.content)  # 以字节流形式打印网页源码
   ```

3. 网络超时

   > 在访问网页时，如果该网页长时间未响应，系统就会判断该网页超时，所以无法打开网页。

   ```python
   url = 'https://www.baidu.com/'  # 创建需要爬取网页的地址
   for i in range(1, 50):
       try:
           response = requests.get(url, timeout=0.5)  # 设置超时为0.5s
           print(response.status_code)
       except Exception as e:
           print('异常' + str(e))
   ```

   > requests模块还提供了其他常见的网络异常类
   >
   > > ReadTimeout：超时异常
   > >
   > > HTTPError：HTTP异常
   > >
   > > RequestException：请求异常

4. 代理服务

   > 如果IP被爬取网站的服务器所屏蔽了，可以使用代理服务，设置代理时需要先找到代理地址，然后设置对应的端口号。

   ```python
   import requests
   
   proxy = {'http': '122.114.31.177:808',
            'https': '122.114.31.177:8080'}  # 设置代理ip与对应的端口号
   # 对需要爬取的网页发送请求
   response = requests.get('http://www.mingrisoft.com/', proxies=proxy)
   print(response.content)
   ```

5. Beautiful Soup

   > Beautiful Soup是一个用于从HTML和XML文件中提取数据的Python库，它提供一些简单的函数用来处理导航、搜索、修改分析树等功能。
   >
   > Beautiful Soup自动将输入文档转化为Unicode编码，输出文档转化为UTF-8编码。
   >
   > Beautiful Soup支持Python标准库中包含的HTML解析器，也支持许多第三方Python解释器

   | 解析器           | 使用方法                                                     | 优势                                                      | 劣势                                                     |
   | ---------------- | ------------------------------------------------------------ | --------------------------------------------------------- | -------------------------------------------------------- |
   | Python标准库     | BeautifulSoup(markup, “html.parser”)                         | Python的内置标准库、执行速度适中、文档容错能力强          | （Python 2.7.3及Python 3.2.2之前的版本文档中）容错能力差 |
   | lxml的HTML解析器 | BeautifulSoup(markup, “lxml”)                                | 速度快、文档容错能力强                                    | 需要安装C语言库                                          |
   | lxml的XML解析器  | BeautifulSoup(markup, “lxml-xml”)   BeautifulSoup(markup, “xml”) | 速度快、唯一支持XML的解析器                               | 需要安装C语言库                                          |
   | html5lib         | BeautifulSoup(markup, “html5lib”)                            | 最好的容错性、以浏览器的方式解析文档、生成HTML5格式的文档 | 速度慢、不依赖外部扩展                                   |

   

   ```python
   # -*- coding: UTF-8 -*- 
   # 创建者：LeK
   # 创建日期：2022/7/27
   
   
   import requests
   from bs4 import BeautifulSoup
   
   # 创建模拟HTML代码的字符串
   html_doc = '''
   <!DOCTYPE html>
   <html lang="zh-CN">
   
   <head>
       <meta charset="UTF-8">
       <meta http-equiv="X-UA-Compatible" content="IE=edge">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>LJJ's Website</s></title>
       <style>
           body{
               height: 100vh;
               background-color: azure;
           }
         
           p {
               color: blue;
           }
   
           #one {
               color: aquamarine
           }
   
           .mystyle {
               color: rgb(138, 43, 226);
               font-size: xx-large;
           }
   
       </style>
   </head>
   
   <body>
       <div>hello world!</div>
       <p>HELLO HEY！</p>
       <h1 id="one">我是嫩蝶</h1>
       <h2 class="mystyle"">别emo摆烂了，来跟我一起学习</h2>
       <h3 class=" mystyle">每天学一点，跟我一起进步吧！如果遇到不会的善用搜索引擎，详情请看→<a id=one href=" http://www.baidu.com.cn">搜素引擎</a></h3>
           <h4 class="mystyle">如果实在学不下去了就去看小李的直播吧→<a
                   href=" https://live.bilibili.com/23708853?spm_id_from=333.337.0.0">小李</a></h4>
           <h5>学web可看→<a class="mystyle" href=" https://www.w3school.com.cn/">w3school</a></h5>
           <img src=" https://s1.328888.xyz/2022/07/25/DTtxP.jpg" width="1000" height="800" alt="女孩">
           <img src="https://img1.imgtp.com/2022/07/25/pTjuu5Wv.jpg" width="800" height="800" alt="天空">
   </body>
   
   </html>
   '''
   # 创建一个Beautiful Soup对象，获取页面正文
   soup = BeautifulSoup(html_doc, features='lxml')
   print(soup)
   
   # 打开需要解析的html文件
   soup = BeautifulSoup(open('index.html','rb'), 'lxml')
   print(soup.prettify())
   ```

6. 框架

   1. Scrapy

      > Scrapy是一个适用爬取网站数据、提取结构性数据的应用程序框架，它可以应用在广泛领域：Scrapy 常应用在包括数据挖掘，信息处理或存储历史数据等一系列的程序中。通常我们可以很简单的通过 Scrapy 框架实现一个爬虫，抓取指定网站的内容或图片。它也提供了多种类型爬虫的基类，如BaseSpider、sitemap爬虫等，最新版本又提供了web2.0爬虫的支持。
      >
      > 尽管Scrapy原本是设计用来屏幕抓取（更精确的说，是网络抓取），但它也可以用来访问API来提取数据。
      >
      > Scrapy功能很强大，它支持自定义Item和pipeline数据管道；支持在Spider中指定domain（网页域范围），以及相应的Rule（爬取规则）；支持XPath对DOM的解析等。而且Scrapy还有自己的shell，可以在上面方便地调试爬虫项目和查看爬虫运行结果。
      >
      > Scrapy使用了Twisted（其主要对手是Tornado）异步网络框架来处理网络通讯，该网络框架可以加快我们的下载速度，并且包含了各种中间件接口，可以灵活的完成各种需求。
      >
      > 由于Scrapy运行速度快、操作简单、可扩展强，它已成为目前最常用的通用爬虫框架。
      >
      > 
      >
      > - **Scrapy Engine(引擎)**: 负责Spider、ItemPipeline、Downloader、Scheduler中间的**通讯，信号、数据传递**等。
      > - **Scheduler(调度器)**: 它负责**接受引擎发送过来的Request请求，并按照一定的方式进行整理排列，入队**，当引擎需要时，交还给引擎。
      > - **Downloader（下载器）**：负责**下载Scrapy Engine(引擎)发送的所有Requests请求，并将其获取到的Responses交还给Scrapy Engine(引擎)**，由引擎交给Spider来处理，
      > - **Spider（爬虫）**：它负责**处理所有Responses,从中分析提取数据，获取Item字段需要的数据，并将需要跟进的URL提交给引擎**，再次进入Scheduler(调度器).
      > - **Item Pipeline(管道)**：它负责**处理Spider中获取到的Item，并进行进行后期处理**（详细分析、过滤、存储等）的地方。
      > - **Downloader Middlewares（下载中间件）**：你可以当作是一个可以**自定义扩展下载功能**的组件。
      > - **Spider Middlewares（Spider中间件）**：你可以理解为是一个可以**自定扩展和操作引擎和Spider中间通信的功能组件**（比如进入Spider的Responses;和从Spider出去的Requests）
   
      1. 新建项目(scrapy startproject)
   
         在开始爬取之前，必须创建一个新的Scrapy项目。
   
         ```
         scrapy startproject spidername
         ```

         目录结构

         ```
         mySpider/
             scrapy.cfg
             mySpider/
                 __init__.py
                 items.py
                 pipelines.py
                 middlewares.py
                 settings.py
                 spiders/
                     __init__.py
                     ...
         ```

         - 放置 spider 代码的目录文件 spiders（用于编写爬虫）。
         - 项目中的 item 文件 items.py（用于保存所抓取的数据的容器，其存储方式类似于 Python 的字典）。
         - 项目的中间件
         - middlewares.py（提供一种简便的机制，通过允许插入自定义代码来拓展 Scrapy 的功能）。
         - 项目的 pipelines 文件 pipelines.py（核心处理器）。
         - 项目的设置文件 settings.py。
         - 项目的配置文件 scrapy.cfg。
   
      2. Scrapy设置(settings)提供了定制Scrapy组件的方法。可以控制包括核心(core)，插件(extension)，pipeline及spider组件。比如 设置Json Pipeliine、LOG_LEVEL等。
   
         - `BOT_NAME`
   
            - 默认: 'scrapybot'
            - 当您使用 startproject 命令创建项目时其也被自动赋值。
   
         - `CONCURRENT_ITEMS`
   
            - 默认: 100
            - Item Processor(即 Item Pipeline) 同时处理(每个response的)item的最大值。
   
         - `CONCURRENT_REQUESTS`
   
            - 默认: 16
            - Scrapy downloader 并发请求(concurrent requests)的最大值。
   
         - `DEFAULT_REQUEST_HEADERS`
   
            - 默认: 如下
   
               ```1c
                    {
                    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
                    'Accept-Language': 'en',
                    }
               ```
   
         ​             Scrapy HTTP Request使用的默认header。
   
         - `DEPTH_LIMIT`
   
            - 默认: 0
            - 爬取网站最大允许的深度(depth)值。如果为0，则没有限制。
   
         - `DOWNLOAD_DELAY`
   
            - 默认: 0
   
            - 下载器在下载同一个网站下一个页面前需要等待的时间。该选项可以用来限制爬取速度， 减轻服务器压力。同时也支持小数:
   
               `DOWNLOAD_DELAY = 0.25 # 250 ms of delay`
   
            - 默认情况下，Scrapy在两个请求间不等待一个固定的值， 而是使用0.5到1.5之间的一个随机值 `DOWNLOAD_DELAY` 的结果作为等待间隔。
   
         - `DOWNLOAD_TIMEOUT`
   
            - 默认: 180
            - 下载器超时时间(单位: 秒)。
   
         - `ITEM_PIPELINES`
   
            - 默认: {}
            - 保存项目中启用的pipeline及其顺序的字典。该字典默认为空，值(value)任意，不过值(value)习惯设置在0-1000范围内，值越小优先级越高。
   
         ```ebnf
                     ITEM_PIPELINES = {
                     'mySpider.pipelines.SomethingPipeline': 300,
                     'mySpider.pipelines.ItcastJsonPipeline': 800,
                     }
         ```
   
         - `LOG_ENABLED`
   
            - 默认: True
            - 是否启用logging。
   
         - `LOG_ENCODING`
   
            - 默认: 'utf-8'
            - logging使用的编码。
   
         - `LOG_LEVEL`
   
            - 默认: 'DEBUG'
            - log的最低级别。可选的级别有: CRITICAL、 ERROR、WARNING、INFO、DEBUG 。
   
         - `USER_AGENT`
   
            - 默认: "Scrapy/VERSION (+[http://scrapy.org](https://link.segmentfault.com/?enc=ebPMBmbKjhtCA0bX6ZPyyg%3D%3D.we3BSMpAuublWoYP4SV57J%2B5Mq8ONSfNymSla9l59mE%3D))"
            - 爬取的默认User-Agent，除非被覆盖。
   
         - `PROXIES`： 代理设置
   
            - 示例：
   
               ```1c
                  PROXIES = [
                     {'ip_port': '111.11.228.75:80', 'password': ''},
                     {'ip_port': '120.198.243.22:80', 'password': ''},
                     {'ip_port': '111.8.60.9:8123', 'password': ''},
                     {'ip_port': '101.71.27.120:80', 'password': ''},
                     {'ip_port': '122.96.59.104:80', 'password': ''},
                     {'ip_port': '122.224.249.122:8088', 'password':''},
                   ]
               ```
   
         - `COOKIES_ENABLED = False`
   
            - 禁用Cookies
   
      2. 制作爬虫
   
         ```
         scrapy genspider spidername domain
         ```
   
         要建立一个Spider， 你必须用scrapy.Spider类创建一个子类，并确定了三个强制的属性 和 一个方法。
   
         1. name = "" ：这个爬虫的识别名称，必须是唯一的，在不同的爬虫必须定义不同的名字。
         2. allow_domains = [] 是搜索的域名范围，也就是爬虫的约束区域，规定爬虫只爬取这个域名下的网页，不存在的URL会被忽略。
         3. start_urls = () ：爬取的URL元祖/列表。爬虫从这里开始抓取数据，所以，第一次下载的数据将会从这些urls开始。其他子URL将会从这些起始URL中继承性生成。
         4. parse(self, response) ：解析的方法，每个初始URL完成下载后将被调用，调用的时候传入从每一个URL传回的Response对象来作为唯一参数，主要作用：负责解析返回的网页数据(response.body)，提取结构化数据(生成item)，生成需要下一页的URL请求。
   
      3. 运行爬虫
   
         ```python
         from scrapy.cmdline import execute
         import sys
         import os
         
         # os.path.abspath(__file__) 获取当前文件所在的路径
         # os.path.dirname(os.path.abspath(__file__)) 获取当前文件所在的父目录
         
         # 设置执行路径
         sys.path.append(os.path.dirname(os.path.abspath(__file__)))
         
         # 设置执行命令
         execute(["scrapy", "crawl", "cymy_spider"])  # 成语谜语
         ```
   
      5. Scrapy爬虫的数据类型：
   
         1. Request类
            1. Request对象表示一个HTTP请求
            2. 由Spider生成，由Downloader执行
   
         2. Response类
            1. Response对象表示一个HTTP响应
            2. 由Downloader生成，由Spider处理   
   
         3. Item类
            1. Item对象表示一个从HTML页面中提取的信息内容
            2. 由Spider生成，由Item Pipeline处理
            3. Item类似字典类型，可以按照字典类型操作
   
      6. xpath表达式
   
         - `/html/head/title`: 选择HTML文档中 `<head>` 标签内的 `<title>` 元素
         - `/html/head/title/text()`: 选择上面提到的 `<title>` 元素的文字
         - `//td`: 选择所有的 `<td>` 元素
         - `//div[@class="mine"]`: 选择所有具有 `class="mine"` 属性的 `div` 元素
   
      7. **scrapy框架会根据 yield 返回的实例类型来执行不同的操作：**
   
         - 返回 scrapy.Request 对象，scrapy框架会去获得该对象指向的链接并在请求完成后调用该对象的回调函数。
         - 返回 scrapy.Item 对象，scrapy框架会将这个对象传递给 pipelines.py做进一步处理。
   
      8. pipeline
   
         >https://segmentfault.com/a/1190000013199835
   
      
   
   2. Crawley
   
      > Crawley是Python开发出的、基于非阻塞通信（NIO）的Python爬虫框架。它能高速爬取对应网站的内容，支持关系型和非关系型数据库如MongoDB、Postgre、Mysql、Oracle、Sqlite等，支持输出Json、XML 和CSV等各种格式。
   
   3. PySpider
   
      > pyspider是Binux做的一个爬虫架构的开源化实现，主要功能有 ：
      >
      > - 抓取、更新调度多站点的特定的页面
      > - 需要对页面进行结构化信息提取
      > - 灵活可扩展，稳定可监控
      >
      > pyspider以去重调度，队列抓取，异常处理，监控等功能作为框架，只需提供给抓取脚本，并保证灵活性。最后加上web的编辑调试环境，以及web任务监控，即成为了这套框架。pyspider的设计基础是：以python脚本驱动的抓取环模型爬虫
      >
      > - 各个组件间使用消息队列连接，除了scheduler是单点的，fetcher 和 processor 都是可以多实例分布式部署的。 scheduler 负责整体的调度控制
      > - 任务由 scheduler 发起调度，fetcher 抓取网页内容， processor 执行预先编写的python脚本，输出结果或产生新的提链任务（发往 scheduler），形成闭环
      > - 每个脚本可以灵活使用各种python库对页面进行解析，使用框架API控制下一步抓取动作，通过设置回调控制解析动作
   
   4. Portia
   
      > Portia是scrapyhub开源的一款可视化的爬虫规则编写工具，提供可视化的Web页面，用户只需要通过点击标注页面上需要抽取的数据，不需要任何编程知识即可完成规则的开发（但是动态网页需要自己编写JS解析器）。
      >
      > 除此之外，Portia框架还提供了网页版，用户不需要下载框架就可以直接使用，只需要注册一个账号即可。
   
   5. Newspaper
   
      > Newspaper框架是专门用于提取新闻、文章和内容分析的爬虫框架。该框架的特点包括：
      >
      > - 支持10多种语言（英语，中文，德语等）；
      > - 所有内容都使用Unicode编码；
      > - 使用多线程下载文章；
      > - 能够识别新闻网站的URL；
      > - 能够从网页中提取文本和图片，并且从文本中提取关键词、摘要和作者。
   
   6. Python-goose
   
      > Goose本身是一个Java语言编写的用于提取文章的框架，Python-goose是用Python语言对goose框架的重新实现。Python-goose的设计目的是爬取新闻和网页文章，并从中提取以下内容：
      >
      > - 文章的主体；
      > - 文章中的图片；
      > - 文章中包含的所有YouTube/Vimeo视频；
      > - 元描述信息；
      > - 元标签。



#	多线程(threading)

> 线程是CPU分配资源的基本单位。当一程序开始运行，这个程序就变成了一个进程，而一个进程相当于一个或者多个线程。当没有多线程编程时，一个进程相当于一个主线程；当有多线程编程时，一个进程包含多个线程（含主线程）。使用线程可以实现程序大的开发。
>
> 多个线程可以在同一个程序中运行，并且每一个线程完成不同的任务。
>
> 多线程实现后台服务程序可以同时处理多个任务，并不发生阻塞现象。
>
> 多线程的程序设计的特点就是能够提高程序执行效率和处理速度。
>
> python程序可以同时并行运行多个相对独立的线程。
>
> python的多线程可以降低IO的时间损耗，在遇到IO阻塞的时候可以执行其他线程任务，但数据处理的时间减少不是绝对的

 ```python
 import threading
 import time
 from queue import Queue
 
 
 def thread_job():
     print('T1 start\n')
     print("This is an added Thread, number is %s\n" % threading.current_thread())
     for i in range(3):
         time.sleep(1)
     print('T1 finish')
 
 
 def thread2_job(list, q):
     for i in range(len(list)):
         list[i] = list[i] ** 2
     q.put(list)
 
 
 def thread3_job():
     global A, lock
     lock.acquire()
     for i in range(10):
         A += 1
         print('job1', A)
     lock.release()
 
 
 def thread4_job():
     global A, lock
     lock.acquire()
     for i in range(10):
         A += 10
         print('job2', A)
     lock.release()
 
 
 def main():
     added_thread = threading.Thread(target=thread_job, name='T1')  # 添加线程
     added_thread.start()  # 运行线程
     added_thread.join()  # 阻塞主线程
     print('This is main function.')
 
     print(threading.active_count())  # 返回正在运行线程的数量，相当于len(threading.enumerate())
     print(threading.enumerate())  # 返回一个正在运行线程的列表
     print(threading.current_thread())  # 返回当前线程变量
 
     # 使用Queue队列返回多线程的结果
     q = Queue()
     data = [[1, 2, 3], [3, 4, 5], [4, 4, 4], [5, 5, 5]]
     threads = []
     for i in range(4):
         t = threading.Thread(target=thread2_job, args=(data[i], q))
         t.start()
         threads.append(t)
     for thread in threads:
         thread.join()
     result = []
     for _ in range(4):
         result.append(q.get())
     print(result)
 
     # 锁
     global A,lock
     A = 0
     lock = threading.Lock()
     t1 = threading.Thread(target=thread3_job)
     t2 = threading.Thread(target=thread4_job)
     t1.start()
     t2.start()
     t1.join()
     t2.join()
 
 
 if __name__ == '__main__':
     main()
 ```

- 注意：赋值给target的回调函数是不带括号的，不能这样`thread = threading.Thread(target=thread_job())`。带上括号会执行这个函数，target这里只是进行索引而已，是不带参数的，所以是没有()的。需要传递参数则使用args这个参数。
- 使用join方法后，该子线程所在的主线程会被阻塞，主线程会等待该子线程执行结束后再继续执行。
- 多线程是没有返回值的，需要把结果放在队列中，可以使用python的标准库queue。





#	异步执行

---



##	协程(coroutine )

1. 协程不是系统级线程，很多时候协程被称为“轻量级线程”、“微线程”、“纤程(fiber)”等，是用户态内的上下文切换技术，用于降低IO阻塞的时间消耗。简单来说可以认为协程是**同一个线程里不同的函数**，这些**函数之间可以相互快速切换**
2. 协程和用户态线程非常接近，用户态线程之间的切换不需要陷入内核，但部分操作系统中用户态线程的切换需要内核态线程的辅助
3. 协程是编程语言（或者 lib）提供的特性（协程之间的切换方式与过程可以由编程人员确定），是用户态操作。协程适用于 IO 密集型的任务。常见提供原生协程支持的语言有：c++20、golang、python 等，其他语言以库的形式提供协程功能，比如 C++20 之前腾讯的 fiber 和 libco 等等
4. Python中的实现方法
   1. greenlet，早期模块
   2. yield关键字，生成器
   3. asyncio装饰器 (Python 3.4及以上版本)
   4. async、await关键字 (Python 3.5及以上版本)【推荐】



##	asyncio

1. 事件循环(Eventloop)

   Eventloop可以说是asyncio应用的核心，是中央总控。Eventloop实例提供了注册、取消和执行任务和回调的方法。

   把一些异步函数(任务，Task)注册到这个事件循环上，事件循环会循环执行这些函数(但同时只能执行一个)，当执行到某个函数时，如果它正在等待I/O返回，事件循环会暂停它的执行去执行其他的函数；当某个函数完成I/O后会恢复，下次循环到它的时候继续执行。因此，这些异步函数可以协同(Cooperative)运行：这就是事件循环的目标。

   ```python
   import asyncio
   
   loop = asyncio.get_event_loop()  # 生成或获取一个事件循环
   loop.run_until_complete(asyncio.wait(tasks))  # 将任务放入任务列表中
   loop.close()  # 关闭事件循环
   
   # Python 3.7添加新接口可替代上述代码
   asyncio.run(asyncio.wait(tasks) )
   ```

2. 协程函数

   协程函数并不能在事件循环中被执行，必须要变成task才能被事件循环进行执行

   ```python
   # 此写法仅支持Python 3.5以上版本
   async def func():
       block
   ```

3. 协程对象

   ```python
   async def func():
       block
   result = func()	# 协程对象
   ```

   协程对象生成时不会执行协程函数

   协程对象可作为任务添加入事件循环中

4. await关键字

   类似于生成器的`yield from`

   await + IO等待 即可等待对象(协程对象、Future对象、Task对象)
   
   遇到IO操作时会挂起当前协程(任务)，等IO操作完成后等待事件循环再次执行该函数剩余部分；当当前协程挂起时事件循环可以去执行其他协程(任务)。
   
5. Future对象

   1. asyncio.Future对象它代表了一个「未来」对象，异步操作结束后会把最终结果设置到这个Future对象上。Future是对协程的封装，不过日常开发基本不需要直接用这个底层Future类。Task继承Future，Task对象内部await结果的处理基于Future。
   2. concurrent.futures.Future对象是使用进程池、线程池实现异步操作时用到的对象

6. Task对象

   Task是Future的子类，Tasks用于并发调度协程，通过`asyncio.create_task(协程对象)`的方式(仅适用于Python 3.7及以上版本)创建对象，这样可以让协程立即加入事件循环中等待被调度执行，即在事件循环中添加多个任务。还可以用低层级的`loop.create_task()`或`ensure_future()`函数。不建议手动实例化Task对象。

   asyncio.create_task方法是将一个协程包装成一个任务对象，**并且将该任务任务绑定到事件循环上** ，然后看时机等待被事件循环调度，这些都是非阻塞的，返回任务对象本身，如果你对任何一个可等待对象直接进行了await操作，那么一定得等到该可等待对象的状态确定之后才能返回，否则一定会被阻塞在此处，所以你不要在所有的地方都进行await操作，你只需在需要等待的地方进行await操作，以避免阻塞；并且你的每一个协程任务应该尽可能的小，让他们只做好一件事，如果是cpu密集型的任务，尽量与你的异步代码分离，因为你每个时刻只能干一件事，如果cpu密集型的任务占用了太多的cpu，你就没办法处理更多的IO了，异步IO是为了用更少的资源更方便处理更多的多的IO

   ```python
   import asyncio
   
   
   async def func():
       print(1)
       await asyncio.sleep(2)
       print(2)
       return '返回值'
   
   
   async def main():
       print('main开始')
       # 创建Task对象，并将这些对象放入一个列表中
       task_list = [
           asyncio.create_task(func(), name='n1'),
           asyncio.create_task(func(), name='n2')
       ]
       done, pending = await asyncio.wait(task_list, timeout=None)  # done以集合的形式接收结果，pending接收未完成任务
       print(done)
       print('main结束')
   
   
   asyncio.run(main())
   
   '''
   main开始
   1
   1
   2
   2
   {<Task finished name='n1' coro=<func() done, defined at E:\Test File\Python\STUDY-TEST\coroutine.py:9> result='返回值'>, <Task finished name='n2' coro=<func() done, defined at E:\Test File\Python\STUDY-TEST\coroutine.py:9> result='返回值'>}
   main结束
   '''
   ```

   ```python
   async def func():
       print(1)
       await asyncio.sleep(2)
       print(2)
       return '返回值'
   
   # 因为创建Task对象前没有事件循环被创建，因此此时使用asyncio.create_task()方法不能使协程添加进事件循环
   task_list = [
       func(),
       func()
   ]
   # asyncio.wait()方法会自动将task_list中的协程添加入事件循环
   done, pending =asyncio.run(asyncio.wait(task_list))
   print(done)
   
   '''
   1
   1
   2
   2
   {<Task finished name='Task-2' coro=<func() done, defined at E:\Test File\Python\STUDY-TEST\coroutine.py:9> result='返回值'>, <Task finished name='Task-3' coro=<func() done, defined at E:\Test File\Python\STUDY-TEST\coroutine.py:9> result='返回值'>}
   '''
   ```

7. 异步与非异步模块的结合

   ```python
   import asyncio
   import requests
   
   
   async def download_image(url):
       # 发送网络请求，下载图片
       print('开始下载', url)
   
       # request模块默认不支持异步操作，想要实现异步操作可以使用线程池进行转换
       # 第一步：内部会先调用 ThreadPoolExeutor的submit方法申请一个线程去执行函数，并返回一个concurrent.futures.Future对象
       # 第二步：调用asyncio.wrap_future方法将concurrent.futures.Future对象包装为asyncio.Future对象
       loop = asyncio.get_event_loop()
       future = loop.run_in_executor(None, requests.get, url)	# 第一个参数若为None则申请线程
       response = await future
       print('下载完成')
   
       # 将图片保存到本地
       file_name = url.rsplit('_')[-1]
       with open(file_name, mode='wb') as file_object:
           file_object.write(response.content)
   
   
   if __name__ == '__main__':
       url_list = [
   
       ]
   
       tasks = [download_image(url) for url in url_list]
       asyncio.run(asyncio.wait(tasks))
   
   ```

8. 异步上下文管理器

   此种对象通过定义`__aenter__()` `__aexit__()`方法对`async with`语句中的环境进行控制



##	uvloop

 uvloop是 asyncio 默认事件循环的一个代替品，实现的功能完整，且即插即用。

uvloop是用Cython写的，基于 li.buv。

uvloop 可以使 asyncio 更快。事实上，它至少比 nodejs、gevent 和其他 Python 异步框架要快 **两倍** 。基于 uvloop 的 asyncio 的速度几乎接近了 Go 程序的速度。

```python
import asyncio
import uvloop

asyncio.set_event_loop_policy(uvloop.EventLoopPloicy)
```

