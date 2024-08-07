# C++

---

# 简介

C++ 是一种静态类型的、**编译式**的、通用的、**大小写敏感的**、不规则的编程语言，支持过程化编程、面向对象编程和泛型编程。

C++ 被认为是一种**中级**语言，它综合了高级语言和低级语言的特点。

C++ 是由 Bjarne Stroustrup 于 1979 年在新泽西州美利山贝尔实验室开始设计开发的。C++ 进一步扩充和完善了 C 语言，最初命名为带类的C，后来在 1983 年更名为 C++。

C++ 是 C 的一个超集，事实上，任何合法的 C 程序都是合法的 C++ 程序。

**注意：**使用静态类型的编程语言是在编译时执行类型检查，而不是在运行时执行类型检查。



# ANSI 标准

ANSI 标准是为了确保 C++ 的便携性 —— 您所编写的代码在 Mac、UNIX、Windows、Alpha 计算机上都能通过编译。

由于 ANSI 标准已稳定使用了很长的时间，所有主要的 C++ 编译器的制造商都支持 ANSI 标准。



# 标准化

| 发布时间 | 通称                    | 备注                       |
| :------- | :---------------------- | :------------------------- |
| 2020     | C++20, C++2a            | ISO/IEC 14882:2020         |
| 2017     | C++17                   | 第五个C++标准              |
| 2017     | coroutines TS           | 协程库扩展                 |
| 2017     | ranges TS               | 提供范围机制               |
| 2017     | library fundamentals TS | 标准库扩展                 |
| 2016     | concurrency TS          | 用于并发计算的扩展         |
| 2015     | concepts TS             | 概念库，用于优化编译期信息 |
| 2015     | TM TS                   | 事务性内存操作             |
| 2015     | parallelism TS          | 用于并行计算的扩展         |
| 2015     | filesystem TS           | 文件系统                   |
| 2014     | C++14                   | 第四个C++标准              |
| 2011     | -                       | 十进制浮点数扩展           |
| 2011     | C++11                   | 第三个C++标准              |
| 2010     | -                       | 数学函数扩展               |
| 2007     | C++TR1                  | C++技术报告：库扩展        |
| 2006     | -                       | C++性能技术报告            |
| 2003     | C++03                   | 第二个C++标准              |
| 1998     | C++98                   | 第一个C++标准              |



# 内存分布

1. **栈（Stack）**：
    - 栈是用于存储函数的局部变量、函数参数、以及函数调用时的上下文信息的内存区域。
    - 每当调用函数时，栈会分配一段内存空间来存储函数的参数和局部变量。当函数返回时，这段内存空间会被释放。
    - 栈是一种先进后出（LIFO）的数据结构，它通常在编译时分配，并且具有固定的大小。
2. **堆（Heap）**：
    - 堆是用于动态分配内存的内存区域，它的大小和生命周期不固定，由程序在运行时决定。
    - 在堆上分配的内存需要程序员手动管理，包括分配和释放，通常使用 `new` 和 `delete` 操作符来进行操作。
    - 堆的内存分配由操作系统的内存管理器进行管理，它通常比栈的分配和释放更复杂，也更慢。
3. **全局/静态内存区域**：
    - 全局/静态内存区域用于存储全局变量、静态变量以及常量数据。
    - 这部分内存在程序启动时被分配，并在程序结束时释放。
    - 全局变量和静态变量通常在编译时分配，并且具有固定的大小。
4. **常量区（Constant Area）**：
    - 常量区用于存储程序中的常量数据，如字符串常量等。
    - 这部分内存通常在程序加载时分配，并且在整个程序的生命周期内保持不变。
5. **代码区（Code Area）**：
    - 代码区存储程序的机器码指令，也称为可执行代码段。
    - 这部分内存在程序加载时分配，并且在程序执行期间保持不变。

下图展示了这些内存区域的典型布局：

```
High Memory Addresses
                    -----------------
                    |   Constant    | <- 常量区
                    |     Area      |
                    -----------------
                    |               | 
                    |               | 
                    |               | 
                    |               | 
                    |   Global /    | <- 全局变量、静态变量
                    |  Static Area  |
                    |               |
                    |               |
                    |               |
                    |               |
                    -----------------
                    |               |
                    |               |
                    |     Heap      | <- 堆
                    |               |
                    |               |
                    -----------------
                    |               |
                    |               |
                    |     Stack     | <- 栈
                    |               |
                    |               |
Low Memory Addresses
```

需要注意的是，内存布局可能因操作系统、编译器和程序运行环境的不同而有所差异。上述描述提供了一种典型的情况，实际情况可能会有所不同。

由低地址到高地址：

1. 代码段

    二进制可执行代码

2. 已初始化的数据段

    静态常量

3. 未初始化的数据段

    未初始化的静态变量

4. 堆段

    低地址往高地址

    动态分配

5. 文件映射段

    动态库、共享内存等

6. 栈段

    高地址往低地址

    局部变量、函数调用上下文

7. 内核空间

# 本地环境设置

## 文本编辑器

这将用于输入您的程序。文本编辑器包括 Windows Notepad、OS Edit command、Brief、Epsilon、EMACS 和 vim/vi。

文本编辑器的名称和版本在不同的操作系统上可能会有所不同。例如，Notepad 通常用于 Windows 操作系统上，vim/vi 可用于 Windows 和 Linux/UNIX 操作系统上。

通过编辑器创建的文件通常称为源文件，源文件包含程序源代码。C++ 程序的源文件通常使用扩展名 .cpp、.cp 或 .c。

在开始编程之前，请确保您有一个文本编辑器，且有足够的经验来编写一个计算机程序，然后把它保存在一个文件中，编译并执行它。

## C++ 编译器

写在源文件中的源代码是人类可读的源。它需要"编译"，转为机器语言，这样 CPU 可以按给定指令执行程序。

C++ 编译器用于把源代码编译成最终的可执行程序。

大多数的 C++ 编译器并不在乎源文件的扩展名，但是如果您未指定扩展名，则默认使用 .cpp。

最常用的免费可用的编译器是 GNU 的 C/C++ 编译器，如果您使用的是 HP 或 Solaris，则可以使用各自操作系统上的编译器。

以下部分将指导您如何在不同的操作系统上安装 GNU 的 C/C++ 编译器。这里同时提到 C/C++，主要是因为 GNU 的 gcc 编译器（GNU Compiler Collection，GNU编译器套件，GNU开发的编程语言编译器）适合于 C 和 C++ 编程语言。



### GNU 的 C/C++ 编译器

#### UNIX/Linux 上的安装

如果您使用的是 **Linux 或 UNIX**，请在命令行使用下面的命令来检查您的系统上是否安装了 GCC：

```
$ g++ -v
```

如果您的计算机上已经安装了 GNU 编译器，则会显示如下消息：

