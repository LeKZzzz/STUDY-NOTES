#  JSON

---

> JSON（JavaScript Object Notation, JS对象简谱）是一种轻量级的**数据交换格式**。它基于 ECMAScript（European Computer Manufacturers Association, 欧洲计算机协会制定的js规范）的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 JSON 成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。
>
> JSON的全称是”JavaScript Object Notation”，意思是JavaScript对象表示法，它是一种**基于文本，独立于语言**的轻量级数据交换格式，是存储和交换文本信息的语法。XML也是一种数据交换格式，为什么没有选择XML呢？因为XML虽然可以作为跨平台的数据交换格式，但是在JS(JavaScript的简写)中处理XML非常不方便，同时XML标记比数据多，增加了交换产生的流量，而JSON没有附加的任何标记，在JS中可作为对象处理，所以我们更倾向于选择JSON来交换数据。
>
> 特点：
>
> - JSON 是纯文本
> - JSON 具有"自我描述性"（人类可读）
> - JSON 具有层级结构（值中存在值）
> - JSON 可通过 JavaScript 进行解析
> - JSON 数据可使用 AJAX 进行传输
> - 没有结束标签
> - 读写的速度快
> - 能够使用内建的 JavaScript eval() 方法进行解析
> - 使用数组
> - 不使用保留字

# 语法

1. 数据在`键值对`中
2. 数据由逗号 `,` 分隔
3. 使用斜杆 `\` 来转义字符
4. 大括号 `{}` 保存对象
5. 中括号 `[]` 保存数组，数组可以包含多个对象



##	键值对

```json
key : value
```

JSON 值可以是：

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在中括号中）
- 对象（在大括号中）
- null



##	对象

1. 大括号 `{}` 保存的对象是一个**无序的键值对集合**。一个对象以左括号 `{` 开始， 右括号 `}` 结束。每个"键"后跟一个冒号`:`，多个键值对使用逗号 `,` 分隔。

2. key 必须是**字符串**，value 可以是合法的 JSON 数据类型（字符串, 数字, 对象, 数组, 布尔值或 null）。

   ```json
   { "name":"runoob", "alexa":10000, "site":null }
   ```

3. 访问方式有多种：

   1. 使用点号 `.` 来访问对象的值

      ```json
      var myObj, x;
      myObj = { "name":"runoob", "alexa":10000, "site":null };
      x = myObj.name;
      ```

   1. 使用中括号`[]`来访问对象的值

      ```json
      var myObj, x;
      myObj = { "name":"runoob", "alexa":10000, "site":null };
      x = myObj["name"];
      ```

4. 可以使用 for-in 来循环对象的属性

   ```json
   var myObj = { "name":"runoob", "alexa":10000, "site":null };
   for (x in myObj) {
       document.getElementById("demo").innerHTML += x + "<br>";
   }
   ```

5. JSON 对象中可以嵌套另外一个 JSON 对象

   ```json
   myObj = {
       "name":"runoob",
       "alexa":10000,
       "sites": {
           "site1":"www.runoob.com",
           "site2":"m.runoob.com",
           "site3":"c.runoob.com"
       }
   }
   ```

6. 可以使用 `delete` 关键字来删除 JSON 对象的属性

   ```json
   delete myObj.sites.site1;
   delete myObj.sites["site1"]
   ```

   



##	数组

1. 中括号 `[]` 保存的数组是**值（value）的有序集合**。一个数组以左中括号 `[` 开始， 右中括号 `]` 结束，值之间使用逗号 **,** 分隔。

2. 值（value）可以是双引号括起来的字符串（string）、数值(number)、true、false、 null、对象（object）或者数组（array），它们是可以嵌套的。

3. 数组可包含多个对象：

   ```json
   [
       { key1 : value1-1 , key2:value1-2 }, 
       { key1 : value2-1 , key2:value2-2 }, 
       { key1 : value3-1 , key2:value3-2 }, 
       ...
       { key1 : valueN-1 , key2:valueN-2 }, 
   ]
   ```

4. 数组可以包含其他数组

   ```json
   myObj = {
       "name":"网站",
       "num":3,
       "sites": [
           { "name":"Google", "info":[ "Android", "Google 搜索", "Google 翻译" ] },
           { "name":"Runoob", "info":[ "菜鸟教程", "菜鸟工具", "菜鸟微信" ] },
           { "name":"Taobao", "info":[ "淘宝", "网购" ] }
       ]
   }
   ```

5. 访问方法同对象的访问方法



# 工具

- Json格式化工具

    > https://www.bt.cn/tools/index.html