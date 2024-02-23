# Axios

---

> Axios 是一个基于 promise 网络请求库，作用于 node.js和浏览器中。它是 isomorphic 的(即同-套代码可以运行在浏览器和node.js中)。在服务端它使用原生 node.js的http模块, 而在客户端 (浏览端)则使用XMLHttpRequests。
>
> Axios 对原生的Ajax进行了封装，简化书写，快速开发。

# 引入

```js
<script src="js/axios-0.18.0.js"></script>
```



# 使用

1. ```js
        axios({
            method: "get",
            url: "xxx"
        }).then((result) => {
    
        });
    ```

2. ```js
    axios.get(url [, config])
    axios.delete(url [, config])
    axios.post(url [, data[, config]])
    axios.put(url [, data[, config]])
    ```

3. 

