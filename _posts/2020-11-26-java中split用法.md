---
layout: post
title: "Java中split的用法"
date: 2020-11-26
description: "Java中split函数的详解"
tag: java
---
## 用法
Java中split的用法
Java中的我们可以利用split把字符串按照指定的分割符进行分割，然后返回字符串数组，下面是string.split的用法实例及注意事项：
java.lang.string.split
split 方法
将一个字符串分割为子字符串，然后将结果作为字符串数组返回。
stringObj.split([separator，[limit]]) 
stringObj
必选项。要被分解的 String 对象或文字,该对象不会被split方法修改。
separator 
可选项。字符串或正则表达式对象，它标识了分隔字符串时使用的是一个还是多个字符。如果忽略该选项，返回包含整个字符串的单一元素数组。 
limit
可选项。该值用来限制返回数组中的元素个数(也就是最多分割成几个数组元素,只有为正数时有影响)
split 方法的结果是一个字符串数组，在 stingObj 中每个出现 separator 的位置都要进行分解。separator不作为任何数组元素的部分返回。
示例1：

```java
      String str="Java string split test";
      String[] strarray=str.split(" ");
      for (int i = 0; i < strarray.length; i++)
          System.out.println(strarray[i]);
将输出：
Java
string
split
test
```

示例2：

```java
      String str="Java string split test";
      String[] strarray=str.split(" ",2);//使用limit，最多分割成2个字符串
      for (int i = 0; i < strarray.length; i++)
          System.out.println(strarray[i]);
将输出：
Java
string split test
```

示例3：

```java
      String str="192.168.0.1";
      String[] strarray=str.split(".");
      for (int i = 0; i < strarray.length; i++)
          System.out.println(strarray[i]);
结果是什么也没输出,将split(".")改为split("\\."),将输出正确结果：
192
168
0
1
```

经验分享：   
1、分隔符为“.”(无输出),“|”(不能得到正确结果)转义字符时,“*”,“+”时出错抛出异常,都必须在前面加必须得加"\\",如split("\\|");
2、如果用"/"作为分隔,就得写成这样：String.split("\\//"),因为在Java中是用"//"来表示"/"的,字符串得写成这样：String Str="a//b//c";
 转义字符,必须得加"\\";
3、如果在一个字符串中有多个分隔符,可以用"|"作为连字符,比如：String str="Java string-split#test",可以用Str.split(" |-|#")把每个字符串分开;

## 注意事项
在java.lang包中有String.split()方法，返回是一个数组。



使用时要注意参数如果是特殊符号的话要进行转义。



　 1、“.”和“|”都是转义字符，必须得加"\\";
　　如果用“.”作为分隔的话，必须是如下写法：
String.split("\\."),这样才能正确的分隔开，不能用String.split(".");
如果用“|”作为分隔的话，必须是如下写法：
String.split("\\|"),这样才能正确的分隔开，不能用String.split("|");

　　2、如果在一个字符串中有多个分隔符，可以用“|”作为连字符，比如：“acount=? and uu =? or n=?”,把三个都分隔出来，可以用
　　String.split("and|or");

　　3、public String[] split(String regex,int limit)根据匹配给定的正则表达式来拆分此字符串。
　　此方法返回的数组包含此字符串的每个子字符串，这些子字符串由另一个匹配给定的表达式的子字符串终止或由字符串结束来终止。数组中
　　的子字符串按它们在此字符串中的顺序排列。如果表达式不匹配输入的任何部分，则结果数组只具有一个元素，即此字符串。

　　4、public string[] split(string regex)
　　这里的参数的名称是 regex ，也就是 regular expression （正则表达式）。这个参数并不是一个简单的分割用的字符，而是一个正则表达式，
他对一些特殊的字符可能会出现你预想不到的结果，比如测试下面的代码：

（1） 用竖线 | 分隔字符串，你将得不到预期的结果

```java
String[] aa = "aaa|bbb|ccc".split("|"); //String[] aa = "aaa|bbb|ccc".split("\\|"); 这样才能得到正确的结果 for (int i = 0 ; i <aa.length ; i++ ) { System.out.println("--"+aa); }
```



（2）用竖 * 分隔字符串运行将抛出java.util.regex.PatternSyntaxException异常，用加号 + 也是如此。
String[] aa = "aaa*bbb*ccc".split("*"); //String[] aa = "aaa|bbb|ccc".split("\\*"); 这样才能得到正确的结果 for (int i = 0 ; i <aa.length ; i++ ) { System.out.println("--"+aa); }



（3）显然，+ * 不是有效的模式匹配规则表达式，用"\\*" "\\+"转义后即可得到正确的结果。
（4） "|" 分隔串时虽然能够执行，但是却不是预期的目的，"\\|"转义后即可得到正确的结果。
（5）还有如果想在串中使用""字符，则也需要转义.首先要表达"aaaa\bbbb"这个串就应该用"aaaa\\bbbb",如果要分隔就应该这样才能得到正确结果：
String[] aa = "aaa\\bbb\\bccc".split(\\\\);
（6） 还有就是点号"."，也要首先转义才能得到正确的结果。


第一种方法：

```java
string s="abcdeabcdeabcde"; string[] sArray=s.Split('c') ; foreach(string i in sArray) Console.WriteLine(i.ToString());
```

输出下面的结果:

```java
ab
deab
deab
de
```

第二种方法：
我们看到了结果是以一个指定的字符进行的分割。使用另一种构造方法对多个字符进行分割:

```java
string s="abcdeabcdeabcde"; string[] sArray1=s.Split(new char[3]{'c','d','e'}) ; foreach(string i in sArray1) Console.WriteLine(i.ToString());

可以输出下面的结果：
ab
ab
ab
```

