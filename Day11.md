## Day11

127.0.0.1  本机ip地址

端口号：0~1024端口是系统保留的

端口号的取值范围：0到65535

网络三要素：ip，端口号，协议

#### UDP（User DatagramPacket Protocal）协议的特点

* 面向无连接协议
* 只管发送不确认对方是否收到
* 基于数据包发送，将数据和源以及目的地打包到数据钟
* 数据包大小限制在==64==k
* 因为无连接，所以速度块 

#### TCP（Transmission Control Protocal）协议特点

* 面向连接的协议
* 通过三次我手建立连接：形成数据传输通道
* 通过四次挥手断开连接
* 基于IO流进行数据传输
* 传输数据大小没有限制
* 面向连接，数度慢但可靠

#### TCP协议相关的类

* Socket：一个该类对象就代表一个客户端程序
* ServerSocket：一个该类对象就代表一个服务器端程序
* Socket含义：==套接字==

#### Socket类构造方法

* Socket(String host ,int port)
* 创建客户端Socket对象
* host:服务器端的IP地址
* port：服务器的端口号
* 如果服务器没有开启，则该构造器

#### Socket类常用方法

```java
OutputStream getOutputStream() ;获得字节输出流
InputStream getInputStream();获得字节输入流
```

ServerSocket的构造方法

* SeverSocket(int port);

#### ServerSocket类常用方法

* Socket accept()   等待客户端并连接获得与客户端




#### 注意事项

* 如果使用socket对象开启了OutputStream流,需要使用shutdownOutput关闭该流，否则对方无法结束。



####  使用多线成开启多客户的服务器

```java
SocketServer ss = new SocketServer(8848);
while(true){
    socket s = ss.accept();//注意在这里开启
    new Thread(()->{
        
    }).start;
}
```



## Junit

@After

@Before

@Test

* 命名规范
* 基本使用方法