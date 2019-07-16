# day17

## sql注入

## preparedStatement

PreparedStatement 的作用，进行增删改查

> perpareStatement(String sql)获得PreparedStatement对象，

* 常用方法

```
int executeUpdate();
Resultset executeQuery();
```

* 使用方法

```
使用方法 
//未知内容使用？

```

* 优点
  * 可读性好

## 连接池

* 创建配置文件
  * 文件名要求，必须是c3p0-config.xml
* 文件位置要放在src文件下
* 在配置文件
  * ==数据库连接参数==
  * 连接池参数
    * 初始连接数5
    * 最大连接数 10
    * 最大等待时间 3000毫秒
    * 对打空闲时间
  * 