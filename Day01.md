# Day01
## API����
ȫ�ƣ�Application Programming Interface
ʹ�ò��裺
* ��ѯ�����ĵ��鿴��˵����Ϣ
* ������Ķ���
* ʹ�ö���
* ������.����()
* ������.��Ա������()
## ������
* ��Щ��û�й��췽������һ���о�̬��������ֱ��ͨ���������ã��������Ϊ�����ࡣ
	
## Object��-���������÷�����
* �ص㣺Object��������ĸ���
* toString()����
```
���ã����ظö�����ַ�����ʾ
Ŀ�ģ��ڴ�ӡ����ʱ���뿴���������ڴ��еĵ�ֵַ����ϣ��������������ݣ���Ա��������ֵ��
Ĭ�ϸ�ʽ������.����@�������ڴ��еĵ�ֵַ---��ȫ���ַ���@�������ڴ��еĵ�ֵַ		
��дtoString()��д�����Զ�����	
```

  * equals����
```
���ã�
	�ж����������Ƿ���ͬ����ͬ����true����ͬ����false
	Ĭ����ͨ���Ƚ���������ĵ�ֵַ�ж϶����Ƿ���ͬ
��==��������:
	���ڻ����������ͣ��ǱȽ�����������ֵ
	���������������ͣ��ǱȽ���������ĵ�ֵַ
��дequals����ע�����
    1.��Ҫʹ��instanceOf�����жϣ������п��ܳ���ClassCastException
    2.��Ҫ����ת�ͣ����磺Student s2 = (Student)obj;
��дequals������Ŀ�ģ�
	��ϣ��ͨ����ֵַ�ж����������Ƿ���ͬ������ϣ��ͨ���ж϶���ĳ�Ա������ֵ�Ƿ���ͬ	
��дequals������д�����Զ�����	
```

## Objects�� --�������õķ���
    static boolean isNull(Object obj)---�ж϶����Ƿ�Ϊ�գ��շ���true
    static boolean nonNull(Object obj)--�ж϶����Ƿ�Ϊ�գ���Ϊ�շ���true
    static boolean equals(Object a , Object b) --�ж����������Ƿ���ͬ����ͬ����true 
    ==Objects.equals(object a, Object b)��������aΪnull==

## date��
* Date��Ĺ��췽��	 
	Date()---�������ڶ��󣬵�ǰϵͳʱ��
	Date(long time)---���ݺ���ֵ�������ڶ���

* Date�ೣ�ó�Ա����
	long getTime()-----����1970-1-1 00:00:00 ����ĺ���ֵ
	--->1 �� = 1000 ����
	
## DateFormat��-�ı����ڵ���ʾ��ʽ
* DateFormat�ǳ����࣬����ֱ��ʵ������Ҫʹ��������SimpleDateFormat�����ø��෽��
* SimpleDateFormat���췽����������pattern

  > new SimpleDateFormat("YYYY-MM-dd");      

* ���÷���
  > String format (Date d);���෽��
  > parse��String pattern);
	
* ��ϰһ��
```java
/*��Dateת��"2018��9��15�� 19ʱ18��19��" ��ʽ
        ����1���������ڶ���
		����2������DateFormat�������
		����3������DateFormat�ķ���--format(Date d)
*/
		Date date = new Date();
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy��MM��dd�� HHʱ:mm��:ss��");
		String dateStr = sdf.format(date);
```
* ��ϰ��
```java
	/*  ���ַ���"2017-12-26 10:13:31"ת��Date
	    ����1���������ڸ�ʽ������ָ������ģʽ������ģʽ����������ַ����ĸ�ʽһ��
	    ����2���������ڸ�ʽ�������parse���������ַ�����������ڶ���
	*/
	    String str = "2017-12-26 10:13:31"	;
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
		Date date = sdf.parse(str);//parse�������ܻᵼ���쳣������ҧ�ְ�main�����������쳣
```
## Calendar��
* Dateȱ�ݣ�
    Date��Ե�����ȡ������ʱ���룬�Ӽ����㲻�ô�������Date�಻֧�ֹ��ʻ�

