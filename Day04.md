#   Day04

## 1.Map接口

* map---->映射
* 双列集合的父类
* 用处：解决单列集合查询数据不方便的问题
* 键=值
* 特点：键必须唯一，值可以重复 

```java
public V put (K key, V value):
//即是添加，也是修改的方法
//如果键不存在，则添加，返回null
//如果键存在， 则添加新值，返回旧值

public V get(Object key):
//根据键获得对应的值，如果键不存在，则返回null
	
public V remove(K key):

public boolean containKey(Object key):

public int size():

public void clear();
```

* ==如果使用get方法获得一个空键得值时，会返回一个null==

* #### Map遍历方式一（键找值）

* 1.键找值方式遍历Map集合的步骤

  * 1.调用Map集合的KeySet方法获得键集合：Set集合
	```java
	Set<String> KeySet = map.KeySet();
	```

  * 2.使用增强for或者迭代器遍历键集合，得到每一个键，根据键调用map对象的get方法获得值

  ```java
     for(String Key : KeySet){
         String value = map.get(key);
         System.out.println(key+"="+value);
         }
  //或者使用迭代器遍历键集合
  Iterator<String> it = KeySet.iterator();
  while(it.hasNext()){}
  ```
  
  
  
* #### Map遍历方式2-“键值对”遍历

* Entry对象概述：用于封装键值对

* 如何获得Entry对象？

  * 通过调用Map集合得entrySet方法获得

  * > Set<Entry<K,V>> entrySet()
* Entry对象常用方法
	> K getKey();获得键
	> V getValue();获得值


```java
//使用entrySet()方法
Set<Entry<String,String> >entrySet=map.entrySet();
for(Entry<String ,String> entry: entrySet){
	System.out.println(entry.getKey()+"="+entry.getValue());
}
*  如何取得键和值

```

## HashMap存储自定义类型
* 使用自定义对象作为键时如何实现去重功能
	* 重写hashCode和equalsfangfa
	* 如果不是作为键，则不用重写

## LinkedHashMap
* 特点：继承HashMap：能够保证存取顺序一致



