#	简介

1. Qt概述
   QT是一个跨平台的C++图形用户界面库，由挪威TrollTech公司出品，目前包括Qt Creator， QtEmbedded，Qt Designer快速开发工具，Qt Linguist国际化工具等部分，Qt支持所有Linux/Unix系统，还支持Windows平台、Mac平台等等。

2. Qt优点

   Qt是一个跨平台的C++图形用户界面应用程序框架，提供给应用程序开发者建立艺术级的图形用户界面所需的所用功能。Qt很容易扩展，并且允许真正地组件编程。Qt与GTK、KDE、MFC，OWL，VCL，ATL是一样的图形界面库。

   QT优点如下：

   1. **优良的跨平台特性**

      Qt支持下列操作系统: Microsoft Windows，Linux，Solaris， SunOS， HP-UX， Digital UNIX (OSF/1，Tru64)，Irix，FreeBSD，BSD/OS，SCO，AIX，OS390，QNX等等。

   2. **面向对象**

      Qt的良好封装机制使得Qt的模块化程度非常高，可重用性较好，对于用户开发来说非常方便。 Qt提供了一种称为signals/slots的安全类型来替代 callback，使得各个元件之间的协同工作变得十分简单。

   3. **丰富的API**

      Qt包括多达250个以上的C++类，还提供基于模板的collections， serialization，file，I/O device，directory management，date/time类。

   4. **支持2D/3D图形渲染，支持OpenGL**

   5. **大量的开发文档**

   6. **XML、JSON支持等等**

3. Qt相关工具

   QT开发工具包含Qt Creator、Qt Designer、Qt Linguist、Qt Assistant、Qmake、CMake等等。

   1. **Qt Creator**

      Qt Creator是用于Qt开发的轻量级跨平台集成开发环境。

   2. **Qt Designer**

      Qt Designer是强大的拖曳式图形化用户界面排版和设计工具。

      Qt Designer功能如下：

      A、支持表单和对话框的创建，可即时预览
      B、与Qt版面系统集成
      C、宏大的标准widgets集
      D、支持客户定制的widgets和对话框
      E、与Microsoft Visual Studio .NET无缝集成

      Qt Designer优势如下：

      A、大大加快了界面的设计过程
      B、支持所有平台上的本地外观感觉
      C、开发者能在自行选择的工作环境内充分发挥其现有技能

   3. **Qt Linguist**

      Qt Linguist一整套工具，支持对Qt应用作快捷无误的翻译，是一组能理顺国际化工作流的工具。

      Qt Linguist功能如下：

      A、采集所有的用户界面文本并以一个简洁的窗口将其展现给人工译者
      B、支持所有语言
      C、从单一应用的二进制程序内部提供同时多语言支持及同时多写入系统

      Qt Linguist优势如下：

      A、大大加快了翻译/本地化进程
      B、与Qt的语言敏感排版引擎协同，以创建与语言不相关的简洁一致的界面
      C、轻松应对国际市场

   4. **4 Qt Assistant**

      Qt Assistant是可定制可重发布的帮助文件和文档阅读器。

      Qt Assistant功能如下：

      A、简单明快的web浏览器般导航、书签和文档文件连接
      B、支持富文本HTML
      C、全文本关键词查阅
      D、可定制并随Qt供应

      Qt Assistant优势如下：

      A、无需再从头开始构建帮助系统
      B、充分利用现有的HTML技能
      C、以方便搜寻和导航的格式向最终用户提供文档

   5. **QMake**

      Qmake跨平台makefile生成器。

      Qmake功能如下：

      A、读取工程源码，生成依赖关系树，生成平台相关工程和makefiles
      B、与Visual Studio及Xcode集成

      Qmake优势如下：

      A、无需担忧跨平台编译
      B、降低对makefile手工构建的需求度

   6. **CMake**

      CMake是一个跨平台的安装（编译）工具，可以用简单的语句来描述所有平台的安装(编译过程)。他能够输出各种各样的makefile或者project文件，能测试编译器所支持的C++特性,类似UNIX下的automake。只是 CMake 的组态档取名为 CMakeLists.txt。Cmake 并不直接建构出最终的软件，而是产生标准的建构档（如 Unix 的 Makefile 或 Windows Visual C++ 的 projects/workspaces），然后再依一般的建构方式使用。这使得熟悉某个集成开发环境（IDE）的开发者可以用标准的方式建构他的软件，这种可以使用各平台的原生建构系统的能力是 CMake 和 SCons 等其他类似系统的区别之处。