* ����Calendar��
       *Calendar����һ�������࣬����ֱ�Ӵ�������ֻ��ʹ��������� 
       *ͨ��Calendar���ṩ�ľ�̬����getInstance�����������

* Calendar�ೣ�õķ�����
       int get(int field)-----���������ֶλ�ö�Ӧ���ֶ���Ϣ
       void set(int field,int value)--��ָ�������ֶε�ֵ�޸�Ϊָ����ֵ
       void add(int filed , int amount)--��ָ�������ֶ�ֵ�Ļ�����+-һ��ֵ
* Calendar��ע������
       MONTH:ȡֵ��Χ0-11 ��Ҫ+1 ������ȷ���·�
       DAY_OF_MONTH	 Ĭ����������һ�ܵĵ�һ��  2  �����ܶ�  
* ���ӣ�
```java
       Calendar c = Calendar.getInstance();
       System.out.println(c.get(Calendar.DAY_OF_WEEK));	
	
	   c.set(Calendar.YEAR , 2018);
	   c.add(Calendar.MONTH , 12);
```

## System��--���÷���
>static void exit(int status)

        --->System.exit(0); // ����-1
    	--->0 ���������˳���-1 �����쳣�˳�
>static long currentTimeMillis()--��ȡ��ǰʱ��ĺ���ֵ

        ---->long start = System.currentTimeMillis();
>static void arraycopy(Object src , int srcPos , Object dest , int destPos , int length)  //���鸴��

      src   --Դ����
      srcPos--Դ�������ʼ����
      dest  --Ŀ������
      destpos-Ŀ���������ʼ����
      length--Ҫ���Ƶ�Ԫ�ظ���

## StringBuilder��
* StringBuilder��ʲô��һ���ɱ���ַ�����--�ɱ��==�ַ���==

* StringBuilder�ص㣺
       ����ַ���ƴ�Ӻ����ܵ����⣺��ʱ����ڴ�

* StringBuilder�Ĺ��췽����
```java
StringBuilder sb = new StringBuilder();
StringBuilder(String str)	//�����ɱ��ַ���ת��Ϊ�ɱ��ַ���
StringBuilder sb = new StringBuilder("abc);
```
* StringBuilder�ೣ�÷�����
 append(�������� ����) 
 ```java
	   sb.append(false).append(l23); //��ʽ���
       toString(); //����תΪ���ɱ��ַ���	
 ```


## ��װ��
* Ϊʲô��Ҫ��װ�ࣺ
       ��������������ȻЧ�ʸߣ����ǹ������ȣ�ֻ�����Ӽ��˳����㣬Ϊ�˶Ի����������ͻ��͸���Ĳ�����JavaΪÿ�ֻ������������ṩ�˶�Ӧ���ࣨ��װ�ࣩ

* ��װ��

| �������� | byte | short |   int   | long | float | double |   char    | boolean |
| :------: | :--: | :---: | :-----: | :--: | :---: | :----: | :-------: | ------- |
|  ��װ��  | Byte | Short | Integer | Long | Float | Double | Character | Boolean |

* ��װ��ĳ��ò�����
```java
        //���ַ���ת��Ϊ���õĻ�����������---��װ����.parse��Ӧ�İ�װ����
		int a1 = Integer.parseInt(str1);
		double b1 = Double.parseDouble(Str2);
        //��������������ת��Ϊ�ַ�������---��װ����.toStirng
    	String str3 = Integer.toString(num);
```


## �Զ���װ��
* ������JDK1.5 ������
* ���
	�Զ����䣺Java�������Զ�����װ������ת��Ϊ��Ӧ�Ļ����������͵Ĺ���
	�Զ�װ�䣺Java�������Զ���������������ת��Ϊ��Ӧ�İ�װ������

* ������
```java
       Integer num01 = Integer.valueOf(100); //װ��
       int num02 = num01.intValue();	//����   
```


?	   