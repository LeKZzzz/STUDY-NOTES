# C/C++构建

---

> ## GCC、Make工具、CMake工具
>
> 1. gcc是GNU Compiler Collection（就是GNU编译器套件），也可以简单认为是编译器，它可以编译很多种编程语言（括C、C++、Objective-C、Fortran、Java等等）。
>
> 2. 当你的程序只有一个源文件时，直接就可以用gcc命令编译它。但是当你的程序包含很多个源文件时，用gcc命令逐个去编译时，你就很容易混乱而且工作量大。所以出现了make工具，make工具可以看成是一个智能的批处理工具，它本身并没有编译和链接的功能，而是用类似于批处理的方式—通过调用makefile文件中用户指定的命令来进行编译和链接的。
>
> 3. makefile是什么？
>
>     简单的说就像一首歌的乐谱，make工具就像指挥家，指挥家根据乐谱指挥整个乐团怎么样演奏，make工具就根据makefile中的命令进行编译和链接的。
>
> 4. makefile命令中就包含了调用gcc（也可以是别的编译器）去编译某个源文件的命令。
>
> 5. makefile在一些简单的工程完全可以人工手写，但是当工程非常大的时候，手写makefile也是非常麻烦的，如果换了个平台makefile又要重新修改。
>
> 6. 这时候就出现了Cmake这个工具，cmake就可以更加简单的生成makefile文件给上面那个make用。当然cmake还有其他功能，就是可以跨平台生成对应平台能用的makefile，你不用再自己去修改了。
>
> 7. 可是cmake根据什么生成makefile呢？它又要根据一个叫CMakeLists.txt文件（学名：组态档）去生成makefile。
>
> 8. 到最后CMakeLists.txt文件谁写啊？亲，是你自己手写的。
>
> 9. 当然如果你用IDE，类似VS这些一般它都能帮你弄好了，你只需要按一下那个三角形

# Makefile

---

