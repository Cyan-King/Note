

# day15

## String 类
![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410641470.png)
## String类的特点：
* 字符串对象一旦初始化就不会被改变。



String类中equals复写Object中的equals建立了String类自己的判断字符串对象是否相同的依据
返回字符串的长度  

* 按照面向对象的思想对字符串功能分类
     * “abcd”  
       1.获取：  
     * 1.1获取字符串中字符的个数（长度）。
     * int length();
     * 1.2根据位置获取字符
     * char charAt(int index);
     * 1.3根据字符获取在字符串中的位置
     ```
          int indexOf(int ch); 
          int indexOf(int ch, int fromIndex);
          从指定位置进行ch的第一次出现位置
          int indexOf(String str);
          int indexOf(String str, int fromIndex);
         int indexOf(String str, int fromIndex);
          根据字符串回去在字符串中的第一次出现的位置
          int lastIndexOf(int ch);
          int lastIndexOf(int ch, int fromIndex);
          从指定位置进行ch的第一次出现的位置
         int lastIndexOf(String str);
         int lastIndexIf(String str, int fromIndex);
     ```
     ![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410678484.png)

     根据字符获取字符在字符串中的位置  
     ![1523410805068](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410805068.png)

     ![1523410821619](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410821619.png)

     ![1523410839342](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410839342.png)

     2.转换。
      2.1 将字符串变成字符串数组（字符串的切割）

 * String[] (String regex);涉及到正则表达式

 * 2.2 将字符串变成字符数组。

 * char[] toCHarArray();

 * 2.3 将字符串变成字节数组

 * byte[] getBytes();

 * 2.4  将字符串中的字母转成大小写。

 * String toUpperCase();大写

 * String toLowerCase();小写

 * 2.5 将字符串中的内容进行替换

 * String replace(char ch, char ch);
    ![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410872355.png)
    ![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410883029.png)
    3.判断

 * 3.1 两个字符串内容是否相同啊？

 * boolean equals(Object obj);

 * boolean equalsIgnireCase(String str);忽略大小写比较字符串内容

 * 3.2 字符串中是否包含指定字符串？

 * boolean contains(String str);

 * 3.3 字符串是否以指定字符串开头，是否以指定字符串结尾

 * boolean startsWith(string);

 * boolean endsWith(string);


intern():对字符串池进行操作
StringBuffer
字符串缓冲区对象
* StringBuffer:就是字符串缓冲去。
 * 用于存储数据的容器。
 * 特点：
 * 1.长度是可变的。
 * 2.可以存储不同类型的数据。
 * 3.最终要转成字符串
 * 4.可以对字符串进行修改
    *
     *
 * 既然是一个容器对象，应该具备什么功能呢？
 * 1.添加：
 * StringBuffer append(data);
 * StringBuffer insert(index, data);
 * 2.删除：
 * StringBuffer delete(start, end);包含头，不包含尾
 * StringBuffer deleteChatAt(int index);删除指定的元素
 * 3.查找：
 * char charAt(index);
 * int indexOf(string);
 * int lastIndexOf(string);
 * 3.修改：
 * StringBuffer replace(start end, string)
 * void setCharAt(index, char);
    *
 * 增删改查C(create)U(update)R(read)D(delete)
    ![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410896016.png)
    StringBuilder
    jdk1.5以后出现了功能和StringBuffer一摸一样的对象。
     *
 * 不同的是：
 * StringBuffer是线程同步的。 通常用于多线程
 * StringBuilder是线程不同步的。 通常用于单线程
    *
 * jdk升级
 * 1.简化书写。
 * 2.提高效率。
 * 3.增加安全性。
    ![image](C:\Users\CYAN-K~1\AppData\Local\Temp\1523410920703.png)
    基本数据类型对象包装类。
 * 为了方便操作基本数据类型值，将其封装成了对象，在对象中定义了属性和行为丰富了该数据的操作。
 * 用于描述该对象的类就称为基本数据类型对象包装类。
    *
 * byte    Byte
 * short   Short
 * int     Integer
 * long    Long
 * float   Float
 * double  Double
 * char    Character
 * boolean Boolean
    *
 * 该包装对象主要用于剧本类型和字符串之间的转换。
    *
 * 基本类型---->字符串
 * 1.基本类型数值+""
 * 2.用String类中的静态方法valueOf(基本类型数值)；
    *
 * 字符串----->基本类型
 * 1.使用包装类中的静态方法 xxx parseXxx("xxx类型的字符串")
 * int parseInt(intstring");
 * long parseLong("longstring");
    *
 * boolean parseBoolean("booleanstring");
 * 只有Character没有parse方法

``` java
public class Helloword{
    public static void main(String[] args){
        Sysout.println.out("Hello Java!!")
    }
}
```

