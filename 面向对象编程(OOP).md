#	面向对象编程

---

> OO技术主要包括三种领域：
>
> 1. 面向对象分析(object oriented analysis, OOA)
> 2. 面向对象设计(object oriented design, OOD)
> 3. 面向对象编程(object oriented programming, OOP)

- 从语言实现层面来看，对象封装了代码和数据
- 从规格层面讲，对象是一系列可被使用的公共接口
- 从概念层面讲，对象是某种拥有责任的抽象

#	基本特征

---

##	封装性

1. 封装(encapsulation)是将对象的状态(属性)和行为(方法)结合成一个独立的系统单位，并尽可能地隐藏对象的内部细节
2. 封装使一个对象形成两个部分：接口部分和实现部分。对用户来说，接口部分是可见的，而实现部分是不可见的
3. 封装提供了两种保护：
   1. 保护对象，放置用户直接存取对象的内部细节
   2. 保护客户端，防止对象实现部分的改变可能产生的副作用，即实现部分的改变不会影响到客户端的改变
4. 在对象中，代码或数据对该对象来说都可以是私有的(private)或公有的(public)或保护的(protected)，私有代码和数据仅能被对象本身的其他部分引用，不能被该对象外的任何程序所访问；当代码或数据是公有的时，虽然它们定义在对象中，但程序的其他部分也可以访问；当代码或数据是保护的时，它们只能在该类和该类的派生类的中被访问



##	继承性

1. 继承(inheritance)是一个对象获得另一个对象属性的过程
2. 继承的重要性在于它支持层级结构类的概念，如果使用继承则对象只需要定义自己特有的属性，而基本属性则可以从父类继承
3. 继承性体现了类之间是一种(IS-A)关系，类之间的关系还有组合、关联等



##	多态性

1. 多态(polymorphism)是指一个程序中相同的名字表示不同含义的情况，即同一个接口不同的实现
2. 面向对象程序中的多态有多种情况：
   1. 静态多态：在同一个类中定义了多个名称相同的方法，即方法重载
   2. 动态多态：在子类中定义与父类中的方法同名的方法，即方法覆盖





#	OOP的优势

---

1. 易维护(maintainability)

   采用OOP方法可以很容易地使程序模块化，这种模块化极大地减少了维护的问题

2. 可重用(resusability)

   可重用是指之前写好的代码可以被代码的创建者或需要该代码功能的其他人重用，可重用性不仅适用于重用类和其他类型的代码，在OOP系统中设计应用程序时，针对OOP设计问题的解决方案也可以重用，这些解决方案称为设计模式

3. 可扩展(extensibility)

   可拓展是指一种软件在投入使用之后，其功能可以被扩展或增强，在OOP中，可扩展性主要通过继承来实现
   
4. 对变化的适应性

   隔离变化，将变化带来的影响减为最小



# 设计原则

---

## 依赖倒置原则(DIP)

- 高层模块(稳定)不应该依赖于低层模块(变化)，二者都应该依赖于抽象(稳定)
- 抽象(稳定)不应该依赖于实现细节(变化)，实现细节应该依赖于抽象(稳定)



## 开放封闭原则(OCP)

- 对扩展开放，对更改封闭
- 类模块应该是可扩展而不可修改的



## 单一职责原则(SRP)

- 一个类应该仅有一个引起它变化的原因
- 变化的方向隐含着类的责任



## Liskov替换原则(LSP)

- 子类必须能够替换它们的基类(IS-A)
- 继承表达类型抽象



## 接口隔离原则(ISP)

- 不应该强迫客户程序依赖它们不用的方法
- 接口应该小而完备



## 优先使用对象组合而不是类继承

- 类继承通常为“白箱复用“，对象组合通常为"黑箱复用"
- 继承在某种程度上破坏了封装性，子类父类耦合度高
- 而对象组合则只要求被组合的对象具有良好定义的接口，耦合度低



## 封装变化点

- 使用封装来创建对象之间的分界层，让设计者可以在分界层的一侧进行修改，而不会对另一侧产生不良的影响，从而实现层次间的松耦合 



## 针对接口编程而不是针对实现编程

- 不将变量类型声明为某个特定的具体类，而是声明为某个接口
- 客户程序无需获知对象的具体类型，只需要知道对象所具有的接口
- 减少系统中各部分的依赖关系，从而实现“高内聚、松耦合"的类型设计方案





# 个人理解

面向对象设计实现了代码之间的解耦，将众多的条件判断语句分离为一个个独立的对象，每个对象是独立的个体，对对象的改变(变化)不影响已有的逻辑(稳定)，在接口稳定的情况下可以实现变化的结果，使其满足上述的设计原则，在软件开发过程中具有重要意义。
