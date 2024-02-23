# Ajax

---

> 定义：Asynchronous JavaScript And XML，异步的JavaScript和XML，AJAX 并非编程语言。
>
> AJAX 仅仅组合了：
>
> - 浏览器内建的 XMLHttpRequest 对象（从 web 服务器请求数据）
> - JavaScript 和 HTML DOM（显示或使用数据）
>
> 作用:
>
> - 数据交换:通过Ajax可以给服务器发送请求，并获取服务器响应的数据。
> - 异步交互:可以在不重新加载整个页面的情况下，与服务器交换数据并更新部分网页的技术，如:搜索联想、用户名是否可用的校验等等。



# 使用

```js
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
```

