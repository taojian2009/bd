### 常用API的使用
java.util需要导包， java.lang不需要导包；



#### 0. Array
#### 1. 什么是数组
数组，是用于存储多个<b>相同类型</b>数据的存储模型；
+ 类型必须相同
+ 长度一旦固定，不可更改

#### 2. 数组的动态初始化
```
// 动态初始化
int[] rates = new int[3];
// 静态初始化
int[] rates = {123, 43,45,}
```
#### 3. 内存访问
堆内存：用于存储局部变量，用完回收
栈内存：用于存储数组中的实体；

#### 1. String
字符串有几种不同的构造方法；
hello是共享的，放在堆内存
字符串，`reference type`, 创建之后不可改变，但是可以共享；
```java
public class StringDemo {
    public static void main(String[] args) {
        String info = new String("hello");
        String debug = "hello";
        System.out.println(info.equals(debug));
        System.out.println(info == debug);
        // true
        // false 
    }
}
```
在java中,不能用“==”和“!=”来判断两个字符串是否相等。因为String是引用类型,而不是基本数据类型

**for each is not applicable for Class String**
##### 常见方案
`charAt`  `equals` `contains` 

 
#### 2.StringBuilder 
在做字符串拼接的时候，每次拼接，都会构建一个新的字符串，会消耗更多的资源；
StringBuilder 内容是可变的，String是不变的。

##### 构造方法
```java
public class SH{
    public static void main(String[] args){
        StringBuilder sb = new StringBuilder("hello"); // string 转stringBuilder
        sb.append(", java!"); 
        System.out.println(sb.toString()); // StringBuilder to String 
        System.out.println(sb.reverse()); // StringBuilder reversed , return this
    }
}
```

### 3. ArrayList 
是数组，但是数组的大小可以调整，而且实现了List的方法
`extends AbstractList implements List ...`
##### 特点：
+ ArrayList里面可以放任意数据类型的元素，但是元素类型相同；
+ 元素个数可以调整；
+ 因为实现了list的方法，所以可以使用list定义的方法；

```java
import java.util.ArrayList;
import java.util.Scanner;

public class ArrayListDemo {

    public static void main(String[] args) {
        ArrayList<String> students = new ArrayList<String>();
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i < 3; i++) {
            System.out.printf("请输入第%d个同学的名称：\n", i);
            students.add(sc.nextLine());
        }
        System.out.println(students);
        System.out.println(students.contains("zoe"));
        students.set(0, "sue");
        students.remove(students.size() - 1);
        System.out.println(students);
        System.out.println(students.get(0));
        // ArrayList初始化，并赋值
        ArrayList<String> tableNames = new ArrayList<String>(){{
            add("hive");
            add("spark");
            add("presto");
        }};
        System.out.println(tableNames);

    }
}
```





