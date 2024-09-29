# JavaScript

----

# 使用

---

1. `<script>`标签

    脚本可被放置与 HTML 页面的 `<body>` 或 `<head>` 部分中，或兼而有之

    > 把脚本置于 `<body>` 元素的底部，可改善显示速度，因为脚本编译会拖慢显示

2. 外部脚本

    如需使用外部脚本，需要在 `<script>` 标签的 `src` (source) 属性中设置脚本的名称

    可以在 `<head>` 或 `<body>` 中放置外部脚本引用

    外部脚本不能包含 `<script>` 标签

    在外部文件中放置脚本有如下优势：

    - 分离了 HTML 和代码
    - 使 HTML 和 JavaScript 更易于阅读和维护
    - 已缓存的 JavaScript 文件可加速页面加载

    如需向一张页面添加多个脚本文件可以使用多个 script 标签

3. 外部引用

    可通过完整的 URL 或相对于当前网页的路径引用外部脚本

    ```javascript
    <script src="/js/myScript1.js"></script>
    <script src="myScript1.js"></script>
    ```



# 输出

---

1. 使用 `window.alert()` 写入警告框

2. 使用 `document.write()` 写入 HTML 输出

    在 HTML 文档完全加载后使用 `document.write()` 将删除所有已有的 HTML

3. 使用 `innerHTML` 写入 HTML 元素

    更改 HTML 元素的 innerHTML 属性是在 HTML 中显示数据的常用方法

    `document.getElementById("id").innerHTML = "test";`

    `document.write()` 方法仅用于测试

4. 使用 `console.log()` 写入浏览器控制台



# 语法

----

1. JavaScript 语句由值、运算符、表达式、关键词和注释构成

2. 分号分隔 JavaScript 语句，如果有分号分隔，允许在同一行写多条语句，以分号结束语句不是必需的

3. JavaScript 语句可以用花括号（`{`...`}`）组合在代码块中

4. 关键词

    | 关键词        | 描述                                              |
    | :------------ | :------------------------------------------------ |
    | break         | 终止 switch 或循环。                              |
    | continue      | 跳出循环并在顶端开始。                            |
    | debugger      | 停止执行 JavaScript，并调用调试函数（如果可用）。 |
    | do ... while  | 执行语句块，并在条件为真时重复代码块。            |
    | for           | 标记需被执行的语句块，只要条件为真。              |
    | function      | 声明函数。                                        |
    | if ... else   | 标记需被执行的语句块，根据某个条件。              |
    | return        | 退出函数。                                        |
    | switch        | 标记需被执行的语句块，根据不同的情况。            |
    | try ... catch | 对语句块实现错误处理。                            |
    | var           | 声明变量。                                        |

5. 标识符

    所有 JavaScript 变量必须以唯一的名称的标识，这些唯一的名称称为标识符

    在 JavaScript 中，首字符必须是字母、下划线（-）或美元符号（$）

    连串的字符可以是字母、数字、下划线或美元符号

    数值不可以作为首字符

6. JavaScript 标识符对大小写敏感

    JavaScript 程序员倾向于使用以小写字母开头的驼峰大小写

7. JavaScript 使用 Unicode 字符集

8. 在 JavaScript 中，`null` 的数据类型是对象

    `Undefined` 与 `null` 的值相等，但类型不相等

9. NaN 的数据类型是数字
    数组的数据类型是对象
    日期的数据类型是对象
    null 的数据类型是 object
    未定义变量的数据类型为 undefined
    未赋值的变量的数据类型也是 undefined



# 变量

---

> 使用 JavaScript 的情况下，全局作用域是 JavaScript 环境。
>
> 在 HTML 中，全局作用域是 window 对象。
>
> 通过 `var` 关键词定义的全局变量属于 window 对象
>
> 通过 `let` 关键词定义的全局变量不属于 window 对象
>
> 
>
> JavaScript 拥有动态类型，这意味着相同变量可用作不同类型
>
> 
>
> 在 JavaScript 中有 5 种不同的可以包含值的数据类型：
>
> - `string`
> - `number`
> - `boolean`
> - `object`
> - `function`
>
> 有 6 种类型的对象：
>
> - `Object`
> - `Date`
> - `Array`
> - `String`
> - `Number`
> - `Boolean`
>
> 以及 2 种不能包含值的数据类型：
>
> - `null`
> - `undefined`

