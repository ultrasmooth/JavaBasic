#   Day02

## 今天的内容

* 集合概念和继承体系
* Collection集合
* 迭代器
* 泛型
* 斗地主

## 集合

* 集合的定义：用来存储多个元素的容器

* 容器：数组和集合

* 集合和数组的区别

  * 数组：长度固定，==数组可以存储基本数据类型，也可以存储引用数据类型==
  * 集合：长度可变，==只能存储引用数据类型==，如果要存储基本数据类型则需要使用对应的包装类类型

* 集合分类

  * ==单列集合==：每次存储元素只需要存储一个

  * ==双列集合==：每次存储元素时需要存储两个。

    

* ==如何选择集合和数组==

  * 如果元素个数规定，则可以随便选择，否则只能选集合。

    

## 单列集合（今天主要学Collection）

### collection 集合体系

![1560840800114](D:\JAVA学习资料\.vscode\就业班笔记\图片\单列结合的体系.png)

* collection是根接口

### collection集合的常用7个方法

```
	public boolean add(E e):把给定的对象添加到当前集合中
	public void clear();	清空
	boolean remove(E e）	删除一个指定元素
	boolean contains(E e)判断当前的集合中是否包含指定的元素
	boolean isEmpty(): 判断集合是否为空集合
	int size():返回集合中的个数
	Object toArray()  返回一个数组

```



## 迭代器

* 什么是迭代
  * 迭代==遍历
  * ==一个用来遍历结合的对象==，该对象必须实现一个接口：==Iterator==
* 为什么要使用迭代器
	* 不同集合的集合特点不一样
  
* 迭代器的好处
  * 屏蔽了众多集合的内部实现细节，对外提供统一的遍历方式
  * 所有的==单列集合==都可以直接使用迭代器

* ==如何获得迭代器对象==
	* ==通过集合调用iterator（）方法==获得：Iterator<T> iterator();

* 迭代器的常用方法
```java
   boolean hasNext();
  E next()
```

* 迭代器的使用步骤
  * 调用集合方法获得迭代器对象
  * 调用迭代器对象方法从集合中获得元素

```java
  Iterator<E> it = list.iterator(); //得到对象
  System.out.println(it.hasNext());//true
  System.out.println(it.next());元素内容
  
```

* next方法的异常
	* NoSuchElementException

* 遍历的过程

 ```java
  while(it.hasNext()){
  	System.out.println(it.next());
  }
 ```

* ==注意== ：hasNext，判断是否有下一个元素，有返回true，否则false。如果指针不动，调用该方法也不会东g

* next方法。移动==指针==，并返回值

* ==并发修改异常==-不要再遍历的过程中进行增删操作

  * 如果在使用迭代器的遍历集合的过程中，增删集合，会出现该异常

  * ConcurrentModificationException

    

* hasNext 和 next 需要成对使用，可能出异常
* ==增强for本质是迭代器，所以不能再使用时候进行增删操作

## 泛型

* 是JDK1.5新特性

* 集合不使用泛型

  * 需要转型

  * 需要进行判断     
* 泛型的概念：数据类型参数化
* 可以使用再==类上==，==方法上==，==接口上==
* 在类上使用了泛型的类则称为泛型类
* 泛型类的格式
```java
	 class类名<T>{
	
	}
```
* T被称为泛型变量：只要是合法的标识符就可以。一般使用一个大写字母表示变量。常用的字母：T type,E elemtn,K key,V, value

* 泛型使用注意事项

   * 如果没有指定具体数据类型，则默认是Object

   * 泛型变量的具体数组类型由使用者创建泛型类对象时指定
   * 泛型指定的类型不能使用基本数组类型，只能是包装类



### 泛型方法

* 定义格式

>修饰符 <T> 返回值 方法名（参数列表）{}

* 具体的参数类型由传入的参数决定

* ==静态方法不能使用类上定义的泛型变量，如果静态方法需要使用泛型变量，则必须将该方法定义成泛型方法==

  
### 泛型接口
* 定义格式
> interface 接口名<T>{} //在接口中将T当成一种数据类型使用。

* 泛型接口的==实现方式==
  	* 实现接口时不指定泛型变量的具体数据类型，此时实现类必须定义为泛型类，由使用者创建
```java
public class StudentDao<T> implements Dao<T>{}
```
***
	*  实现接口同时指定泛型变量的据具体数据类型

```java
public class StudentDao implements Dao<Student>{}
```

### 通配符

* 通配符：可以匹配任何类型的数据

* 在泛型中没有多态的概念

>ArrayList<Object>list = new ArrayList<String >();//错误

* 通配符--匹配任意类型的数据
	* 一般不会单独使用，会结合泛型上下限使用
```java
ArrayList<?> list01 = new ArrayList<String>();
ArrayList<?> list02 = new ArrayList<String>();
ArrayList<?> list03 = new ArrayList<String>();
```
需求：定义一个方法接受ArrayList集合，方法功能：遍历打印集合元素
==再听一下==

```java
public static void printArrayList(ArrayList<?> list){
	for(Object obj : list){
		System.out.println(obj);
	}
}
```

***

#### 泛型上下限

* 泛型上限
  * 可以接受Animal机器子类类型数据

![1560851442219](D:\JAVA学习资料\.vscode\就业班笔记\图片\泛型上限.png)

* 泛型下限度

  * 只能接受Animal及其父类类型数据

  ![1560851720858](D:\JAVA学习资料\.vscode\就业班笔记\图片\泛型下限.png)

### 泛型定义的方式
* 泛型类
```java
class  Demo<P,R>{
	public R fun(P p){
		return null;
	}
}
```

* 泛型接口
```java
interface Demo<T>{
	public void method(T t){
	
	}
}
```

* 泛型接口的实现
```java
//方式一
//再子类中继续设置泛型，此泛型也作为接口中的泛型类型
class Demo2<S> implements Demo<S>{
	public void method(S s){
	
	}
}

// 泛型接口的实现方式二
//子类为父类接口设置具体泛型类型
class Demo2 implements Demo<String>{
	public void print(String t){
		System.out.println(t);
	}
}

````

* 泛型方法的定义
```java
//必须在方法的返回值类型前明确定义泛型标记
public static <T> T fun(T t){
	return t;
}
```