#	Qt Widgets、QML、Qt Quick

1. **基础窗口控件QWidget 类是Qt所有用户界面对象的基类，所有的窗口和控件都直接或间接继承自QWidget类。**

   - QWidget 是用户界面的原子：它从窗口系统接收鼠标、键盘和其他事件，并在屏幕上绘制自己的表示。每个小部件都是矩形的，它们按Z顺序排序。小部件由其父部件和它前面的小部件剪裁。
   - 窗口控件（Widget，简称“控件”)是在PyQt中建立界面的主要元素。一般窗口都有边框、标题栏。窗口是指程序的整体界面，可以包含标题栏、菜单栏、工具栏、关闭按钮、最小化按钮、最大化按钮等;控件是指按钮、复选框、文本框、表格、进度条等这些组成程序的基本元素。一个程序可以有多个窗口，一个窗口也可以有多个控件。
   - 未嵌入父窗口小部件的 QWidget 称为窗口。通常，窗口有边框和标题栏。
   - QWidget 的一些没有直接使用。例如，QWidget有一个字体属性，但从不使用它。而是由其子类使用。
   - 在实现一个新的小部件时，重新实现sizeHint()为小部件提供一个合理的默认大小并使用setSizePolicy()设置正确的大小策略是很有用的。大小策略为布局管理系统提供良好的默认行为。默认大小策略指示size提示表示小部件的首选大小。
   - 小部件响应通常由用户操作引起的事件。Qt通过使用包含每个事件信息的QEvent子类实例调用特定的事件处理函数，将事件传递给小部件由小部件处理。
   - QWidget使用双缓冲绘制，因此不需要在paintEvent()中编写双缓冲代码来避免闪烁。

2. QML 是一种**用户界面规范和标记语言**，它允许开发/设计人员创建高性能、流畅的动画和具有视觉吸引力的应用程序。

   这里，主要涉及两点：

   1. 用户界面规范：QML提供了一种高度可读的、声明式的、类似 JSON 的语法，支持命令式 JavaScript 表达式和动态属性绑定。
   2. 标记语言：像 C++ 一样，QML 也是一种语言，它的文件以 .qml 结尾。

3. Qt Quick 是 **QML 类型和功能的标准库**，它包括视觉类型、交互类型、动画、模型和视图、粒子效果和着色效果（可以使用 import 语句访问所有这些功能）。

   Qt Quick 使用 QML 作为声明语言，来设计以用户界面为中心的应用程序。严格来讲，Qt Quick 是一个用于 QML 的工具包，允许以 QML 语言来开发图形界面。当然，还有其他的工具包用于 QML：

   - 图形化的（例如：Sailfish Silica 或 BlackBerry Cascades）
   - 非图形的（例如：QBS - QMake/CMake/make ... 的一个替代品）

#	Qt Creater

---

> Qt Creator是跨平台的集成开发环境（IDE），旨在为开发者带来最好的体验。 Qt Creator可在Windows、Linux和macOS桌面操作系统上运行，并允许开发人员在桌面、移动和嵌入式平台创建应用程序。
>
> 它大大简化了Qt开发，可以原生创建QT应用程序（带有Qt引擎的C++），并且允许我们创建和编辑源代码，调试应用程序等。除此之外，可以在Qt Creator中打开.ui文件或.qml文件，然后进行编辑并创建Qt/C++应用程序。
>
> Qt Designer是一个图形工具，可以构建QWidget GUI，Qt Quick Designer与之类似，只是用于构建QML GUI，而两者都内置在Qt Creator中。