> 什么是`makefile`？或许很多`Windows`的程序员都不知道这个东西，因为那些`Windows`的`IDE`都为你做了这个工作，但我觉得要做一个好的和`professional`的程序员，`makefile`还是要懂。这就好像现在有这么多的`HTML`的编辑器，但如果你想成为一个专业人士，你还是要了解`HTML`的标识的含义。**特别在`Unix`下的软件编译，你就不能不自己写`makefile`了，会不会写makefile`，从一个侧面说明了一个人是否具备完成大型工程的能力**。
>
> 因为，`makefile`关系到了**整个工程的编译规则**。一个工程中的源文件不计数，其按类型、功能、模块分别放在若干个目录中，`makefile`**定义了一系列的规则**来指定，哪些文件需要先编译，哪些文件需要后编译，哪些文件需要重新编译，甚至于进行更复杂的功能操作，因为`makefile`就像一个`Shell`脚本一样，其中也可以执行操作系统的命令。
>
> `makefile`带来的好处就是——“自动化编译”，一旦写好，**只需要一个`make`命令，整个工程完全自动编译**，极大的提高了软件开发的效率。`make`是一个命令工具，是一个解释`makefile`中指令的命令工具，一般来说，大多数的`IDE`都有这个命令，比如：`Delphi`的`make`，`Visual C++`的`nmake`，`Linux`下`GNU`的`make`。可见，`makefile`都成为了一种在工程方面的编译方法。
>
> 现在讲述如何写`makefile`的文章比较少，这是我想写这篇文章的原因。当然，不同产商的`make`各不相同，也有不同的语法，但其本质都是在“文件依赖性”上做文章，这里，我仅对`GNU`的`make`进行讲述，我的环境是`RedHat Linux 8.0`，`make`的版本是`3.80`。必竟，这个`make`是应用最为广泛的，也是用得最多的。而且其还是最遵循于`IEEE 1003.2-1992`标准的（POSIX.2）。

1. 关于程序的编译和链接

    在此，我想多说关于程序编译的一些规范和方法，一般来说，无论是`C`、`C++`、还是`pas`，首先要把源文件编译成中间代码文件，在`Windows`下也就是`.obj`文件，`UNIX`下是`.o`文件，即 `Object File`，这个动作叫做**编译（compile）**。然后再把大量的`Object File`合成执行文件，这个动作叫作**链接（link）**。

    编译时，编译器需要的是**语法**的正确，**函数与变量的声明**的正确。对于后者，通常是你需要告诉编译器**头文件的所在位置**（头文件中应该只是声明，而定义应该放在`C/C++`文件中），只要所有的语法正确，编译器就可以编译出中间目标文件。一般来说，**每个源文件都应该对应于一个中间目标文件**（`.o`文件或是`.obj`文件）。

    链接时，主要是**链接函数和全局变量**，所以，我们可以使用这些中间目标文件（`.o`文件或是`.obj`文件）来链接我们的应用程序。链接器并不管函数所在的源文件，只管函数的中间目标文件（Object File），在大多数时候，由于源文件太多，编译生成的中间目标文件太多，而在链接时需要明显地指出中间目标文件名，这对于编译很不方便，所以，我们要**给中间目标文件打个包**，在`Windows`下这种包叫**库文件（Library File)**，也就是`.lib` 文件，在`UNIX`下，是**Archive File**，也就是`.a`文件。

    总结一下，源文件首先会生成**中间目标文件**，再由中间目标文件生成**执行文件**。在编译时，编译器只检测程序语法，和函数、变量是否被声明。如果函数未被声明，编译器会给出一个警告，但可以生成`Object File`。而在链接程序时，链接器会在所有的`Object File`中找寻函数的实现，如果找不到，那到就会报链接错误码（Linker Error），在`VC`下，这种错误一般是：`Link 2001错误`，意思说是说，链接器未能找到函数的实现。你需要指定函数的`Object File`

2. Makefile介绍

    1. 规则

        在讲述这个`Makefile`之前，还是让我们先来粗略地看一看`Makefile`的**规则**。

        ```shell
        target ... : prerequisites ...
        			command
                    ...
                    ...
        ```

        - `target`也就是一个目标文件，可以是`Object File`，也可以是执行文件。还可以是一个标签（Label），对于标签这种特性，在后续的“伪目标”章节中会有叙述。
        - `prerequisites`就是，要生成那个`target`所需要的文件或是目标。
        - `command`也就是`make`需要执行的命令。（任意的Shell命令）

        这是一个**文件的依赖关系**，也就是说，`target`这一个或多个的目标文件依赖于`prerequisites`中的文件，其生成规则定义在`command`中。说白一点就是说，`prerequisites`中如果有一个以上的文件比`target文件`要新的话，`command`所定义的命令就会被执行。这就是`Makefile`的规则。也就是`Makefile`中最核心的内容。

    2. make是如何工作的

        在默认的方式下，也就是我们只输入make命令。那么：

        1. `make`会在当前目录下找名字叫`Makefile`或`makefile`的文件。
        2. 如果找到，它会找文件中的第一个目标文件（target），在上面的例子中，他会找到`edit`这个并把这个文件作为最终的目标文件。
        3. 如果`edit`文件不存在，或是`edit`所依赖的后面的 `.o 文件`的修改时间要比`edit`这个文件新，那么，他就会执行后面所定义的命令来生成`edit`这个文件。
        4. 如果`edit`所依赖的`.o文件`不存在，那么`make`会在当前文件中找目标为`.o文件`的依赖性，如果找到，则根据对应的依赖规则生成`.o`文件。（这有点像一个堆栈的过程）
        5. 当然，你的C文件和H文件是存在的啦，于是`make`会生成`.o 文件`，然后再用`.o 文件`生成`make`的终极任务，也就是执行文件`edit`了。

        这就是整个`make`的**依赖性**，`make`会一层又一层地去找文件的**依赖关系**，直到最终编译出第一个目标文件。在寻找的过程中，如果出现错误，比如最后被依赖的文件找不到，那么make就会直接退出，并报错，而对于所定义的命令的错误，或是编译不成功，`make`根本不理。`make`只管文件的依赖性，即，如果在我找了依赖关系之后，冒号后面的文件还是不在，那么对不起，我就不工作啦。

        通过上述分析，我们知道，像`clean`这种，没有被第一个目标文件直接或间接关联，那么它后面所定义的命令将不会被自动执行，不过，我们可以显示要`make`执行。即执行命令`make clean`，以此来清除所有的目标文件，以便重编译。

        于是在我们编程中，如果这个工程已被编译过了，当我们修改了其中一个源文件，比如`file.c`，那么根据我们的依赖性，我们的目标`file.o`会被重编译（也就是在这个依性关系后面所定义的命令），于是`file.o`的文件也是最新的啦，于是`file.o`的文件修改时间要比`edit`要新，所以`edit`也会被重新链接了（详见edit目标文件后定义的命令）。

        而如果我们改变了`command.h`，那么，`kdb.o`、`command.o`和`iles.o`都会被重编译，并且，`edit`会被重链接。

    3. makefile中使用变量

        **为了makefile的易维护**，在`makefile`中我们可以**使用变量**。`makefile`的**变量也就是一个字符串**，理解成C语言中的宏可能会更好。

        比如，我们声明一个变量，叫objects, OBJECTS, objs, OBJS, obj, 或是 OBJ，反正不管什么啦，只要能够表示`obj文件`就行了。我们在`makefile`一开始就这样定义：

        ```shell
        objects = main.o kbd.o command.o display.o /
        		insert.o search.o files.o utils.o
        12
        ```

        于是，我们就可以很方便地在我们的`makefile`中以`$(objects)`的方式来使用这个变量了

    4. make自动推导

        `GNU`的`make`很强大，它可以**自动推导文件**以及**文件依赖关系后面的命令**，于是我们就没必要去在每一个`.o文件`后都写上类似的命令，因为，我们的`make`会**自动识别**，并**自己推导命令**。

        只要`make`看到一个`.o文件`，它就会自动的把`.c文件`加在依赖关系中，如果`make`找到一个`whatever.o`，那么`whatever.c`，就会是`whatever.o`的依赖文件。并且`cc -c whatever.c`也会被推导出来，于是，我们的`makefile`再也不用写得这么复杂。我们的是新的`makefile`又出炉了。

        ```shell
        # 变量定义
        objects = main.o kbd.o command.o display.o /
        		insert.o search.o files.o utils.o
        # 最终目标文件
        edit : $(objects)
        		cc -o edit $(objects)
        # 中间目标文件
        main.o : defs.h
        kbd.o : defs.h command.h
        command.o : defs.h command.h
        display.o : defs.h buffer.h
        insert.o : defs.h buffer.h
        search.o : defs.h buffer.h
        files.o : defs.h buffer.h command.h
        utils.o : defs.h
        # 伪目标文件
        .PHONY : clean
        clean :
        		rm edit $(objects)
        12345678910111213141516171819
        ```

        这种方法，也就是`make`的隐晦规则。
        **上面文件内容中，`.PHONY`表示，`clean`是个伪目标文件。**
        关于更为详细的**隐晦规则**和**伪目标文件**，我会在后续给你一一道来。





# CMake

----

## 添加第三方库

```cmake
set(INC_DIR  ./lib/openssl/include)	# 头文件目录
set(LINK_DIR  ./lib/openssl/MD)	# 库目录

include_directories(${INC_DIR})
link_directories(${LINK_DIR})
link_libraries(libssl libcrypto)	# 要链接的库

add_executable(test test.cpp headers.h)

target_link_libraries(test libssl libcrypto)
```

