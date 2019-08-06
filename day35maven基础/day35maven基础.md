# maven

![1565007375752](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565007375752.png)

## 配置maven

1.将Maven压缩包解压到某个目录，会出现 ``bin`` ``boot`` ``conf`` ``lib`` 四个文件夹

2.配置本地仓库，解压Repository压缩包

* 上面两个压缩包我都放在D:install下面

3.配置<font color=red>本地仓库</font>，修改maven的安装目录中/conf/settings.xml文件在53行配置本地仓库为上面的目录。

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 
http://maven.apache.org/xsd/settings-1.0.0.xsd">
    
<!--加上下面这句话，上面是原来就有的-->
<localRepository>e:\repository</localRepository>

```

4.配置<font color=red>远程仓库</font>，修改settings.xml文件，159行指定中央仓库的镜像。这里使用的是阿里云的仓库，速度比官方的快很多。

```xml
<mirror>
 <id>nexus</id>
 <mirrorOf>*</mirrorOf> 
 <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
 </mirror>
```

5.配置maven默认使用的<font color=red>jdk版本</font>，在setting.xml中，第189行加入如下信息

```xml
 <profile>
 <id>development</id>
 <activation>
 <jdk>1.8</jdk>
 <activeByDefault>true</activeByDefault>
 </activation>
 <properties>
 <maven.compiler.source>1.8</maven.compiler.source>
 <maven.compiler.target>1.8</maven.compiler.target>
 <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
 </properties>
 </profile>
```

6.配置MAVEN_HOME的<font color=red>环境变量</font>

```
MAVEN_HOME    路径
Path          %MAVEN_HOME%/bin
```

7.测是安装好的Maven

打开cmd本地控制台，输入

``mvn -v``

* 结果如下图

![1564988873244](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1564988873244.png)

## IDEA 创建Maven工程

在idea2017.03.02版本中（别的版本可能不同有点不同）。File--Other Setting --Default Settings--Build,Execution,Deployment--Maven

![1564989561009](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1564989561009.png)

![1565005567750](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565005567750.png)

### 创建maven工程有三种方法

1. 通过骨架创建工程，需要完善javaWeb-的目录结构

   ![1565005788370](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565005788370.png)

   * 1.1 需要在pom.xml加上Servlet的以来，artifactid设置为javax.servlet-api,选择版本为3.1.0的版本<font color=red>在tomcat中有servlet的jar包,但是在编译时和运行时没有，所有scope选择provide。
   * ![1565005986173](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565005986173.png)

2. 自定义创建maven代码

   2.1 创建完成一个web项目之后，在模块名字上面右键:Add Framworks Support,选择web application
   
   2.2 创建完成一个web 
   
   2.3 右键jbljavatoweb以后，修改pom.xml,加上下面这一段依赖
   
   ```xml
   <!--在<project></project>标签内加入-->
     <!--导入依赖-->
     <dependencies>
   
       <!--导入junit依赖-->
       <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.12</version>
         <scope>test</scope><!--scope是依赖范围，设置当前的junit的jar在哪里使用
                               值为test代表junit的jar包在test目录下java代码编译时可用
                           -->
       </dependency>
   
       <!--导入servlet依赖-->
       <dependency>
         <groupId>javax.servlet</groupId>
         <artifactId>javax.servlet-api</artifactId>
         <version>3.1.0</version>
         <scope>provided</scope>
       </dependency>
     </dependencies>
   
     <build>
   
       <plugins>
       <!-- jdk版本插件（了解），因为一般都采用全局配置,如果当前项目不使用全局就可以使用这个插件 -->
       <plugin>
         <groupId>org.apache.maven.plugins</groupId>
         <artifactId>maven-compiler-plugin</artifactId>
         <version>3.2</version>
         <configuration>
           <source>1.8</source>
           <target>1.8</target>
           <encoding>UTF-8</encoding>
           <showWarnings>true</showWarnings>
         </configuration>
       </plugin>
   
       <!--tomcat7的插件:
           优点，运行速度快，而且还支持webapp目录资源的热部署（webapp目录下资源的修改不用重新部署直接刷新识别）
       -->
       <plugin>
         <groupId>org.apache.tomcat.maven</groupId>
         <artifactId>tomcat7-maven-plugin</artifactId>
         <version>2.2</version>
         <configuration>
           <port>8080</port>
           <path>/</path>
           <uriEncoding>UTF-8</uriEncoding>
           <server>tomcat7</server>
         </configuration>
       </plugin>
   
       </plugins>
   
     </build>
   ```
   
   ## 生命周期

![1565054795531](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565054795531.png)

#### runtime依赖

jdbc驱动，只有运行的时候才会使用jdbc驱动，编译时只是加载

比如class forName("com.mysql.jdbc.Driver");,com.mysql.jdbc.Drivers是jar包已经编译好的，程序在执行过程中读取mysql驱动类生成它的子类对象，只在测试和运行期间才会用到mysql子类，所以设置runtimme范围。

### tomcat插件

不能通过下面的图片访问

![1565058864796](D:\note\就业班笔记\day35maven基础\day35maven基础.assets\1565058864796.png)