# DAY14

## DQL语句

#### 条件查询

* SELECT * FROM student WHERE age = 20; //查询age等于20岁的学生
* SELEC T * FROM student WHRER age > 35 AND sex = '男'; 查询age大于35且性别为男的学生
* 查询id是1或3或5的学生（in关键字）
  * SELECT * FROM student3 WHERE id IN ( 1, 3, 5);
* 查询id不是1或3或5的学生
  * SELECT * FROM student3 WHERER id NOT IN(1,3,5);

##### 范围

* MySQL 通配符： % ，—

* BETWEEN 值1 AND 值2 表示从值1到值2范围，包头又包尾 比如： age BETWEEN 80 AND 100 相当于：age>=80 && age<=100

* LIKE 标识模糊查询SELECT*FROM 表名 WHERE 字段名 LIKE '通用符字符串' ; 

  ![1562372419614](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562372419614.png)

#### 排序查询

* 单列排序
 ![1562375039610](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375039610.png)

* 组合排序
 ![1562375137927](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375137927.png)

#### 聚合函数查询

5个常用聚合函数



| 函数名 |      |
| ------ | ---- |
| count  |      |
| sum    |      |
| max    |      |
| min    |      |
| avg    |      |

* count（会跳过null的数组）
  ![1562375524307](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375524307.png)![1562375631196](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375631196.png)

![1562375660411](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375660411.png)

![1562375711844](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375711844.png)

####  分组查询 group by 字段名 having



![1562375989916](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562375989916.png)

结果：

![1562376016505](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562376016505.png)

![1562376209398](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562376209398.png)

![1562376573853](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562376573853.png)

![1562376625450](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562376625450.png

![1562376674011](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562376674011.png)

![1562378031756](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562378031756.png)                                                     



分页 语法  select *from 表名 limit 要跳过的行数，要查询的行数

####  数据库的备份和还原



#### 数据约束

| 主键约束 | primary key                                               |
| -------- | --------------------------------------------------------- |
| 唯一约束 | unique                                                    |
| 非空约束 | not null                                                  |
| 默认约束 | default 默认值                                            |
| 外键约束 | constraint foreign key（外键列名）references 主表（主键） |
| 检查约束 | MySQL不支持                                               |

* 添加主键约束 primary key

```sql
create table st1(
	id int primary key,
);
```

* 主键值规则：唯一且非空。
* 添加主键约束（方法二-在添加表之后添加）添加主键约束不能违反现状
  * alter table st1 add primary key (id) 
* 删除st1表的主键
	* alter table st1 drop primary key;

* 一张表只能有一个主键

#### 主键自增长

> auto_increment

![1562381062479](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562381062479.png)

修改自增长的值从1000开始

alter table st2 auto_increment  = 1000;

#### delete 和 truncate 的区别

* 相同点：都可以删除表的所有数据

* 不同点： delete删除所有数据则不会影响主键自增长的值，仅仅是删除数据，不会影响表结构。

  ​                 truncate删除所有数据会重置主键自增长的值，原理：先drop表，然后创建同名的表

  

  

#### 零填充

![1562381662009](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562381662009.png)

#### 唯一约束

![1562381982492](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562381982492.png)



#### 非空约束

![1562382217512](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562382217512.png)

#### 默认约束

![1562382460330](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562382460330.png)

#### 外键约束

* 约束一张表（从表）的某一列（外键列）的值来引用另一张表的主键列值

![1562385034062](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562385034062.png)

* 查询外键约束名称

  show create table xx

  删除employee 表的emp_depid 外键

  alter table employee drop foreign key employee_ibfk_1;

  

* 再employee 表存在的条件下添加外键
* alter table employee add constraint foreign key(dept_id) references dept(id).



#### 级联操作

* 级联更新

  * 语法：on update cascade

    ![1562386295688](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562386295688.png)

* 级联删除(慎用)

  * 语法： on delete cascade 

  ![1562386348232](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562386348232.png)

#### 表关系 

一对一（实际开发用得最少）

* 多对多
*  
* ![1562388591076](D:\JAVA学习资料\.vscode\就业班笔记\图片\1562388591076.png)