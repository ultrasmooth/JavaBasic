#   Day03

##  1.数据结构
* 栈的数据结构特点：先进后出（FILO）
* 队列结构的特点：先进先出（FIFO）
* 数组结构的特点：查询快，增删慢
* 链表结构：查询慢，增删快
* 红黑树：查询速度很快




## 2.list集合
* 特点：有序，有索引，元素可重复
 ####   list集合常用方法

```java
//list独有的，不包含collection
public void add(int index, E element)在指定位置添加元素
public E get(int index)获得指定位置元素
public E remove(int index)删除指定位置的元素，返回被删除的元素
public E set(int index, E element)修改指定位置的元素为新元素。
```
* 注意：==带索引的方法要注意索引越界问题==

####   ArrayList集合底层结构和特点

* 查询快，增删慢





##  3.LinkedList

* 特点：有序，有索引，可重复
* LinkedList集合特点有方法
```java
public void addFirst(E e)//将元素添加到链表头的方法
public void addLast(E e)//将元素添加到链表尾的方法
public E getFirst()//获得链表头元素的方法
public E getLast()//获得链表尾元素的方法
public E removeFirst() //删除链表尾部元素的方法
```


####  如何选择LinkedList和ArrayList

* 如果需要执行增删操作，则选择LinkedList
* 如果只是执行查询操作，则选择ArrayList




## 4.vector集合

* List接口的实现类之一，已经过时了。

* 底层数组：增删慢，查询快，线程安全，效率低（已经被ArrayList取代了）

* 遍历vector集合，==使用Enumeration接口==

* 常用方法


|    判断是否有下一个元素    | 将指针下移指向下一个元素并返回当前元素 |
| :------------------------: | :------------------------------------: |
| boolean hasMoreElements(); |           E nextElements();            |

```java
Enumeration<String> it = vector.elements();  //使用elements()方法
while(it.hasMoreElements()){
    System.out.println(it.nextElement());
}

```


## 5.set集合

* 特点：无序，无索引，元素不重复

* 遍历方法：==增强for或迭代器==

  

####   HashSet集合特点和底层结构

* 特点：无序，无索引，元素不可重复
* 底层结构：==哈希表（数组和链表的结合体）==------->参考第7点
* ==如何从HashSet集合中获取元素：只能采用遍历==



####  LinkedHashSet的特点和底层结构
* 继承==HashSet==
* 特点：无索引，元素不可重复
* 继承hashset：能够保证存储顺序一致
* 底层结构：==哈希表（数组和链表的结合二体）+链表==----->参考第7点




## ==6.对象哈希值==

* 每一个对象都有一个哈希值

* 哈希值是一个十进制的整数

* 默认是对象在内存中的地址值

* 可以理解为对象的唯一标识，相当于人的身份证

***

#### 如何获得对象的hash值

	* int hashCode
***

#### hash值有什么用？

* 哈希值是对象存储到哈希表的重要依据
	
***
* String 重写hashcode方法



## 7. 哈希表

* 什么是哈希表
	* jdk1.8 ==链表+数组==
	* jdk 1.8 之后 数组+链表+ 红黑树



## 8.可变参数(1.5新特性)
> 格式：数据类型...变量名

```java
public static int sum(int...a){}
```

* 本质是数组

![1561025562445](D:\JAVA学习资料\.vscode\就业班笔记\图片\可变参数.png)

* 遍历方法（使用foreach遍历）：

```java
public static int sum(int...arr){
    int result = 0;
    for(int i : arr){
        result += i;
    }
    return result;
}
```



* ==注意事项==
  
  * 可变参数在形参列表中只能放在==最后面==。
  
    

## 9.Collections工具类
* 一般带s的类是工具类

* 常用方法（三个）

    > public static <T> boolean addAll(Collection<T> c, T... elements) :
    >
    > public static void shuffle (List<?> list)
    >
    > public static <T> void sort (List <T> list)

* 注意事项
	* shuffle和sort方法只能接受list
	* sort方法默认是升序 

## 10.Comparator 比较器
* 自定义Comparator比较且的步骤
	* 创建类实现Comparator接口并重写compare方法
	* 在compaere方法中定义号排序规则
	> return o2 -o1;降序
	> return o1 -o2;升序

## 总结

### 如何选择集合

* 如何要求元素可重复，则只能在list体系下选择
	* 如果需要执行大量增删操作，则选择LinkedList
	* 如果只要执行查询操作，则选择ArrayList
* 如果要求元素不可重复，则在set体系下选择
	* 如果需要保证存取顺序一致，则只能选择LinkedHashSet，否则可以随便选择
* 

![1561027906472](D:\JAVA学习资料\.vscode\就业班笔记\图片\day3总结.png)





## 课后练习

####  训练描述
一个学科中有若干班级，每一个班级又有若干学生。整个学科一个大集合，若干个班级分为每一个小集合(集合嵌
套之HashSet嵌套HashSet)。要求如下
1、 学生类有两个属性，姓名和年龄，并定义有参构造、无参构造和getter/setter方法.姓名和年龄相同的视为同一
学生
2、向班级集合中添加若干个学生（至少两个学生）。
2、向学科集合中添加所有班级(至少创建两个班级)。
3、使用两种方法遍历学科集合，并打印出所有学生。

* 定义学生类（不是重点）
```java
class Student{
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Student(String name, int age) {

        this.name = name;
        this.age = age;
    }

    public Student() {

    }

    @Override
    public String toString() {
        return "Student{" +
                "姓名='" + name + '\'' +
                ", 年龄=" + age +
                '}';
    }
}
```
* 主方法一，在subject的HashSet添加泛型变量<<HashSet<Student>>
```java
import java.util.Collections;
import java.util.HashSet;
import java.util.Iterator;

public class Test02 {
    public static void main(String[] args) {
        HashSet<HashSet<Student>> subject = new HashSet<>();
        HashSet<Student> classes = new HashSet<>();
        HashSet<Student> classes2 = new HashSet<>();
        Collections.addAll(classes, new Student("张三", 3), new Student("李四", 4));
        Collections.addAll(classes2, new Student("张四", 3), new Student("李五", 4));

        Collections.addAll(subject, classes, classes2);

        //第一种遍历方法：
       /* Iterator<HashSet> iterator = subject.iterator();
        while (iterator.hasNext()){
            Iterator iterator1 = iterator.next().iterator();
            while(iterator1.hasNext()){
               System.out.println(iterator1.next());
            }
        }*/

       //第二种遍历方法：
        for (HashSet<Student> students : subject) {
            for(Student s : students){
                System.out.println(s);
            }
        }

    }
}
```

* 主方法二，在HashSet，subject 中定义泛型变量<HashSet>, 这个时候第二种遍历方式要修改

```java
public class Test02 {
    public static void main(String[] args) {
        HashSet<HashSet> subject = new HashSet<>();
        HashSet<Student> classes = new HashSet<>();
        HashSet<Student> classes2 = new HashSet<>();
        Collections.addAll(classes, new Student("张三", 3), new Student("李四", 4));
        Collections.addAll(classes2, new Student("张四", 3), new Student("李五", 4));

        Collections.addAll(subject, classes, classes2);

        //第一种遍历方法：
       /* Iterator<HashSet> iterator = subject.iterator();
        while (iterator.hasNext()){
            Iterator iterator1 = iterator.next().iterator();
            while(iterator1.hasNext()){
               System.out.println(iterator1.next());
            }
        }*/

       //第二种遍历方法：
        for (HashSet students : subject) {
            for(Object s : students){    //这里就不能写for (Student s: students)
                System.out.println(s);
            }
        }

    }
}
```

