## debug的调试模式(断点调试模式)
![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/4BE55166024843D78C1E9402D83F51F8/5618)
 - debug另外一个用途
    - 查看程序的源码
    - F5 step into：进入到方法
    - F7 step return:返回

## junit的使用
idea也是自带了junit jar包的-----还有我们将普通文件夹转换成为源文件夹：ctrl + Shift + Alt + s-----然后选择Modules---Sources---这样就可以键成源代码文件夹

### @Test:表示方法进行单元测试
![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/F00341D4132E42E8A90A3F63CCFC79DB/5658)
### @Ignore:表示这个方法不进行单元测试
### @Before:在每个方法之前运行----注意是每个方法之前都运行哦
### @After:在每个方法之后运行-----注意是每个方法之后都运行哦
### 断言
    - Assert.assertEquals("测试期望的值", "方法运行的实际的值")

## 泛型的简介
<h3>泛型规范数据类型</h3>
## 为什么要使用泛型？
一般使用在集合上，比如现在把一个字符串类型的值放入到集合里面，这个时候，这个值放入到集合之后，失去本生的类型，只能是object类型，这个时候，比如想要对这个值进行类型转换，很容易出现类型转换错误，怎么解决这个问题，可以使用过泛型来解决。  
### 在集合上如何使用泛型
 - 常用集合 list set map
 - 泛型语法 集合<String> 比如 List<String>
 - ArrayList linkedList Vector
#### list集合的三种遍历方式
分别使用了普通for循环，迭代器，增强for
 - 普通for循环
 ```
  for (int i = 0; i < list.size(); i++){
            String s = list.get(i);
            System.out.println(s);
        }
 ```
  - 迭代器
 ```
 Iterator<String> iterator = list.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next
        }
 ```
 - 增强for
 ```
 for (String s1:list) {
            System.out.println(s1);
        }
 ```
 #### Set集合
 Set集合的特点：
  1. 集合是无序的
  2. 集合中的元素是不重复的

Set集合的两种遍历反射光hi
1. 增强for循环
2. 迭代器遍历

#### Map集合
map结构：key-value-----map添加数据使用put  
map的两种遍历方式：
1. 获取所有的key，通过key得到value 使用get方法 
2. 获取key和value的关系-----使用entrySet()方法----使用getKey()方法和getValue()方法可以获取key和value的值

泛型中不能写数据类型，只能写对象
![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/D882A347C9384244922357C8196AF297/5762)

## 枚举
枚举：需要一定范围内的值，而我们取得值就是在这个范围内中任意取的那一个值  
实现场景：就是交通信号灯，这个有三种信号灯，但是每次只能亮其中一种灯  
构造函数私有化：private Color2(){}  
使用关键字enum来实现枚举
```
enum Color3{
    RED, GREEN, YELLOW;
}
```
特殊的枚举操作
 - 在枚举类里面有构造方法
    - 构造方法里面有参数，需要在每个实例上面都写参数
 - 在枚举类里面有抽象方法
    - 当在枚举里面写了抽象方法之后，需要在每个实现上面都实现抽象方法

 - 得到枚举名称------使用name()方法获取枚举名
 - 得到枚举下标------使用ordinal()方法

![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/5260135E8625471299F0B69B64B91448/5821)

## 静态导入
可以在代码里面，直接使用静态带入方式，导入静态方法或者常量----------import static XX.xxx.xxxx----(packagePATH)
## 自动拆装箱
### 拆箱
 - 把基本的数据类型转换成包装类
```
 int m = i;
//jdk1.4版本的拆箱
int a = i.intValue();
```
### 装箱
 - 把包装类转黄成基本的数据类型
 ```
 Integer i = 10;
 
 Integer i = new Integer(10);
 ```
 ![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/8C99FBE689064893AD10A2D2FF985898/5846)

 ## 增强for循环 
 增强for的出现就是为了替代迭代器------增强for的底层就是迭代器  
 使用的常见：数组-----实现了Iterable接口的集合可以使用增强for循环-----list set 实现了Iterator接口map不能使用增强for循环，没有实现Itearable接口所以不能使用增强for循环

 ## 可变参数
 可变参数的应用场景：实现两个数的相加，实现三个数的相加，实现四个数的相加-----------如果实现的多个方法，这些方法里面逻辑基本相同，唯一不同的事传递的参数的个数，可以使用可变参数。
 ```
 public void add1(int...nums){
      
 }
 ```
 注意的地方：
  1. 可变参数需要卸载方法的参数列表中，不能单独定义
  2. 在方法的参数列表中只能定义一个可变参数
  3. 方法的参数列表中可变参数必须放到最后面-------add(int a, int...nums)

## 反射
### 反射的原理
框架底层的实现，而框架的底层就是用反射来实现的  
应用在一些通用性比较高的代码中。后面学到的框架，大多数都是使用反射来实现的
![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/70AC11B6F1884A309887390CC73C3F29/5883)
设置可以操控私用属性我们使用setAccesssible(boolean)方法来执行  
有参构造方法getConstructor(String.class,String.class)
![image](https://note.youdao.com/yws/public/resource/3456951011673f59d481d505d5c96d48/xmlnote/3629446E3D374727AF8FBB448E185FA2/5912)