## var

1. JavaScript 使用 `var` 关键词来声明变量

2. JavaScript 变量是存储数据值的容器

3. 声明之后，变量是没有值的（技术上，它的值是 `undefined`）

4. 如果再次声明某个 JavaScript 变量，将不会丢它的值

5. 以在一条语句中声明许多变量

    ```js
    var person = "Bill Gates", carName = "porsche", price = 15000;
    ```

6. 字符串也可以使用加号，但是字符串将被级联

7. 如果把要给数值放入引号中，其余数值会被视作字符串并被级联

8. 通过 `var` 关键词声明的变量没有块作用域，在块 {} 内声明的变量可以从块之外进行访问

9. 在块中重新声明变量也将重新声明块外的变量

10. 通过 var 声明的变量会提升到顶端，所以可以在声明变量之前就使用它



## let

1. let关键字在 JavaScript 中提供了块作用域（*Block Scope*）变量

2. 在块 {} 内声明的变量无法从块外访问

3. 在块中重新声明变量不会重新声明块外的变量

4. 如果在循环中用 `let` 声明了变量 i，那么只有在循环内，变量 i 才是可见的

5. 在相同的作用域，或在相同的块中，通过 `let` 重新声明一个 `var` 变量是不允许的

    在相同的作用域，或在相同的块中，通过 `let` 重新声明一个 `let` 变量是不允许的

    在相同的作用域，或在相同的块中，通过 `var` 重新声明一个 `let` 变量是不允许的

    在不同的作用域或块中，通过 `let` 重新声明变量是允许的

6. 通过 `let` 定义的变量不会被提升到顶端，在声明 `let` 变量之前就使用它会导致 ReferenceError，变量从块的开头一直处于“暂时死区”，直到声明为止



## const

1. 通过 `const` 定义的变量与 `let` 变量类似，但不能重新赋值

2. `const` 变量必须在声明时赋值

3. 关键字 `const` 有一定的误导性，它没有定义常量值，它定义了对值的常量引用，因此，我们不能更改常量原始值，但我们可以更改常量对象的属性，但是您无法重新为常量对象赋值

    ```js
    const PI = 3.141592653589793;
    PI = 3.14;      // 会出错
    PI = PI + 10;   // 也会出错
    
    // 您可以创建 const 对象：
    const car = {type:"porsche", model:"911", color:"Black"};
    // 您可以更改属性：
    car.color = "White";
    // 您可以添加属性：
    car.owner = "Bill";
    ```

    > 类似C++中的指针常量，无法修改指针指向的地址，但是可以修改这个地址中的对象内容

4. 可以更改常量数组的元素，但是无法重新为常量数组赋值

    ```js
    // 您可以创建常量数组：
    const cars = ["Audi", "BMW", "porsche"];
    
    // 您可以更改元素：
    cars[0] = "Honda";
    
    // 您可以添加元素：
    cars.push("Volvo");
    ```

5. 在同一作用域或块中，不允许将已有的 `var` 或 `let` 变量重新声明或重新赋值给 `const`

    在同一作用域或块中，为已有的 const 变量重新声明声明或赋值是不允许的

    在另外的作用域或块中重新声明 `const` 是允许的

6. 通过 `const` 定义的变量不会被提升到顶端，`const` 变量不能在声明之前使用



# 事件

---

> HTML 事件可以是浏览器或用户做的某些事情。
>
> 下面是 HTML 事件的一些例子：
>
> - HTML 网页完成加载
>
> - HTML 输入字段被修改
> - HTML 按钮被点击
>
> 通常，当事件发生时，用户会希望做某件事，JavaScript 允许您在事件被侦测到时执行代码。
>
> 通过 JavaScript 代码，HTML 允许您向 HTML 元素添加事件处理程序。

1. `<element event="一些 JavaScript">`

2. | 事件        | 描述                         |
    | :---------- | :--------------------------- |
    | onchange    | HTML 元素已被改变            |
    | onclick     | 用户点击了 HTML 元素         |
    | onmouseover | 用户把鼠标移动到 HTML 元素上 |
    | onmouseout  | 用户把鼠标移开 HTML 元素     |
    | onkeydown   | 用户按下键盘按键             |
    | onload      | 浏览器已经完成页面加载       |
