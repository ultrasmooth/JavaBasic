#   Day12

#### 获得Class 对象的三种方式

* 方式一：通过类名.class 获取
  * Class c = Student.class;



* 方式二：通过Object类的成员方法getClass()方法获取
  * Class c = stu.getClass();



* 方式三：通过Class.forName("全限定类名")方法获取
  * Class c = Class.forName("java.lang.String");





#### Class对象的相关方法

```java
String getSimpleName();获取简单类名，只是类名，没有包
String getName()；获取完整类名，包含包名+类名
```



## 获取Class 对象的Constructor信息

#### Constructor类概述

* Constructor 是构造方法类，类中的每一个构造方法都是Constructor的对象，通过Constructor对象可以实例化对象

#### Class类中与Constructor相关的方法

```java
//1. Constructor getConstructor(Class...parameterTypes)
//根据参数类型获取构造方法对象，只能获得public修饰的构造方法。
//如果不存在对应的构造方法，会抛出java.lang.NoSuchMethodException异常

//2.Constructor getDeclaredConstructor(Class...parameterTypes)
//根据参数类型获取构造方法对象，包括private修饰的构造方法
//如果不存在对应的构造方法，则会抛出 java.lang.NoSuchMethodExcdeption异常

//3.Constructor[] getConstructors()
//获取所有的public修饰的构造方法

//4.Constructor[] getDeclaredConstructors()
//获取所有构造方法，包括private修饰的
```



## 元注解

#### @Target

* 作用：用来标识注解的使用位置
  value属性值定义在ElementType枚举类中，常用值如下：
  TYPE            注解可以作用在类和接口上
  FIELD           注解可以作用在成员变量上
  METHOD      注解可以作用在成员方法上
  PARAMETER      注解可以作用在方法参数上
  CONSTRUCTOR   注解可以作用在构造方法上
  //使用方法例子
  @Target({ElementType.METHOD,ElementType.TYPE})

#### @Retention

* 作用: 用来标识注解的生命周期(有效范围)
* 源码阶段:注解只存在源码中,编译产生的Class文件中就不存在了,
* 字节码阶段:注解在源码中,字节码文件中都存在,运行阶段就不存在了,默认值
* 运行时阶段:注解存在三个阶段:源码,字节码,运行时

```java
//Value属性值定义RetentionPolicy枚举中,可用值如下:
	SOURCE
	CLASS
	RUNTIME
```

