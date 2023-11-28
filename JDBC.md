# JDBC

---

> JDBC(Java DataBase Connectivity ，Java 数据库连接)，即使用Java语言操作关系型数据库的一套API
>
> 本质：
>
> - 官方(sun公司)定义的一套操作所有关系型数据库的规则，即接口
> - 各个数据库厂商去实现这套接口，提供数据库驱动jar包
> - 我们可以使用这套接口(JDBC)编程，真正执行的代码是动iar包中的实现类
>
> 优势：
>
> - 各数据库厂商使用相同的接口，Java代码不需要针对不同数据库分别开发
> - 可随时替换底层数据库，访问数据库的Java代码基本不变

# 基础操作

---

## 导入驱动

将数据库对应驱动导入项目中，将jar包添加为库



## 注册驱动

```java
Class.forName("class_path");
```

> - **class_path**
>   - MySQL：`"com.mysql.jdbc.Driver"`



## 获取连接

```java
import java.sql.DriverManager;
import java.sql.Connection;
Connection conn = DriverManager.getConnection(url, username, password);
```

> - **url**
>   - MySQL：`“jdbc:mysql://host:port/db_name”`



## 定义SQL语句

```java
String sql_name = "statement";
```

> 字符串中不需要添加结束符“**;**”



## 获取执行SQL对象

```java
import java.sql.Statement;
Statement stmt = conn.createStatement();
```



## 执行SQL

```java
ResultSet result = stmt.executeQuery(sql);	//查询语句
int result = stmt.executeUpdate(sql);	//更新语句
stmt.execute(sql);
```



## 处理返回结果

```java
//查询
while(result.next()){
    statement;
}
```



## 释放资源

```java
stmt.close();
conn.close();
```

> 需要先关闭执行SQL对象再关闭连接



# DriverManager

---

> 驱动管理类作用
>
> - 注册驱动
> - 获取数据库连接

1. 注册驱动

   ```java
   Class.forName("class_path");
   ```

   > MySQL 5之后的驱动包可以省略注册驱动的步骤，其会自动加载jar包中META-INF/services/java.sql.Driver文件中的驱动类

2. 获取连接

   ```java
   DriverManager.getConnection(url, username, password);
   ```

   > - **url**
   >   - MySQL
   >     - `jdbc:mysql://ip地址(域名):端口号/数据库名称?参数键值对1&参数键值对2...`
   >     - 如果连接的是本机mysq服务器，并且mysql服务默认端口是3306，则url可以简写为: jdbc:mysql:///数据库名称?参数键值对
   >     - 配置 useSSL=false 参数，禁用安全连接方式，解决警告提示
   >   - PostgreSQL
   >     - `jdbc:postgresql://host:port/postgres`
   > - **user**：用户名
   > - **passwor**：密码

# Connection

---

> 数据库连接对象作用：
>
> - 获取执行SQL的对象
> - 管理事务

1. 获取执行SQL的对象

   - 普通的执行SQL对象

     ```java
     Statement createStatement()
     ```

   - 预编译SQL的执行SQL对象：防止SQL注入

     ```java
     PreparedStatement prepareStatement(sql)

   - 执行存储过程的对象

     ```java
     CallableStatement prepareCall(sql)
     ```

2. 事务管理

   ```java
   setAutoCommit(boolean)	// 开启(true)|关闭(false) 自动提交事务
   commit()	// 提交事务
   rollback()	// 回滚事务

# Statement

---

执行SQL语句

1. 执行DML/DDL语句

   ```java
   int executeUpdate(sql)
   ```

   > **返回值**
   >
   > - DML语句影响的行数
   > - DDL语句执行后，执行成功也可能返回0

2. 执行DQL语句

   ```java
   ResultSet executeQuery(sql)

# PreparedStatement

---



# CallableStatement

---



# ResultSet

---

> 封装了DQL语句的查询结果

1. `next()`：将光标从当前位置向前移动一行，判断当前行是否为有效行

   返回值：true(有效行，当前行有数据) | false(无效行，当前行没数据)

2. ```java
   String getString(arg)
   int getInt(arg)
   ```

   > **arg**
   >
   > - int：列的编号，从1开始
   > - String：列名