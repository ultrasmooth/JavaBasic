# Day10

#### 缓冲流的构造方法的特点

* 构造方法方法都需要传入一个流

#### 字符缓冲流的BufferedWriter的特有方法

* void newLine(); 输出一个换行符

#### BufferedReader的特有方法

* String readLine();
* 从流关联的目标文件中读取一行数据，如果读取到文件末尾，返回null

#### （转换流）InputStreamReader的构造方法

* InputStreamReader(InputStream in , String charsetName)
  * 根据字节输入流创建字符转换流对象
  * charsetName：指定编码表名称，常用：gbk或者utf-8

#### 对象序列化

* ObjectOutputStream & ObjectInputStream
* 构造方法都是传入一个字节流
* 常用方法writeObject(Object obj)   &  readObject()

#### Serializable接口

* 是一个标记性接口，给类打上序列化的标记，只有有了该标记才能被序列化。

#### transient关键字

* 作用：用来修饰成员变量，该成员变量的值不会被序列化到文件中
* 格式：修饰符 transient 数据类型 变量名

#### 序列化集合

* ```java
  1. 将存有多个自定义对象的集合序列化操作，保存到list.txt文件中。
  2. 反序列化list.txt ，并遍历集合，打印对象信息。
  ```

#### 打印流(只有输出)

* 分类：
  * 字节打印流：PrintStream
  * 字符打印流：PrintWriter

* 构造方法：
  * PrintStream(String pathname)
* 常用方法：
  * print(数据类型 变量名）
  * println(数据类型 变量名）
    * 将变量值打印输出到目标文件中



***

# 使用方法小总结

## 输入流的read方法

| 字节流                          | 字符流                             |
| ------------------------------- | ---------------------------------- |
| read()                          | read                               |
| read(byte[] b)                  | read(char[] cbuf)                  |
| read(byte[] b, int off,int len) | read(char[] cbuf,int off, int len) |

* 字节流输入流的使用方法

```java
//1. 读取数据，返回⼀一个字节
int read = fis.read();
System.out.println((char) read);

//2.使用循环读取
int b ；
while ((b = fis.read())!=-1) {
System.out.println((char)b);
}

//3.使用字节数组读取
int len;
byte[] b = new byte[2];
while((len=fis.read(b))!=-1){
    System.out.println(new String(b));
}
```

* 字符输入流的使用方法

```java
//1.使用read方法，一次读取一个字符的数组，
int len = -1;
while((len=fr.read())!=-1){
    System.out.println((char)b);
}

//2.使用字符数组读取
int len;
char[] cbuf = new char[2];
while((len = fr.read(cbuf)!=-1)){
    System.out.println(new String(cbuf,0,len));
}
```



# 字节输出流和字符输出流的write方法

| 字节输出流                       | 字符输出流                              |
| -------------------------------- | --------------------------------------- |
| write(int b)                     | write(int b)                            |
| write(byte[] b)                  | write(char[] cbuf)                      |
| write(byte[] b,int off, int len) | write(char[] cbuf,int off,int len)      |
| --                               | ==write(String str)==                   |
| --                               | ==write(String str, int off, int len)== |