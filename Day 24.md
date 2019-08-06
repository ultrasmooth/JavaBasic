# Day 24

## tomcat的三种运行方式

* 第一种，在webapps目录下面文件夹（假如叫javaEE），将文件夹放在名字任意（假如文件名字叫a.html)。然后启动tomcat服务器，在浏览器输入地址：``http://localhost:8080/javaEE/a.html``。缺点：项目放在webapp下面会导致项目越来越多,tomcat启动会变慢。
* 第二种，虚拟目录。在``conf/server.xml``文件的host元素中配置Context元素。
  * 将文件放在任意目录假如放在``D:\aa\``下，文件叫``first.html``
  * 在server.xml文件中143行，找到host元素，写下面的代码
  * ``<Context path="/aa" docbase="d:/aa/"``
  * 在浏览器中输入：``localhost:8080/aaa/first.html