##	Qt Quick Designer

> Qt Quick Designer是用于以Qt QML（一种类似于CSS和JavaScript的多范式语言）编写文件的所见即所得的编辑器。 它可以帮助您从头开始或基于现成的UI控件快速设计和构建Qt Quick应用程序和组件。
>
> 通常说Qt Quick Designer允许编辑QML文件（.qml），但是现在它已集成在Qt Creator中。



##	Qt Designer

> Qt Designer是一个功能强大的跨平台GUI布局和表单生成器。 您可以用带有传统C++ Qt API的屏幕表单快速设计和构建小部件和对话框。
>
> Qt Designer是用于使用Qt小部件文件（.ui，实质上是XML格式的文件）设计和构建图形用户界面（GUI）的Qt工具，可以按所见即所得（WYSIWYG）的方式编写和自定义窗口或对话框，并使用不同的样式和分辨率对其进行测试。
>
> 它也可用于编辑Qt、C++应用程序的任何（.ui）文件，但是由于它仅允许编辑图形内容（而非C++逻辑），因此它非常受限制。

1. 修改checkbox尺寸

   ```
   ui->checkBox->setStyleSheet("QCheckBox::indicator {width: 27px; height: 27px;}");
   ```

   







#	Qt Design Studio

---

> Qt Design Studio is **UI构成工具**，能将设计愿景转化为功能性产品 —— 它是一切汇集的地方。它也是通过动画、切换、3D和视觉效果为UI设计增添额外视觉魔法的绝佳工具。
>
> QT Quick Designer从新版本Qt6开始该功能默认被禁用，qt打算未来QT Quick Designer和Qt Creator分离，目标就是设计ui的可以只用Qt Design Studio，最终该功能会被下线，由Qt Design Studio承担此重任。
>
> 单概括其功能就是让UI设计转换为qml，为工程师所用，并且可以与Photoshop集成。

##	向导预设

| 类型        | 向导预设                                                     | 描述                                                         |
| :---------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| General     | Empty                                                        | 创建使用默认组件(如矩形、图像和文本)的项目。您可以在所有目标平台上运行该应用程序。 |
| 3D          | 创建使用默认和3D组件(如相机、灯光、3D模型和材料)的项目。     |                                                              |
| Qt for MCUs | MCU                                                          | 创建一个应用程序，使用默认组件的子集(如Qt支持的MCU)，您可以部署，运行和调试MCU板。 |
| Mobile      | Scroll                                                       | 创建一个使用Qt Quick控件实现可滚动列表的应用程序。           |
| Stack       | 创建一个应用程序，使用Qt Quick控件实现一组基于堆栈的导航模型的页面。 |                                                              |
| Swipe       | 创建一个使用Qt Quick控件实现可滑动屏幕的应用程序。           |                                                              |
| Desktop     | Launcher                                                     | 创建使用默认组件(如矩形、图像和文本)的项目，并定义启动程序。 |



##	使用项目向导

创建一个新项目:

- 选择File > New Project
- 在“Presets”选项卡中，选择向导预设。
- 在Details选项卡中:
   - 为项目输入一个名称。请记住，以后不能轻易地重命名项目。
   - 选择项目文件的路径。稍后您可以移动项目文件夹。
   - 设置桌面或设备界面预览的屏幕分辨率。这决定了屏幕的大小。您可以稍后在属性中更改屏幕大小。
   - 选择“Use Qt Virtual Keyboard”允许用户使用虚拟键盘输入文本。
   - 在Target Qt Version中，选择用于开发应用程序的Qt版本。虽然您可以稍后在项目的运行设置中更改Qt版本，但请记住这两个版本不是完全兼容的。
