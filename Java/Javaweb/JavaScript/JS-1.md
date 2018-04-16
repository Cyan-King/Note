## js和html的结合方式(两种)
### 第一种
使用一个标签<script type="text/javascript">js代码</script>
## 第二种
使用script标签，引入一个外部的js文件
创建一个js文件，写js代码<script type="text/javascript" src="1.js"></script>---------使用第二种方法的时候，就不要再script标签里面写js代码了，不会执行。

## js的原始类型和声明变量
typeof----这个方法可以获取数据的数据类型
![image](https://note.youdao.com/yws/public/resource/c4ee8f26251f3c03acf20a6f62fe79de/xmlnote/3A6DE6DED3E64564B4B563182E1D1170/4076)
## js语句
java里面的语句
1. if语句
2. switch语句
3. 循环 for while do-while

![image](https://note.youdao.com/yws/public/resource/c4ee8f26251f3c03acf20a6f62fe79de/xmlnote/CDCE4FBD0BE64A32BBF80ABC21EEB3C0/4089)

i++和++i和Java里面是一样的

## 运算符

 ## 数组
 ![image](https://note.youdao.com/yws/public/resource/c4ee8f26251f3c03acf20a6f62fe79de/xmlnote/CF02000F497746F4A68DD17FA2EC058B/4099)

 ## js的函数
 ### 正常函数
 ``` Java
 在java里面定义方法
 public 返回类型void / int 方法名(参数列表){
     方法体;
     返回值;
 }
 
 public int add(int a; int c){
     int sum = a + b;
     return sum;
 }
 ```
 ### 匿名函数
 ``` JavaScript
 var add = function(参数列表){
     方法体和返回值;
 }
 
 add(参数列表);
 ```
 ### 动态函数
 ``` Javascript
 使用到js里面的一个内置对象Function
 var add = new Function(”参数列表“, "方法体，返回值 ");
 ```

 ## js的全局变量和局部变量
全局变量：在script标签里面定义一个变量，这个变量在页面中的js部分都可以使用。
* 在方法的外部是用，在方法的内部使用，在另一个script标签使用。  
  局部变量：只是在方法中和函数中可以使用的变量。
* 如果我们在方法的外部调用局部变量这样的话就会出错的，在IE中调试工具按F12

## script标签的位置存放
script---可一存放在任何的位置----html的解析方式是由上到下的--html-->title-->head-->body-->

getElementById---获取元素的id
![image](http://note.youdao.com/yws/res/4176/6380CB7A67F44897B1A1DA27E17B3BB8)
## js的重载