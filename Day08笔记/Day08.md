#   Day08	

## File类

* 作用：用来操作硬盘上的文件或文件夹
* 路径分类
  * 绝对路径
  * 相对路径

* 一个File对象可以关联一个==文件==或==文件夹==

#### 1.1 File的构造方法

* public File(String pathname)
* File(File parent ,String child)
* File(String parent, String child)
* File(URI uri)

#### 1.2 File类的常用方法

![1561639223365](D:\JAVA学习资料\.vscode\就业班笔记\图片\1561639223365.png)

#### 1.3File的静态变量

```java
System.out.println(File.pathSeparator);  //    ;

System.out.println(File.separator);//  \
```


## 递归-文件搜索-查找后缀为==（xxx）==的文件

```java
package _06递归练习;

import java.io.File;
import java.util.Arrays;

public class Demo061 {
    public static void main(String[] args) throws Exception{
            File f = new File("D:\\");
        

            FindPDf(f);
    }

    public static void FindPDf(File f)throws Exception{
        if(f.isDirectory() && f != null){
            //下面这一步挺重要的，需要判断是否为空
            if(f.listFiles()!= null) {
                for (File f1 : f.listFiles()) {
                    if (f1.isDirectory() && f1 != null) {
                        FindPDf(f1);
                    } else {
                        if (f1.getName().endsWith(".html")) {
                            System.out.println(f1.getName());
                        }
                    }
                }
            }
        }
        else{
            if(f.getName().endsWith((".pdf"))){
                System.out.println(f.getName());
            }
        }
    }
}

```

#### 

## IO流

* 什么是IO流：java中I/O操作主要是指使用java.io包下的内容，进行输入，输出操作。输入也叫做读取数据，输出也叫做写出数组。

#### IO流的分类—

* 输入流：把数据从其他设备读去到内存中的流
* 输出流：把数据从内存中写出到其他设备上的流



* 字节流：以字节为单位，读写数组的流
* 字节流：以字符为单位，读写数据的流



