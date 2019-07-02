#   Day07



## 一、线程池

* 概述: 一个用来负责创建和管理线程的容器
* 作用: 避免频繁创建线程和销毁线程的开销,提高程序性能,提高线程管理性
* 原理: 程序启动时预定创建一定数量的线程存储在容器中
  * 线程池里面有==工作线程==(PoolWorker),==任务队列==(taskQueue) ,==任务接口==(task),==线程池管理器(Thread Pool)==

## 二、线程池执行Runnable任务

* 创建线程池对象(Excecutorservice = Excetors.newFixedThreadPool(2));
  //包含了两个线程对象
* 创建Runnable接口子类对象
* 提交Runnable接口子类对象   
* submit
* 关闭线程池(一般不做)
  * shutdown()  关闭线程
  * shutdownNow() 立即销毁线程

```java
public class ThreadPoolDemo{
	public static void main(String args[]){
		//1.创建线程池对象
		ExcutorService serviece  = Executors.newFixedThreadPool(2);//包含2个线程对象
		
		//2.创建Runnable实例对象
		MyRunnable r = new MyRunnable();
		
		//3.从线程池中获取线程对象,然后调用MyRunnable中的润()
		service.submit(r);
		service.submit(r);
		//注意:submit 方法调用结束后,程序并不是终止,式因为线程池控制了线程的关闭.
		//将使用完的线程又回归到了线程池中
		//关闭线程池
		//service.shutdown;
		
	}
}
```

## 三、线程池执行Callable任务

* 实现Callable接口需要重写call方法
* 实现Callable接口需要==指定泛型变量==具体数据类型
> public class CallableTask imiplements Callable<String> 
* Callable好处:==有返回值==、==可以声明异常==
* 如何获得Callable任务执行完毕的结果?
  * submit方法本身就会返回一个值，该值的类型是：Future(接口)
     * Future<T> submit(Callable<T> task);
  * 调用Future接口的方法get获得返回值(get方法有异常,需要处理)
* 



## 四、死锁

* 概念 多个线程在执行任务时争夺资源而造成一种相互等待的状态称为死锁
* 产生死锁的条件
  * ==多个线程==
  * ==有多把锁==
  * ==出现同步代码嵌套==

## 五、Lambda表达式的标准格式

* 概念: 函数式思想则尽量忽略面向对象的复杂语法--强调做什么,而不是做什么
* Lambda表达式的标准格式为:
```java
(参数类型 参数名称) -> {代码语句}
```

* 条件:参数或变量必须是接口类型且接口中有且只有一个抽象方法
* 函数式接口: 当接口中有且只有一个抽象方法   @Funtional Interface



## 六、Lambda 表达式的省略格式与规则

* ==规则==:
  * 省略小括号: 当小括号中只有一个参数
  * 参数的数据类型可以省略
  * 大括号中只有一行语句时,可以省略 . 如果省略了,则return语句和分号也需要省略

## 七、Stream流

* 用于对集合中的元素进行加工处理
* 单列集合流的获取
  * 集合名.stream();
* 数组流的获取
  * Stream.of(数组名);
* 双列集合
  *  KeySet.stream();
  *  value.stream();
  *  entrySet.stream();

 ####  7.1流操作


​	![1561551290282](D:\JAVA学习资料\.vscode\就业班笔记\图片\stream流.png)

 #### 7.2 流中的内容收集到集合中

public static <T> Collector<T, ?, List<T>> toList() ：转换为 List 集合。
public static <T> Collector<T, ?, Set<T>> toSet() ：转换为 Set 集合。

```java
import java.util.List;
import java.util.Set;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class Demo15StreamCollect {
  public static void main(String[] args) {
    Stream<String> stream = Stream.of("10", "20", "30", "40", "50");
    List<String> list = stream.collect(Collectors.toList());
    Set<String> set = stream.collect(Collectors.toSet());
 }
}
```
#### 7.3 流中的内容收集到数组中

```java
import java.util.stream.Stream;
public class Demo16StreamArray {
  public static void main(String[] args) {
    Stream<String> stream = Stream.of("10", "20", "30", "40", "50");
    Object[] objArray = stream.toArray();
 }
}
```

