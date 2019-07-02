# Day01
## API概述
全称：Application Programming Interface
使用步骤：
* 查询帮助文档查看类说明信息
* 创建类的对象
* 使用对象：
* 对象名.方法()
* 对象名.成员变量名()
## 工具类
* 有些类没有构造方法，但一般有静态方法，可直接通过类名调用，这种类成为工具类。
	
## Object类-（两个常用方法）
* 特点：Object是所有类的父类
* toString()方法
```
作用：返回该对象的字符串表示
目的：在打印对象时不想看到对象在内存中的地址值，而希望看到对象的内容（成员变量名和值）
默认格式：包名.类名@对象在内存中的地址值---类全名字符串@对象在内存中的地址值		
重写toString()的写法：自动生成	
```

  * equals方法
```
作用：
	判断两个对象是否相同，相同返回true，不同返回false
	默认是通过比较两个对象的地址值判断对象是否相同
“==”的作用:
	对于基本数据类型，是比较两个变量的值
	对于引用数据类型，是比较两个对象的地址值
重写equals方法注意事项：
    1.需要使用instanceOf进行判断，否则有可能出现ClassCastException
    2.需要进行转型，例如：Student s2 = (Student)obj;
重写equals方法的目的：
	不希望通过地址值判断两个对象是否相同，而是希望通过判断对象的成员变量的值是否相同	
重写equals方法的写法：自动生成	
```

## Objects类 --三个常用的方法
    static boolean isNull(Object obj)---判断对象是否为空，空返回true
    static boolean nonNull(Object obj)--判断对象是否不为空，不为空返回true
    static boolean equals(Object a , Object b) --判断两个对象是否相同，相同返回true 
    ==Objects.equals(object a, Object b)可以容忍a为null==

## date类
* Date类的构造方法	 
	Date()---创建日期对象，当前系统时间
	Date(long time)---根据毫秒值创建日期对象

* Date类常用成员方法
	long getTime()-----返回1970-1-1 00:00:00 至今的毫秒值
	--->1 秒 = 1000 毫秒
	
## DateFormat类-改变日期的显示格式
* DateFormat是抽象类，不能直接实例，需要使用其子类SimpleDateFormat，调用父类方法
* SimpleDateFormat构造方法设置日期pattern

  > new SimpleDateFormat("YYYY-MM-dd");      

* 常用方法
  > String format (Date d);父类方法
  > parse（String pattern);
	
* 练习一：
```java
/*将Date转成"2018年9月15日 19时18分19秒" 格式
        步骤1：创建日期对象
		步骤2：创建DateFormat子类对象：
		步骤3：调用DateFormat的方法--format(Date d)
*/
		Date date = new Date();
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH时:mm分:ss秒");
		String dateStr = sdf.format(date);
```
* 练习二
```java
	/*  将字符串"2017-12-26 10:13:31"转成Date
	    步骤1：创建日期格式化对象并指定日期模式：日期模式必须和日期字符串的格式一致
	    步骤2：调用日期格式化对象的parse方法传递字符串，获得日期对象
	*/
	    String str = "2017-12-26 10:13:31"	;
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
		Date date = sdf.parse(str);//parse方法可能会导致异常，所以咬字啊main方法后面抛异常
```
## Calendar类
* Date缺陷：
    Date类对单独获取年月日时分秒，加减运算不好处理；而且Date类不支持国际化

* 创建Calendar类
       *Calendar类是一个抽象类，不能直接创建对象，只能使用子类对象 
       *通过Calendar类提供的静态方法getInstance获得日历对象

* Calendar类常用的方法：
       int get(int field)-----根据日历字段获得对应的字段信息
       void set(int field,int value)--将指定日历字段的值修改为指定的值
       void add(int filed , int amount)--在指定日历字段值的基础上+-一个值
* Calendar类注意事项
       MONTH:取值范围0-11 需要+1 才是正确的月份
       DAY_OF_MONTH	 默认星期天是一周的第一天  2  代表周二  
* 例子：
```java
       Calendar c = Calendar.getInstance();
       System.out.println(c.get(Calendar.DAY_OF_WEEK));	
	
	   c.set(Calendar.YEAR , 2018);
	   c.add(Calendar.MONTH , 12);
```

## System类--常用方法
>static void exit(int status)

        --->System.exit(0); // 或者-1
    	--->0 代表正常退出，-1 代表异常退出
>static long currentTimeMillis()--获取当前时间的毫秒值

        ---->long start = System.currentTimeMillis();
>static void arraycopy(Object src , int srcPos , Object dest , int destPos , int length)  //数组复制

      src   --源数组
      srcPos--源数组的起始索引
      dest  --目标数组
      destpos-目标数组的起始索引
      length--要复制的元素个数

## StringBuilder类
* StringBuilder是什么：一个可变的字符序列--可变的==字符串==

* StringBuilder特点：
       解决字符串拼接耗性能的问题：耗时间耗内存

* StringBuilder的构造方法：
```java
StringBuilder sb = new StringBuilder();
StringBuilder(String str)	//将不可变字符串转化为可变字符串
StringBuilder sb = new StringBuilder("abc);
```
* StringBuilder类常用方法：
 append(数据类型 变量) 
 ```java
	   sb.append(false).append(l23); //链式编程
       toString(); //符串转为不可变字符串	
 ```


## 包装类
* 为什么需要包装类：
       基本数据类型虽然效率高，但是功能优先，只能做加减乘除运算，为了对基本数据类型机型更多的操作，Java为每种基本数据类型提供了对应的类（包装类）

* 包装类

| 基本数据 | byte | short |   int   | long | float | double |   char    | boolean |
| :------: | :--: | :---: | :-----: | :--: | :---: | :----: | :-------: | ------- |
|  包装类  | Byte | Short | Integer | Long | Float | Double | Character | Boolean |

* 包装类的常用操作：
```java
        //将字符串转换为对用的基本数据类型---包装类名.parse对应的包装类名
		int a1 = Integer.parseInt(str1);
		double b1 = Double.parseDouble(Str2);
        //将基本数据类型转换为字符串类型---包装类名.toStirng
    	String str3 = Integer.toString(num);
```


## 自动拆装箱
* 概述：JDK1.5 新特性
* 概念：
	自动拆箱：Java编译器自动将包装类类型转换为对应的基本数据类型的过程
	自动装箱：Java编译器自动将基本数据类型转换为对应的包装类类型

* 举例：
```java
       Integer num01 = Integer.valueOf(100); //装箱
       int num02 = num01.intValue();	//拆箱   
```


?	   