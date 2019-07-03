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



