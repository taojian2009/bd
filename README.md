# bd

1. Math

在java.lang下，不需要导包，属性和方法都是static,可以直接访问

方法	描述
abs()	获取绝对值
ceil()	向上取整，返回double
floor()	向下取整，返回double
round()	四舍五入取整
max()	取最大值
random()	返回double类型随机数，[0.0, 1.0]
2. System

在java.lang下，不需要导包；

方法	说明
exit()	终止当前运行的java虚拟机，非零表示异常终止
currentTimeMillis	返回当前时间
getEnv()	获取当前的环境变量
3. Object

在java.lang下； Object类是所有类的祖宗类，所有类都继承至Object类

方法	说明
equals()	object里面的默认是比较地址是否相同，需要比较内容的话，可以重写方法，可自动生成
toString()	toString方法返回一个“textually代表”这个对象的字符串， 建议所有子类都重写该方法
    @Override
    public String toString() {
        // string concat 方法， overwrite toString方法
        return this.getName().concat("'s age is :").concat(String.valueOf(this.getAge()));
    }


    @Override
    public boolean equals(Object o) {
        // 地址是否相同，相同的话，return true;
        if (this == o) return true;
        // 判断两个对象是否来至同一个类，如果不是，return false 
        if (o == null || getClass() != o.getClass()) return false;
        // 将o强制转型为Student
        Student student = (Student) o;
        // 比较student和当前类的属性是否相同
        return age == student.age &&
                name.equals(student.name);
    }
4. Arrays

4.1 冒泡排序

package SortDemo;

import java.util.Arrays;

public class SortDemo {
    public static void main(String[] args) {
        int[] a = {12, 34, 23, 11, 545};
        // arrays排序
        Arrays.sort(a);
        // 冒号排序
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a.length - i - 1; j++) {
                if (a[j] > a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
        // 打印array
        System.out.println(Arrays.toString(a));
    }
}

4.2 Arrays类

该类包含用于操作数组的各种方法（如排序和搜索）。 该类还包含一个静态工厂，可以将数组视为列表。

方法	说明
toString()	Arrays.toString(a)
sort()	Arrays.sort(a)
工具类，一般构造方法用Private 修饰，成员方法一般用public static修饰

5. 基本类型包装类

Integer.MAX_VALUE 
基本类型包装类的操作：

用于基本类型和字符串之间的转换
5.1 Integer

Integer i = 123; // 初始化integer 类
Integer j = Integer.valueOf('123');
int和string相互转换

        int number = 100;
        //# 1 convert int to string;
        String numStr = "" + number;
        System.out.println(numStr);
        // #2 string.valueOf() 
        String numStr1 = String.valueOf(number);  // 推荐
        System.out.println(numStr1);
        // #3 parseInt from string 返回int 
        String s = "100";
				int si = Integer.valueOf(s).intValue()
        int si = Integer.parseInt(s); // 推荐
string 数字 排序

        // 字符串排序
        String nums = "97 27 46 38 50";
        String[] numbers = nums.split(" ");
        int[] values = new int[numbers.length];
        for (int j = 0; j < numbers.length; j++) {
            values[j] = Integer.parseInt(numbers[j]);
        }
        Arrays.sort(values);
        StringBuilder sb = new StringBuilder();
        for(int value: values){
            sb.append(value);
            sb.append(" ");
        }
        System.out.println(sb);
自动装箱和拆箱

// 自动装箱
Integer i = 100; //自动装箱
Integer ii = Integer.valueOf(100); 

// 自动拆箱
Integer in = 12; // can not be null 
in += 200; //自动拆箱和装箱, 最好先判断是否为null
6. Date

已知直接子类：Date, Time, Timestamp

初始化：

        Date today = new Date();
        System.out.println(today);
        Date startDate = new Date(1000242);
        System.out.println(startDate);
方法:

getTime()

SimpleDateFormat

        Date d = new Date();
        String format = "yyyy-MM-dd HH:mm:ss";
        SimpleDateFormat sdf = new SimpleDateFormat(format);
        String s = sdf.format(d);
        System.out.println(s);
        // string to date
        String ds = "2020-12-05 18:12:35";
        Date dd = sdf.parse(ds);
        sdf.applyPattern("yyyy-MM-dd");
        System.out.println(sdf.format(dd));
package DateDemo;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class DateUtils {

    private final static String FORMAT = "yyyy-MM-dd";
    private DateUtils() {
	  // 构造方法private 
    }

    public static String format(Date date) {
        SimpleDateFormat sdf = new SimpleDateFormat(FORMAT);
        return sdf.format(date);
    }

    public static Date parseDate(String dateString) throws ParseException {
        SimpleDateFormat sdf = new SimpleDateFormat(FORMAT);
        return sdf.parse(dateString);
    }
}

7. Calendar

抽象类

获取某年某月有多少天

    public static int getMonthDays(int year, int month) {
        Calendar c = Calendar.getInstance();
        c.set(year, month, 0);
        return c.get(Calendar.DAY_OF_MONTH);
    }