- 在“Style”选项卡中，选择要使用的预定义UI样式之一。
- 选择Create以创建项目。

Qt Design Studio创建以下文件和文件夹:

- .qmlproject项目文件定义项目文件夹中的所有组件、JavaScript和图像文件属于项目。因此，您不需要单独列出项目中的所有文件。
- .qml文件定义组件的功能和外观。
- Screen01.ui.qml定义了一个可以在表单编辑器中编辑的自定义组件。
   默认情况下，这是项目中的主文件，但是您可以在.qmlproject文件中更改它。虽然自定义组件对于新用户来说是一个很好的起点，但您不必使用它。特别是，如果您使用Qt Bridge导出和导入设计，那么您的主文件很可能被称为其他文件。
- CMakeLists.txt项目配置文件，允许您与开发人员共享您的项目作为一个完全工作的c++应用程序。
- qtquickcontrols2.conf文件指定首选的样式和一些特定于样式的参数。
- fonts文件夹包含已添加到库>资产中的字体文件。
- imports文件夹中包含一个Constants.qml文件，它为Arial字体和屏幕分辨率指定一个字体加载器。默认Screen.ui.qml矩形的大小应该设置为width: Constants.width & height: Constants.height ，以便它继承这里保存的全局分辨率。
- qmldir模块定义文件声明了Constant组件。

要在UI中使用JavaScript和图像文件，请选择Library > Assets > ➕。



##	向项目中添加文件

还可以使用向导模板向项目添加单个文件。

在Qt Quick Controls类别中的向导模板创建Qt Quick Controls模块中组件的可样式版本。您可以创建以下类型的文件:

| 类型              | 向导模板                                                     | 描述                                                         |
| :---------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| Qt Quick Files    | Flow Item and Flow View                                      | 生成可用于设计应用程序流的组件。                             |
| Qt Quick File     | 生成一个组件，使用以下默认组件或定位符作为根组件:项目、矩形、图像、边框图像、可伸缩、行、列、流或网格。 |                                                              |
| Qt Quick UI File  | 生成一个UI文件，其中一个组件作为根组件。                     |                                                              |
| Qt Quick Views    | 生成网格视图或列表视图。                                     |                                                              |
| Qt Quick Controls | Custom Button                                                | 创建带有文本标签的按钮。                                     |
| Custom CheckBox   | 创建一个复选框。                                             |                                                              |
| Custom Dial       | 创建一个旋钮。                                               |                                                              |
| Custom Slider     | 创建一个滑块。                                               |                                                              |
| Custom SpinBox    | 创建一个旋转框。                                             |                                                              |
| Custom Switch     | 创建具有开和关状态的开关。                                   |                                                              |
| Pane              | 提供与UI样式和主题匹配的背景。                               |                                                              |
| StackView         | 提供基于堆栈的导航模型。                                     |                                                              |
| SwipeView         | 允许用户通过横向滑动来导航页面。                             |                                                              |
| QML Files         | ListModel                                                    | 向项目添加列表模型。                                         |
| JavaScript        | JavaScript File                                              | 生成可用于编写应用程序逻辑的文件。这对于在开发人员用c++实现应用程序逻辑之前测试应用程序是很有用的。 |





#	信号与槽函数

> 信号（Signal）和槽（Slot）是Qt中的核心机制，也是在PyQt编程中对象之间进行通信的机制。在Qt中，每一个QObject对象和PyQt中所有继承自QWidget的控件都支持信号与槽机制。当信号发射时，连接的槽函数将会自动执行。通过object.signal.connect()方法连接。

1. 一个信号可以连接多个槽
2. 一个信号可以连接另外一个信号
3. 信号参数可以是任何Python类型
4. 一个槽可以监听多个信号
5. 信号与槽的连接方式可以是同步连接，也可以是异步连接。
6. 信号与槽的连接可能会跨线程
7. 信号可能会断开
