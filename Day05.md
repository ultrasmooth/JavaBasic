#   Day05
## Java中的异常体系
* Throwable类是Java语言中所有错误或者异常的超类  
    * 1.Error不能处理的  
    * 2.Exception（异常，可以处理）  
      * 编译时异常(必须处理的)
      * 运行时异常(可以处理，也可以不处理)

* error例子
 ![1561272672437](D:\note\就业班笔记\图片\错误.png)
#### 如何判断是异常还是错误  
* 以Exception结尾的是异常，否则是错误

## throw创建异常  
* ==throw的格式==
```java
throw new 异常名称
```
* 例子
```java
public class Demo03{
    public static void main(String args[]){
        int[] arr = {} ;
        int number = getNumber(arr);
        System.out.println("number=" + number);
    }

    public static int getNumber(int[] arr){
        if(arr.length == 0){
            throw new Exception("数组长度为0");        }
        int i = arr[arr.length - 1] ;
        return i;
    }
}
```
## 处理throws异常
#### 处理异常的两种方式  
* try...catch 方式：(自己处理，负责)
* throws方式:(让别人去处理，不负责任)

* throws处理异常的格式
>修饰符 返回值类型 方法名（参数列表) throws 异常类名1，异常类型2...{}

* 例子-throws处理异常
```java
  public class Demo04{
      public  static void main(String args[])throws Exception{
          int[] arr = {11,22,33};
          int[] arr = {} ;
          int number = getNumber(arrJ);
          System.out.println("number="+number);
      }

    public static int getNu-mber(int[] arr)throws Exception{
        if(arr.length == 0){
            throw new Exceptino("异常");
            int i = arr[arr.length - 1];
            return i ;
        }
    }
  }
```
* 例子二- try-catch 
```java
public class Demo05{
    public static void main(String[] args){
        int[] arr = {};
        int number = getNumber(arr);
        System.out.println("number"+number);
    }

    public static int getNumber(int[] arr){
        try{
            if(arr.length == 0){
                throw new Exception("异常");
            }
        }
    }
}

```

## 多catch处理异常

* 多catch捕获异常的注意事项
  * 如果多个异常类型之间没有继承关系，则父类类型的异常要写在子类类型的==后面==
  * 如果没有继承关系，就没有顺序之分。

![1561276781380](D:\JAVA学习资料\.vscode\就业班笔记\图片\1561276781380.png)



* catch多个异常的注意事项
	* 如果多个异常类型之间有继承关系，则父类类型的异常要写在子类类型的后面。
	* 当多个catcch代码块时，有没有可能同时执行多个代码的catch
当有个catch代码块时，有没有同时执行多个

## finally代码块

* 作用: 主要是用来释放资源，关闭资源。

```java
public class Demo7{
    public static void main(String[] args){
        divide(10,0);
    }

    public static int divide(int a ,int b){
        int c = 0;
        try{
            c = a / b;
            System.out.println("cccc");
        }catch(ArithmeticException e){
            System.out.println("我处理了除数为0");
            return -1;
        }finally{
            System.out.prinln("我一定会走");
        }
        return c;
    }
}

```

## 异常中常用方法
* String getMessage() 返回此throwable的详细消息字符串-- by zero
* String toString() 返回此 throwable的简短描述--java.lang.ArithemeticException: /by zero
* void printStackTrace() 将此throwable及其追踪输出及标准字符流。--异常默认输出的信息
  * 使用最多

```java
public class Demo08{
    public static void main(String[] args){
        try{
            int c = 10 / 0;
            System.out.println("c="+c);
        }catch(ArithmeticExceptin e){
            System.err.println("我是红色的。");
            e.printStackTrace();
        }
    }
}
```
## 异常分类
* 运行时异常：可以不处理（RuntimeException及其子类异常)
* 编译时异常：一定要处理，否则编译有问题
* 为什么编译器对运行时异常管理如此松散？
  * ==因为运行时异常一般可以通过程序员良好的编程习惯避免。==
#### 常见的运行时异常
```java
ArithemeticException
NullPointerException
ArrayIndexOutOfBoundsException
StringIndexOutOfBoundsException
```
## ==异常注意事项（子类继承父类的问题）==
* 子类重写方法时不能声明比父类方法声明大的异常
* 父类没有声明异常，子类重写方法时不能声明
* 父类声明了异常，则子类可以声明和父类声明一样的异常或其子类异常。
* ==子类不能声明比父类范围更大的异常==
## 自定义异常

* 创建一个类继承Exception或RuntimeException： 
* 命名：XxxException
* 提供两个构造方法：无参数和有参数
* 创建例子：

```java
//这是一个编译时异常
public class U18Exception extends Exception{
    //定义构造方法
    public U18Exception(){

    }

    public U18Exception(String message){
        super(message);
    }
}
```
使用步骤:throw new 异常类对象();
```java
public class Demo09{
	public static void main(String[] args){
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入用户名");
		String unsername = sc.nextLine();
		system.our.println("请输入年龄");
		int age = sc.nextInt();
		if(register(username , age)){
			System.out.println("注册成功");
		}else{
			System.out.println("注册失败");
	}
	public static boolean register(String username, int age) throws Exception{
		if(age < 18){
			U18Exception e = new U18Exception("您未成年");
		}
	}
}
```
## 并发和并行
并行：指两个或多个事件在同一时刻发生（同时发生）12：30

并发：指两个或多个时间在同一时间段内发生12：30 - 12：35

## 什么是线程

    是进程的执行单元，线程就是来执行代码的

#### 进程和线程比喻  
    进程相当于公司
    线程相当于员工

#### ==实现重进入==

![1561454332667](D:\note\就业班笔记\图片\1561454332667.png)

# wait() 和 notify（）的使用注意事项

* 必须在同步代码块和同步方法中调用 
* 必须由锁对象调用