```
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr .......
Thread model: posix
gcc version 4.1.2 20080704 (Red Hat 4.1.2-46)
```

如果未安装 GCC，那么请按照 http://gcc.gnu.org/install/ 上的详细说明安装 GCC。

#### Mac OS X 上的安装

如果您使用的是 Mac OS X，最快捷的获取 GCC 的方法是从苹果的网站上下载 Xcode 开发环境，并按照安装说明进行安装。一旦安装上 Xcode，您就能使用 GNU 编译器。

Xcode 目前可从 https://developer.apple.com/download 上下载，需要使用 apple ID 登录 。

#### Windows 上的安装

为了在 Windows 上安装 GCC，您需要安装 MinGW。为了安装 MinGW，请访问 MinGW 的主页 [mingw-w64.org](https://www.mingw-w64.org/)，进入 MinGW 下载页面，下载最新版本的 MinGW 安装程序，命名格式为 MinGW-<version>.exe。

当安装 MinGW 时，您至少要安装 gcc-core、gcc-g++、binutils 和 MinGW runtime，但是一般情况下都会安装更多其他的项。

添加您安装的 MinGW 的 bin 子目录到您的 **PATH** 环境变量中，这样您就可以在命令行中通过简单的名称来指定这些工具。

当完成安装时，您可以从 Windows 命令行上运行 gcc、g++、ar、ranlib、dlltool 和其他一些 GNU 工具。

#### g++ 应用说明

程序 g++ 是将 gcc 默认语言设为 C++ 的一个特殊的版本，链接时它自动使用 C++ 标准库而不用 C 标准库。通过遵循源码的命名规范并指定对应库的名字，用 gcc 来编译链接 C++ 程序是可行的，如下例所示：

| 选项         | 解释                                                         |
| :----------- | :----------------------------------------------------------- |
| -ansi        | 只支持 ANSI 标准的 C 语法。这一选项将禁止 GNU C 的某些特色， 例如 asm 或 typeof 关键词。 |
| -c           | 只编译并生成目标文件。                                       |
| -DMACRO      | 以字符串"1"定义 MACRO 宏。                                   |
| -DMACRO=DEFN | 以字符串"DEFN"定义 MACRO 宏。                                |
| -E           | 只运行 C 预编译器。                                          |
| -g           | 生成调试信息。GNU 调试器可利用该信息。                       |
| -IDIRECTORY  | 指定额外的头文件搜索路径DIRECTORY。                          |
| -LDIRECTORY  | 指定额外的函数库搜索路径DIRECTORY。                          |
| -lLIBRARY    | 连接时搜索指定的函数库LIBRARY。                              |
| -m486        | 针对 486 进行代码优化。                                      |
| -o           | FILE 生成指定的输出文件。用在生成可执行文件时。              |
| -O0          | 不进行优化处理。                                             |
| -O           | 或 -O1 优化生成代码。                                        |
| -O2          | 进一步优化。                                                 |
| -O3          | 比 -O2 更进一步优化，包括 inline 函数。                      |
| -shared      | 生成共享目标文件。通常用在建立共享库时。                     |
| -static      | 禁止使用共享连接。                                           |
| -UMACRO      | 取消对 MACRO 宏的定义。                                      |
| -w           | 不生成任何警告信息。                                         |
| -Wall        | 生成所有警告信息。                                           |



## 头文件存放路径

- Linux下：/usr/include



#	关键字

| asm          | else      | new              | this     |
| ------------ | --------- | ---------------- | -------- |
| auto         | enum      | operator         | throw    |
| bool         | explicit  | private          | true     |
| break        | export    | protected        | try      |
| case         | extern    | public           | typedef  |
| catch        | false     | register         | typeid   |
| char         | float     | reinterpret_cast | typename |
| class        | for       | return           | union    |
| const        | friend    | short            | unsigned |
| const_cast   | goto      | signed           | using    |
| continue     | if        | sizeof           | virtual  |
| default      | inline    | static           | void     |
| delete       | int       | static_cast      | volatile |
| do           | long      | struct           | wchar_t  |
| double       | mutable   | switch           | while    |
| dynamic_cast | namespace | template         |          |



# 运算符

1. 算术运算符

   | 运算符 | 描述                             | 实例             |
   | :----- | :------------------------------- | :--------------- |
   | +      | 把两个操作数相加                 | A + B 将得到 30  |
   | -      | 从第一个操作数中减去第二个操作数 | A - B 将得到 -10 |
   | *      | 把两个操作数相乘                 | A * B 将得到 200 |
   | /      | 分子除以分母                     | B / A 将得到 2   |
   | %      | 取模运算符，整除后的余数         | B % A 将得到 0   |
   | ++     | 自增运算符，整数值增加 1         | A++ 将得到 11    |
   | --     | 自减运算符，整数值减少 1         | A-- 将得到 9     |

2. 关系运算符

   | 运算符 | 描述                                                         | 实例              |
   | :----- | :----------------------------------------------------------- | :---------------- |
   | ==     | 检查两个操作数的值是否相等，如果相等则条件为真。             | (A == B) 不为真。 |
   | !=     | 检查两个操作数的值是否相等，如果不相等则条件为真。           | (A != B) 为真。   |
   | >      | 检查左操作数的值是否大于右操作数的值，如果是则条件为真。     | (A > B) 不为真。  |
   | <      | 检查左操作数的值是否小于右操作数的值，如果是则条件为真。     | (A < B) 为真。    |
   | >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。 | (A >= B) 不为真。 |
   | <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。 | (A <= B) 为真。   |

3. 逻辑运算符

   | 运算符 | 描述                                                         | 实例                 |
   | :----- | :----------------------------------------------------------- | :------------------- |
   | &&     | 称为逻辑与运算符。如果两个操作数都 true，则条件为 true。     | (A && B) 为 false。  |
   | \|\|   | 称为逻辑或运算符。如果两个操作数中有任意一个 true，则条件为 true。 | (A \|\| B) 为 true。 |
   | !      | 称为逻辑非运算符。用来逆转操作数的逻辑状态，如果条件为 true 则逻辑非运算符将使其为 false。 | !(A && B) 为 true。  |

4. 位运算符

   位运算符作用于位，并逐位执行操作。&、 | 和 ^ 的真值表如下所示：

   | p    | q    | p & q | p \| q | p ^ q |
   | :--- | :--- | :---- | :----- | :---- |
   | 0    | 0    | 0     | 0      | 0     |
   | 0    | 1    | 0     | 1      | 1     |
   | 1    | 1    | 1     | 1      | 0     |
   | 1    | 0    | 0     | 1      | 1     |

5. 赋值运算符

   | 运算符 | 描述                                                         | 实例                            |
   | :----- | :----------------------------------------------------------- | :------------------------------ |
   | =      | 简单的赋值运算符，把右边操作数的值赋给左边操作数             | C = A + B 将把 A + B 的值赋给 C |
   | +=     | 加且赋值运算符，把右边操作数加上左边操作数的结果赋值给左边操作数 | C += A 相当于 C = C + A         |
   | -=     | 减且赋值运算符，把左边操作数减去右边操作数的结果赋值给左边操作数 | C -= A 相当于 C = C - A         |
   | *=     | 乘且赋值运算符，把右边操作数乘以左边操作数的结果赋值给左边操作数 | C *= A 相当于 C = C * A         |
   | /=     | 除且赋值运算符，把左边操作数除以右边操作数的结果赋值给左边操作数 | C /= A 相当于 C = C / A         |
   | %=     | 求模且赋值运算符，求两个操作数的模赋值给左边操作数           | C %= A 相当于 C = C % A         |
   | <<=    | 左移且赋值运算符                                             | C <<= 2 等同于 C = C << 2       |
   | >>=    | 右移且赋值运算符                                             | C >>= 2 等同于 C = C >> 2       |
   | &=     | 按位与且赋值运算符                                           | C &= 2 等同于 C = C & 2         |
   | ^=     | 按位异或且赋值运算符                                         | C ^= 2 等同于 C = C ^ 2         |
   | \|=    | 按位或且赋值运算符                                           | C \|= 2 等同于 C = C \| 2       |

6. 杂项运算符

   | 运算符               | 描述                                                         |
   | :------------------- | :----------------------------------------------------------- |
   | sizeof               | sizeof 运 算符返回变量的大小。例如，sizeof(a) 将返回 4，其中 a 是整数。 |
   | Condition ? X : Y    | 条件运算符。如果 Condition 为真 ? 则值为 X : 否则值为 Y。    |
   | ,                    | 逗号运算符会顺序执行一系列运算。整个逗号表达式的值是以逗号分隔的列表中的最后一个表达式的值。 |
   | .（点）和 ->（箭头） | 成员运算符用于引用类、结构和共用体的成员。                   |
   | Cast                 | 强制转换运算符把一种数据类型转换为另一种数据类型。例如，int(2.2000) 将返回 2。 |
   | &                    | 指针运算符 & 返回变量的地址。例如 &a; 将给出变量的实际地址。 |
   | *                    | 指针运算符 * 指向一个变量。例如，*var; 将指向变量 var。      |

7. 运算符优先级

   按运算符优先级从高到低列出各个运算符

   | 类别       | 运算符                            | 结合性   |
   | :--------- | :-------------------------------- | :------- |
   | 后缀       | () [] -> . ++ - -                 | 从左到右 |
   | 一元       | + - ! ~ ++ - - (type)* & sizeof   | 从右到左 |
   | 乘除       | * / %                             | 从左到右 |
   | 加减       | + -                               | 从左到右 |
   | 移位       | << >>                             | 从左到右 |
   | 关系       | < <= > >=                         | 从左到右 |
   | 相等       | == !=                             | 从左到右 |
   | 位与 AND   | &                                 | 从左到右 |
   | 位异或 XOR | ^                                 | 从左到右 |
   | 位或 OR    | \|                                | 从左到右 |
   | 逻辑与 AND | &&                                | 从左到右 |
   | 逻辑或 OR  | \|\|                              | 从左到右 |
   | 条件       | ?:                                | 从右到左 |
   | 赋值       | = += -= *= /= %=>>= <<= &= ^= \|= | 从右到左 |
   | 逗号       | ,                                 | 从左到右 |



# 三字符组

三字符组就是用于表示另一个字符的三个字符序列，又称为三字符序列。三字符序列总是以两个问号开头。

三字符序列不太常见，但 C++ 标准允许把某些字符指定为三字符序列。以前为了表示键盘上没有的字符，这是必不可少的一种方法。

三字符序列可以出现在任何地方，包括字符串、字符序列、注释和预处理指令。

从Microsoft Visual C++ 2010版开始，该编译器默认不再自动替换三字符组。如果需要使用三字符组替换（如为了兼容古老的软件代码），需要设置编译器命令行选项/Zc:trigraphs

g++仍默认支持三字符组，但会给出编译警告。

| 三字符组 | 替换 |
| :------- | :--- |
| ??=      | #    |
| ??/      | \    |
| ??'      | ^    |
| ??(      | [    |
| ??)      | ]    |
| ??!      | \|   |
| ??<      | {    |
| ??>      | }    |
| ??-      | ~    |



# 注释

1. C++ 支持单行注释和多行注释。注释中的所有字符会被 C++ 编译器忽略。

2. C++ 注释一般有两种：

   - **//** - 一般用于单行注释。注释以 **//** 开始，直到行末为止。

   - **/* ... */** - 一般用于多行注释。

3. 在 **/\*** 和 ***/** 注释内部，**//** 字符没有特殊的含义。在 **//** 注释内，**/\*** 和 ***/** 字符也没有特殊的含义，因此可以在一种注释内嵌套另一种注释。

4. 块注释符（/*...*/）是不可以嵌套使用的。

5. **#if 0 ... #endif** 属于条件编译，0 即为参数。

   此外，我们还可以使用 **#if 0 ... #endif** 来实现注释，且可以实现嵌套，格式为：

   ```
   #if 0
      code
   #endif 
   ```

   可以把 **#if 0** 改成 **#if 1** 来执行 **code** 的代码。

   这种形式对程序调试也可以帮助，测试时使用 **#if 1** 来执行测试代码，发布后使用 **#if 0** 来屏蔽测试代码。

   **#if** 后可以是任意的条件语句。

   下面的代码如果 condition 条件为 true 执行 code1 ，否则执行 code2。

   ```
   #if condition
     code1
   #else
     code2
   #endif
   ```



# 数据类型



## 基本内置类型

| 类型     | 关键字  |
| :------- | :------ |
| 布尔型   | bool    |
| 字符型   | char    |
| 整型     | int     |
| 浮点型   | float   |
| 双浮点型 | double  |
| 无类型   | void    |
| 宽字符型 | wchar_t |

> ```c++
> typedef short int wchar_t;
> ```
>
>  wchar_t 实际上的空间和 short int 一样。

| 类型               | 位            | 范围                                                         |
| :----------------- | :------------ | :----------------------------------------------------------- |
| char               | 1 个字节      | -128 到 127 或者 0 到 255                                    |
| unsigned char      | 1 个字节      | 0 到 255                                                     |
| signed char        | 1 个字节      | -128 到 127                                                  |
| int                | 4 个字节      | -2147483648 到 2147483647                                    |
| unsigned int       | 4 个字节      | 0 到 4294967295                                              |
| signed int         | 4 个字节      | -2147483648 到 2147483647                                    |
| short int          | 2 个字节      | -32768 到 32767                                              |
| unsigned short int | 2 个字节      | 0 到 65,535                                                  |
| signed short int   | 2 个字节      | -32768 到 32767                                              |
| long int           | 8 个字节      | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807      |
| signed long int    | 8 个字节      | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807      |
| unsigned long int  | 8 个字节      | 0 到 18,446,744,073,709,551,615                              |
| float              | 4 个字节      | 精度型占4个字节（32位，1位符号，8位指数，23位小数。）内存空间，+/- 3.4e +/- 38 (~7 个数字) |
| double             | 8 个字节      | 双精度型占8 个字节（64位，1位符号，11位指数，52位小数）内存空间，+/- 1.7e +/- 308 (~15 个数字) |
| long double        | 16 个字节     | 长双精度型 16 个字节（128位）内存空间，可提供18-19位有效数字。 |
| wchar_t            | 2 或 4 个字节 | 1 个宽字符                                                   |

> 一些基本类型可以使用一个或多个类型修饰符进行修饰：
>
> - signed
> - unsigned
> - short
> - long
>
> 不同系统会有所差异，各种类型的存储大小与系统位数有关，一字节为 8 位。
>
> 默认情况下，int、short、long都是带符号的，即 signed。
>
> long int 8 个字节，int 都是 4 个字节，早期的 C 编译器定义了 long int 占用 4 个字节，int 占用 2 个字节，新版的 C/C++ 标准兼容了早期的这一设定。



## typedef 声明

可以使用 **typedef** 为一个已有的类型取一个新的名字

```c++
typedef type newname; 
```



## 枚举类型

枚举类型(enumeration)是C++中的一种派生数据类型，它是由用户定义的若干枚举常量的集合。

如果一个变量只有几种可能的值，可以定义为枚举(enumeration)类型。所谓"枚举"是指将变量的值一一列举出来，变量的值只能在列举出来的值的范围内。

创建枚举，需要使用关键字 **enum**。

如果枚举没有初始化, 即省掉"=整型常数"时, 则从第一个标识符开始。

默认情况下，第一个名称的值为 0，第二个名称的值为 1，第三个名称的值为 2，以此类推。但是，您也可以给名称赋予一个特殊的值，只需要添加一个初始值即可，这个初始值会影响在这个值之后的标识符对应的值。

枚举类型的一般形式为：

```c++
enum 枚举名{ 
     标识符[=整型常数], 
     标识符[=整型常数], 
... 
    标识符[=整型常数]
} 枚举变量;
```



## 修饰符

C++ 允许在 **char、int 和 double** 数据类型前放置修饰符：

- signed
- unsigned
- long
- short

修饰符 **signed、unsigned、long 和 short** 可应用于整型，**signed** 和 **unsigned** 可应用于字符型，**long** 可应用于双精度型。

修饰符 **signed** 和 **unsigned** 也可以作为 **long** 或 **short** 修饰符的前缀。例如：**unsigned long int**。

C++ 允许使用速记符号来声明**无符号短整数**或**无符号长整数**。可以不写 int，只写单词 **unsigned、short** 或 **long**，**int** 是隐含的。



## 限定符

| 限定符   | 含义                                                         |
| :------- | :----------------------------------------------------------- |
| const    | **const** 类型的对象在程序执行期间不能被修改改变。           |
| volatile | 修饰符 **volatile** 告诉编译器不需要优化volatile声明的变量，让程序可以直接从内存中读取变量。对于一般的变量编译器会对变量进行优化，将内存中的变量值放在寄存器中以加快读写效率。 |
| restrict | 由 **restrict** 修饰的指针是唯一一种访问它所指向的对象的方式。只有 C99 增加了新的类型限定符 restrict。 |



## 内存占用

1. **整数类型**：

    - `char`：通常占用 1 字节（8 位），取决于编译器和平台，有时可能占用更多字节。
    - `short int`（`short`）：通常占用 2 字节（16 位）。
    - `int`：通常占用 4 字节（32 位）。
    - `long int`（`long`）：通常占用 4 或 8 字节（32 或 64 位）。
    - `long long int`（`long long`）：通常占用 8 字节（64 位）。

2. **浮点类型**：

    - `float`：通常占用 4 字节（32 位），单精度浮点数。
    - `double`：通常占用 8 字节（64 位），双精度浮点数。
    - `long double`：通常占用 10 或更多字节（80 位或更多），扩展精度浮点数。

3. **布尔类型**：

    - `bool`：通常占用 1 字节，但只使用 1 位。存储 `true` 或 `false`。

4. **字符类型**：

    - `char`：通常占用 1 字节。存储 ASCII 字符或者宽字符（wchar_t）。

5. **指针类型**：

    - 所有指针类型（如 `int*`、`char*` 等）在 32 位系统上通常占用 4 字节，64 位系统上通常占用 8 字节。

6. **复合类型**：

    - 数组：根据元素的类型和数量计算大小。例如 `int array[5]` 通常占用 `5 * sizeof(int)` 字节。

    - 结构体（struct）：由一组不同类型的成员组成，占用成员大小之和，可能需要对齐。

        > 结构体的对齐是指编译器在分配内存时如何安排结构体的成员变量在内存中的存放位置。对齐的目的是为了提高内存访问的效率，因为在大多数计算机架构中，访问未对齐的内存地址可能会导致性能下降甚至出现异常。
        >
        > 结构体的对齐通常遵循以下原则：
        >
        > 1. **成员变量对齐**：
        >     - 结构体的每个成员变量在内存中的存放位置通常需要满足其自身的对齐要求。例如，一个 `int` 类型通常需要在内存中对齐到4字节边界，而一个 `double` 类型通常需要对齐到8字节边界。
        >     - 这意味着结构体的每个成员变量通常会在内存中分配足够的空间，并且可能会在结构体的开头或者某个位置开始对齐。
        > 2. **结构体整体对齐**：
        >     - 结构体本身的起始地址通常需要满足所有成员变量的最大对齐要求。这意味着结构体的起始地址可能会被调整，以确保结构体中的最大对齐要求被满足。
        >     - 例如，如果结构体中有一个 `double` 类型的成员变量，那么结构体的起始地址通常需要对齐到8字节边界。
        > 3. **填充字节**：
        >     - 为了满足对齐要求，编译器可能会在结构体的成员变量之间插入额外的填充字节。
        >     - 这些填充字节的数量和位置取决于结构体中每个成员变量的大小和对齐要求。
        > 4. 需要注意的是，结构体的对齐规则可能因编译器、编译选项和目标平台的不同而有所不同。在某些情况下，可以使用编译器指令或预处理器指令来修改对齐规则，以满足特定的需求。

    - 联合体（union）：所有成员共享同一块内存空间，占用最大成员的大小。

7. **枚举类型**：

    - 取决于枚举中常量的数量，通常与 `int` 类型相同大小。

8. **自定义类型**：

    - 取决于类型定义的方式和平台的字节对齐方式。

9. **引用**：

    - 引用本身在大多数情况下不占用额外的空间，因为引用被视为对象的别名。它们通常被实现为指针，因此在内存中占用与指针相同大小的空间（通常为 4 或 8 字节）。
    - 引用用于提供对变量的别名，因此它们不是独立的对象，而是与被引用的对象共享存储空间。因此，引用本身不会增加额外的空间消耗。

10. **自定义对象**：

    - 自定义对象的大小取决于其成员变量的大小之和，以及可能的内存对齐方式。
    - 对象的大小也可能受到编译器的优化和内存对齐的影响。例如，结构体（`struct`）或类（`class`）可能会被编译器重新排列，以避免内存浪费。
    - 如果对象包含指针或其他引用类型的成员变量，需要考虑指针或引用本身的大小，并且需要额外的内存来存储指向的对象。

> 上述大小是基于通常情况下的典型实现，实际情况可能会因编译器、操作系统和硬件平台的不同而有所不同。可以使用 `sizeof` 运算符来确定特定数据类型在当前系统中的大小。

# 变量

## 定义

变量定义就是告诉编译器在何处创建变量的存储，以及如何创建变量的存储。

```c++
type variable_list;
```

**type** 必须是一个有效的 C++ 数据类型，可以是 char、wchar_t、int、float、double、bool 或任何用户自定义的对象，**variable_list** 可以由一个或多个标识符名称组成，多个标识符之间用逗号分隔

变量可以在声明的时候被初始化（指定一个初始值）。初始化器由一个等号，后跟一个常量表达式组成

不带初始化的定义：带有静态存储持续时间的变量会被隐式初始化为 NULL（所有字节的值都是 0），其他所有变量的初始值是未定义的。



## 声明

变量声明向编译器保证变量以给定的类型和名称存在，这样编译器在不需要知道变量完整细节的情况下也能继续进一步的编译。变量声明只在编译时有它的意义，在程序连接时编译器需要实际的声明变量。

当您使用多个文件且只在其中一个文件中定义变量时（定义变量的文件在程序连接时是可用的），变量声明就显得非常有用。您可以使用 **extern** 关键字在任何地方声明一个变量。虽然您可以在 C++ 程序中多次声明一个变量，但变量只能在某个文件、函数或代码块中被定义一次。



## 左值（Lvalues）和右值（Rvalues）

- **左值（lvalue）**：**指向内存位置**的表达式被称为左值（lvalue）表达式。左值可以出现在赋值号的左边或右边。
- **右值（rvalue）**：术语右值（rvalue）指的是**存储在内存中某些地址的数值**。右值是不能对其进行赋值的表达式，也就是说，右值可以出现在赋值号的右边，但不能出现在赋值号的左边。



## 自动转换

1、若参与运算量的类型不同，则先转换成同一类型，然后进行运算。

2、转换按数据长度增加的方向进行，以保证精度不降低。如int型和long型运算时，先把int量转成long型后再进行运算。   		a、若两种类型的字节数不同，转换成字节数高的类型   

​		b、若两种类型的字节数相同，且一种有符号，一种无符号，则转换成无符号类型

 3、所有的浮点运算都是以双精度进行的，即使仅含float单精度量运算的表达式，也要先转换成double型，再作运算。

 4、char型和short型参与运算时，必须先转换成int型。

 5、在赋值运算中，赋值号两边量的数据类型不同时，赋值号右边量的类型将转换为左边量的类型。如果右边量的数据类型长度比左边长时，将丢失一部分数据，这样会降低精度。



## 强制转换

```
(type) variable
```

强制类型转换是通过类型转换运算来实现的。

其功能是把表达式的运算结果强制转换成类型说明符所表示的类型



## 作用域

作用域是程序的一个区域，一般来说有三个地方可以定义变量：

1. 在函数或一个代码块内部声明的变量，称为局部变量

   它们只能被函数内部或者代码块内部的语句使用。

2. 在函数参数的定义中声明的变量，称为形式参数。

3. 在所有函数外部声明的变量，称为全局变量。

   在所有函数外部定义的变量（通常是在程序的头部）

   全局变量的值在程序的整个生命周期内都是有效的。

   全局变量可以被任何函数访问。也就是说，全局变量一旦声明，在整个程序中都是可用的。

   全局变量在堆中创建。

在程序中，局部变量和全局变量的名称可以相同，但是在函数内，局部变量的值会覆盖全局变量的值。

当局部变量被定义时，系统不会对其初始化，您必须自行对其初始化。定义全局变量时，系统会自动初始化为下列值：

| 数据类型 | 初始化默认值 |
| :------- | :----------- |
| int      | 0            |
| char     | '\0'         |
| float    | 0            |
| double   | 0            |
| pointer  | NULL         |



# 常量

 常量是固定值，在程序执行期间不会改变。这些固定的值，又叫做**字面量**。

常量可以是任何的基本数据类型，可分为整型数字、浮点数字、字符、字符串和布尔值。

常量就像是常规的变量，只不过常量的值在定义后不能进行修改。

把常量定义为大写字母形式，是一个很好的编程实践

常量定义方式：

- 使用 **#define** 预处理器。

   ```c++
   #define identifier value
   ```

- 使用 **const** 关键字。

   ```c++
   const type variable = value;
   ```

   

1. 整数常量

   整数常量可以是十进制、八进制或十六进制的常量。前缀指定基数：0x 或 0X 表示十六进制，0 表示八进制，不带前缀则默认表示十进制。

   整数常量也可以带一个后缀，后缀是 U 和 L 的组合，U 表示无符号整数（unsigned），L 表示长整数（long）。后缀可以是大写，也可以是小写，U 和 L 的顺序任意，不能重复后缀

2. 浮点常量

   浮点常量由整数部分、小数点、小数部分和指数部分组成。您可以使用小数形式或者指数形式来表示浮点常量。

   当使用小数形式表示时，必须包含整数部分、小数部分，或同时包含两者。当使用指数形式表示时， 必须包含小数点、指数，或同时包含两者。带符号的指数是用 e 或 E 引入的。

   ```c++
   3.14159       // 合法的 
   314159E-5L    // 合法的 
   510E          // 非法的：不完整的指数
   210f          // 非法的：没有小数或指数
   .e55          // 非法的：缺少整数或分数
   ```

3. 布尔常量

   布尔常量共有两个，它们都是标准的 C++ 关键字：

   - **true** 值代表真。
   - **false** 值代表假。

   我们不应把 true 的值看成 1，把 false 的值看成 0。

4. 字符常量

   字符常量是括在单引号中。如果常量以 L（仅当大写时）开头，则表示它是一个宽字符常量（例如 L'x'），此时它必须存储在 **wchar_t** 类型的变量中。否则，它就是一个窄字符常量（例如 'x'），此时它可以存储在 **char** 类型的简单变量中。

   字符常量可以是一个普通的字符（例如 'x'）、一个转义序列（例如 '\t'），或一个通用的字符（例如 '\u02C0'）。

   在 C++ 中，有一些特定的字符，当它们前面有反斜杠时，它们就具有特殊的含义，被用来表示如换行符（\n）或制表符（\t）等。下表列出了一些这样的转义序列码：

   | 转义序列   | 含义                       |
   | :--------- | :------------------------- |
   | \\         | \ 字符                     |
   | \'         | ' 字符                     |
   | \"         | " 字符                     |
   | \?         | ? 字符                     |
   | \a         | 警报铃声                   |
   | \b         | 退格键                     |
   | \f         | 换页符                     |
   | \n         | 换行符                     |
   | \r         | 回车                       |
   | \t         | 水平制表符                 |
   | \v         | 垂直制表符                 |
   | \ooo       | 一到三位的八进制数         |
   | \xhh . . . | 一个或多个数字的十六进制数 |

5. 字符串常量

   字符串字面值或常量是括在双引号 **""** 中的。一个字符串包含类似于字符常量的字符：普通的字符、转义序列和通用的字符。

   可以使用 **\\** 做分隔符，把一个很长的字符串常量进行分行。





# 存储类

存储类定义 C++ 程序中变量/函数的范围（可见性）和生命周期。这些说明符放置在它们所修饰的类型之前。下面列出 C++ 程序中可用的存储类：

- auto
- register
- static
- extern
- mutable
- thread_local (C++11)

从 C++ 17 开始，auto 关键字不再是 C++ 存储类说明符，且 register 关键字被弃用。

1. auto 存储类

   自 C++ 11 以来，**auto** 关键字用于两种情况：声明变量时根据初始化表达式自动推断该变量的类型、声明函数时函数返回值的占位符。

   C++98标准中auto关键字用于自动变量的声明，但由于使用极少且多余，在 C++17 中已删除这一用法。

2. register 存储类

   **register** 存储类用于定义存储在寄存器中而不是 RAM 中的局部变量。这意味着变量的最大尺寸等于寄存器的大小（通常是一个词），且不能对它应用一元的 '&' 运算符（因为它没有内存位置所以无法取内存地址）。

   寄存器只用于需要快速访问的变量，比如计数器。还应注意的是，定义 'register' 并不意味着变量将被存储在寄存器中，它意味着变量可能存储在寄存器中，这取决于硬件和实现的限制。

3. static 存储类

   **static** 存储类指示编译器在**程序的生命周期内**保持局部变量的存在，而不需要在每次它进入和离开作用域时进行创建和销毁。因此，使用 static 修饰局部变量可以**在函数调用之间保持局部变量的值**。

   static 修饰符也可以应用于全局变量。当 static 修饰全局变量时，会使变量的作用域限制在声明它的文件内。

   在 C++ 中，当 static 用在类数据成员上时，会导致仅有一个该成员的副本被类的所有对象共享。

4. extern 存储类

   **extern** 存储类用于提供一个全局变量的引用，全局变量对所有的程序文件都是可见的。当您使用 'extern' 时，对于无法初始化的变量，会把变量名指向一个之前定义过的存储位置。

   当有多个文件且定义了一个可以在其他文件中使用的全局变量或函数时，可以在其他文件中使用 *extern* 来得到已定义的变量或函数的引用。可以这么理解，*extern* 是用来在另一个文件中声明一个全局变量或函数。

   extern 修饰符通常用于当有两个或多个文件共享相同的全局变量或函数的时候

5. mutable 存储类

   **mutable** 说明符仅适用于类的对象， 它允许对象的成员替代常量。也就是说，mutable 成员可以通过 const 成员函数修改。

6. thread_local 存储类

   使用 thread_local 说明符声明的变量仅可在它在其上创建的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。

   thread_local 说明符可以与 static 或 extern 合并。

   可以将 thread_local 仅应用于数据声明和定义，thread_local 不能用于函数声明或定义。



# 基本结构

## 循环结构

一个循环内可以嵌套另一个循环。C++ 允许至少 256 个嵌套层次。

1. while循环

   只要给定的条件为真，**while** 循环语句会重复执行一个目标语句。

   ```c++
   while(condition)
   {
      statement(s);
   }
   ```

   > **statement(s)** 可以是一个单独的语句，也可以是几个语句组成的代码块。**condition** 可以是任意的表达式，当为任意非零值时都为真。当条件为真时执行循环。
   >
   > 当条件为假时，程序流将继续执行紧接着循环的下一条语句。

   *while* 循环可能一次都不会执行。当条件被测试且结果为假时，会跳过循环主体，直接执行紧接着 while 循环的下一条语句。

2. for 循环

   **for** 循环是执行特定次数的循环的重复控制结构，能多次执行一个语句序列，简化管理循环变量的代码。

   ```c++
   for ( init; condition; increment )
   {
      statement(s);
   }
   ```

   > 1. **init** 会首先被执行，且只会执行一次。这一步允许您声明并初始化任何循环控制变量。您也可以不在这里写任何语句，只要有一个分号出现即可。
   > 2. 接下来，会判断 **condition**。如果为真，则执行循环主体。如果为假，则不执行循环主体，且控制流会跳转到紧接着 for 循环的下一条语句。
   > 3. 在执行完 for 循环主体后，控制流会跳回上面的 **increment** 语句。该语句允许您更新循环控制变量。该语句可以留空，只要在条件后有一个分号出现即可。
   > 4. 条件再次被判断。如果为真，则执行循环，这个过程会不断重复（循环主体，然后增加步值，再然后重新判断条件）。在条件变为假时，for 循环终止。

   基于范围的for循环(C++11)

   ```c++
   int my_array[5] = { 1, 2, 3, 4, 5 };
   
   // 不会改变 my_array 数组中元素的值
   // x 将使用 my_array 数组的副本
   for (int x : my_array)
   {
       x *= 2;
       cout << x << endl;
   }
   
   // 会改变 my_array 数组中元素的值
   // 符号 & 表示 x 是一个引用变量，将使用 my_array 数组的原始数据
   // 引用是已定义的变量的别名
   for (int& x : my_array)
   {
       x *= 2;
       cout << x << endl;
   }
   
   // 还可直接使用初始化列表
   for (int x : { 1, 2, 3, 4, 5 })
   {
       x *= 2;
       cout << x << endl;
   }
   ```

   > 上面for述句的第一部分定义被用来做范围迭代的变量，就像被声明在一般for循环的变量一样，其作用域仅只于循环的范围。而在":"之后的第二区块，代表将被迭代的范围。

3. do...while 循环

   不像 **for** 和 **while** 循环，它们是在循环头部测试循环条件。**do...while** 循环是在循环的尾部检查它的条件。

   **do...while** 循环与 while 循环类似，但是 do...while 循环会确保至少执行一次循环。

   ```c++
   do
   {
      statement(s);
   
   }while( condition );
   ```

4. break 语句

   终止 **loop** 或 **switch** 语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。

   如果使用的是嵌套循环，break 语句会停止执行最内层的循环，然后开始执行该块之后的下一行代码。

5. continue语句

   引起循环跳过主体的剩余部分，立即重新开始测试条件。

   **continue** 语句不是强迫终止，continue 会跳过当前循环中的代码，强迫开始下一次循环。

   对于 **for** 循环，**continue** 语句会导致执行条件测试和循环增量部分。对于 **while** 和 **do...while** 循环，**continue** 语句会导致程序控制回到条件测试上。

6. goto 语句

   **goto** 语句允许把控制无条件转移到同一函数内的被标记的语句。

   goto 语句一个很好的作用是退出深嵌套例程。

   但是不建议在程序中使用 goto 语句。

   ```c++
   goto label;
   ..
   .
   label: statement;
   ```

   > **label** 是识别被标记语句的标识符，可以是任何除 C++ 关键字以外的纯文本。标记语句可以是任何语句，放置在标识符和冒号（:）后边。



## 选择结构

1. if 语句

   一个 **if 语句** 由一个布尔表达式后跟一个或多个语句组成。

   ```c++
   if(boolean_expression)
   {
      // 如果布尔表达式为真将执行的语句
   }
   ```

   如果布尔表达式为 **true**，则 if 语句内的代码块将被执行。如果布尔表达式为 **false**，则 if 语句结束后的第一组代码（闭括号后）将被执行。

   C 语言把任何**非零**和**非空**的值假定为 **true**，把**零**或 **null** 假定为 **false**。

2. if...else 语句

   一个 **if 语句** 后可跟一个可选的 **else 语句**，else 语句在布尔表达式为假时执行。

   ```c++
   if(boolean_expression)
   {
      // 如果布尔表达式为真将执行的语句
   }
   else
   {
      // 如果布尔表达式为假将执行的语句
   }
   ```

3. if...else if...else 语句

   一个 **if** 语句后可跟一个可选的 **else if...else** 语句，这可用于测试多种条件。

   当使用 if...else if...else 语句时，以下几点需要注意：

   - 一个 if 后可跟零个或一个 else，else 必须在所有 else if 之后。
   - 一个 if 后可跟零个或多个 else if，else if 必须在 else 之前。
   - 一旦某个 else if 匹配成功，其他的 else if 或 else 将不会被测试。

   ```c++
   if(boolean_expression 1)
   {
      // 当布尔表达式 1 为真时执行
   }
   else if( boolean_expression 2)
   {
      // 当布尔表达式 2 为真时执行
   }
   else if( boolean_expression 3)
   {
      // 当布尔表达式 3 为真时执行
   }
   else 
   {
      // 当上面条件都不为真时执行
   }
   ```

4. switch 语句

   一个 **switch** 语句允许测试一个变量等于多个值时的情况。每个值称为一个 case，且被测试的变量会对每个 **switch case** 进行检查。

   ```c++
   switch(expression){
       case constant-expression  :
          statement(s);
          break; // 可选的
       case constant-expression  :
          statement(s);
          break; // 可选的
     
       // 您可以有任意数量的 case 语句
       default : // 可选的
          statement(s);
   }
   ```

   - **switch** 语句中的 **expression** 必须是一个整型或枚举类型，或者是一个 class 类型，其中 class 有一个单一的转换函数将其转换为整型或枚举类型。
   - 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号。
   - case 的 **constant-expression** 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量或字面量。
   - 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 **break** 语句为止。
   - 当遇到 **break** 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行。
   - 不是每一个 case 都需要包含 **break**。如果 case 语句不包含 **break**，控制流将会 *继续* 后续的 case，直到遇到 break 为止。
   - 一个 **switch** 语句可以有一个可选的 **default** case，出现在 switch 的结尾。default case 可用于在上面所有 case 都不为真时执行一个任务。default case 中的 **break** 语句不是必需的。

5. ? : 运算符

   ```c++
   Exp1 ? Exp2 : Exp3;
   ```

   ? 表达式的值是由 Exp1 决定的。如果 Exp1 为真，则计算 Exp2 的值，结果即为整个 ? 表达式的值。如果 Exp1 为假，则计算 Exp3 的值，结果即为整个 ? 表达式的值。



# 函数

 函数是一组一起执行一个任务的语句。每个 C++ 程序都至少有一个函数，即主函数 **main()** ，所有简单的程序都可以定义其他额外的函数。

函数**声明**告诉编译器函数的名称、返回类型和参数。函数**定义**提供了函数的实际主体。

C++ 标准库提供了大量的程序可以调用的内置函数。例如，函数 **strcat()** 用来连接两个字符串，函数 **memcpy()** 用来复制内存到另一个位置。

函数还有很多叫法，比如方法、子例程或程序，等等。



## 定义

```c++
return_type function_name( parameter list )
{
   body of the function
}
```

> - **返回类型：**一个函数可以返回一个值。**return_type** 是函数返回的值的数据类型。有些函数执行所需的操作而不返回值，在这种情况下，return_type 是关键字 **void**。
> - **函数名称：**这是函数的实际名称。函数名和参数列表一起构成了函数签名。
> - **参数：**参数就像是占位符。当函数被调用时，您向参数传递一个值，这个值被称为实际参数。参数列表包括函数参数的类型、顺序、数量。参数是可选的，也就是说，函数可能不包含参数。
> - **函数主体：**函数主体包含一组定义函数执行任务的语句。



## 声明

```c++
return_type function_name( parameter list );
```

函数**声明**会告诉编译器函数名称及如何调用函数。函数的实际主体可以单独定义。

在函数声明中，参数的名称并不重要，只有参数的类型是必需的.

在一个源文件中定义函数且在另一个文件中调用函数时，函数声明是必需的。在这种情况下，应该在调用函数的文件顶部声明函数。



# 位字段

在 C++ 中，使用 | 分隔函数参数可以将多个参数作为一个参数传递给函数。这种方式传递的参数称为位字段（Bit Field），用于在一个整数中存储多个值，可以有效地节省内存空间。通常，在函数调用中使用位字段传递参数时，还需要使用结构体或联合体来定义位字段的名称和数据类型，这样才能正确地传递和解析参数。



# 特殊宏

1. `__THROW`：用于标记函数不会抛出异常。在 C 语言中，`__THROW` 不会产生任何作用，但在 C++ 中，被 `__THROW` 修饰的函数将支持 C++ 抛出异常的功能。这是因为在 C++ 中，函数可以抛出异常，但是在 C 语言中，函数不能抛出异常。`__THROW` 的定义可以在 GNU C 语言的头文件中找到，如 `include/sys/cdefs.h`，`__THROW`宏定义只在GCC下有效

   在一般C环境中此宏是没有意义的；在GNUC版本高于3.2时，库用函数属性将C函数标记为`__nothrow__`；而如果代码定义了`__cplusplus`则表示为C++代码，且GNUC版本为2.8.x，此时才有意思，为C++程序加入`throw()`以优化函数调用。

2. `__nonnull ((1))`：这是一个函数属性，用于指定函数的某些参数必须是非空指针。`__nonnull ((1))` 表示函数的第一个参数必须是非空指针。如果传入空指针到标记为非空的参数，且使用了 `-Wnonnull`，编译器会报 warning。如果不指定`nonnull`属性的参数索引号，则所有指针参数都被标记为非空。

   `__nonnull`的宏定义在`/usr/include/sys/cdefs.h`里面，如果当前版本低于3.3，则`__nonnull`实际就是`__nonnull__`属性，

3. `__wur`：这是一个函数属性，用于指定函数的返回值被使用。如果函数的返回值被忽略，编译器会发出警告。这个属性可以帮助开发者发现可能的错误，比如忘记处理函数的返回值。

   `__wur`的宏定义在`/usr/include/sys/cdefs.h`里面，在GCC版本小于3.4且`__USE_FORTIFY_LEVEL`>0时，`__wur`就是`__attribute__ ((__warn_unused_result__))`



# 特殊关键字

1. `__attribute__`是一个编译属性，用于向编译器描述特殊的标识、错误检查或高级优化。它是GNU C特色之一，系统中有许多地方使用到。`__attribute__`可以设置函数属性（Function Attribute）、变量属性（Variable Attribute）和类型属性（Type Attribute）等。



# new与delete

1. new

    1. **内存分配**：
        - `new` 操作符会调用内存分配函数，通常是 `operator new`。这个函数会从堆中分配一块足够大小的内存，以存储对象的数据。
        - `operator new` 函数可能会使用底层的系统调用，如 `malloc()` 或者 `HeapAlloc()`，来分配内存。不过，它也可能会使用其他机制，比如内存池或自定义的内存管理器。
    2. **调用构造函数**：
        - 分配到的内存被用来存储对象的数据。`new` 操作符会在分配的内存上调用对象的构造函数来初始化对象。
        - 如果对象是一个数组，`new[]` 操作符会调用每个元素的构造函数来初始化数组中的每个对象。

    举例来说，假设有这样一个代码片段：

    ```cpp
    MyClass *ptr = new MyClass();
    ```

    在底层，这个操作可能会被转换成类似以下的伪代码：

    ```cpp
    void* memory = operator new(sizeof(MyClass)); // 分配内存
    MyClass *ptr = new(memory) MyClass(); // 调用构造函数
    ```

    其中 `operator new` 是一个返回 `void*` 类型的函数，用于内存分配；`new(memory) MyClass()` 则是在分配的内存上调用了 `MyClass` 类的构造函数，实现对象的初始化。

    值得注意的是，在使用 `new` 创建对象后，程序员通常不需要手动释放内存，因为 `new` 会调用对象的析构函数，并在对象生命周期结束时自动释放内存。配对使用的是 `delete` 操作符，用于显式地释放由 `new` 分配的内存并调用对象的析构函数。

2. delete

    1. **调用对象的析构函数**：
        - 在释放内存之前，`delete` 操作符会调用对象的析构函数来进行清理工作。这个步骤确保了对象的资源得到正确地释放。
    2. **释放内存**：
        - 一旦对象的析构函数被调用，`delete` 操作符就会将分配给对象的内存释放回系统，调用内存分配函数，通常是 `operator delete`。这样，该内存就可以被重新使用，或者返回给操作系统。

    举例来说，如果有这样一段代码：

    ```cpp
    MyClass *ptr = new MyClass();
    // 使用ptr指向的对象
    delete ptr;
    ```

    在底层，这段代码可能会被转换成类似以下的伪代码：

    ```cpp
    ptr->~MyClass(); // 调用对象的析构函数
    operator delete(ptr); // 释放内存
    ```

    其中，`ptr->~MyClass()` 是调用对象 `ptr` 所指向内存中的 `MyClass` 对象的析构函数；`operator delete(ptr)` 则是释放 `ptr` 所指向的内存，使其能够被系统回收。

    需要注意的是，如果使用 `new[]` 来分配数组，应该使用 `delete[]` 来释放对应的内存，以确保所有元素的析构函数被正确调用，并且释放的内存大小正确匹配数组的大小。



# STL

## unordered_map

1. 头文件：`<unordered_map>`

2. ```cpp
    std::unordered_map<int, std::string> mp;
    std::unordered_map<int, vector<int>> mp;
    ```

3. 遍历

    1. 使用迭代器遍历：

    ```cpp
    #include <unordered_map>
    #include <iostream>
    
    int main() {
        std::unordered_map<int, std::string> myMap = {{1, "One"}, {2, "Two"}, {3, "Three"}};
        
        // 使用 auto 关键字声明迭代器
        for (auto it = myMap.begin(); it != myMap.end(); ++it) {
            std::cout << "Key: " << it->first << ", Value: " << it->second << std::endl;
        }
        
        return 0;
    }
    ```

    在这个例子中，我们使用 `begin()` 和 `end()` 函数获取 `unordered_map` 的起始和结束迭代器，并在循环中逐个迭代访问每对键值对。

    1. 使用范围循环（C++11 以上）：

    ```cpp
    #include <unordered_map>
    #include <iostream>
    
    int main() {
        std::unordered_map<int, std::string> myMap = {{1, "One"}, {2, "Two"}, {3, "Three"}};
        
        // 使用范围循环
        for (const auto& pair : myMap) {
            std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
        }
        
        return 0;
    }
    ```

    这种方法使用了范围循环，更加简洁直观。`const auto& pair` 表示每个元素都是一个键值对，其中 `pair.first` 是键，`pair.second` 是值。



## priority_queue

优先队列，C++默认大根堆，Python默认小根堆

`priority_queue<储存的类型,vector<储存的类型>,顶堆的类型> 容器名`

> 顶堆类型
>
> - less<储存的数据类型> 即使用大顶堆
> - greater<储存的数据类型> 即是用小顶堆

自定义数据结构时，如果要创建小堆，需要用户提供>的重载；如果要创建大堆，需要用户提供<的重载



## 升序与降序

1. priority_queue：greater<>为小根堆，less<>为大根堆
2. sort：greater<>()为降序，less<>()为升序