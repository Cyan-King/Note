在脚本片段中定义的变量是全局变量，在方法片段中中定义的变量是局部变量。  

# Object对象
toString():将对象变成字符串。  
自定义String()方法， 去除字符串两端的空格。
1. 定义两个变量，一个记录开始，一个记录结束。
2. 从开始进行判断是否是空格，如果是空格就进行递增，知道不是空格为止。
3. 从结束进行判断是否是空格，如果是空格就进行递减，直到不是空格为止。
4. 必须保证开始<=结束，这样才可以进行截取。
## prototype属性
## 原型
原型：就是该对象的一个描述，该描述中如果添加了一个新功能。那么该功能都会具备这些新功能，而prototype就可以获取到这个原型对象。通过prototype就可以对对象的功能进行扩展。
## 常见对象Array
我们使用concat()对两个数组进行连结
join()方法
```
myJoin(arr, separator){
    var str = "";
    for(var x = 0; x < arr.length; x++){
        if(x!=arr.length-1){
            str += arr[x] + separator;
        }
        else{
            str += arr[x];
        }
    }
    return str;
}
```
移除数组中的元素，并返回该元素。pop  
shift();//删除并返回第一个元素
splice()//删除元素并可以进行元素的替换
```
var arr = [];
    // arr.unshift("abc1", "abc2", "abc3");
    //这是压栈动作，一个一个向下压存
    arr.unshift("abc1");
    arr.unshift("abc2");
    arr.unshift("abc3");
    println(arr);

    //释放从下面释放堆栈中的数据
    /*println(arr.pop());
    println(arr.pop());
    println(arr.pop());*/

    //从上到下释放堆栈中的数据
    println(arr.shift());
    println(arr.shift());
    println(arr.shift());
```
## date
getDate---月的天数-----getDay----星期的天数---gettime----用于转换秒数  
parse方法是一个静态方法，可以用/或者-来分割，不过格式应该是（月/日/年）  
为了简化对象调用内容的书写。可以使用js中的特有语句with来完成。  
格式：  
with(对象)
{
    在该区域中可以直接使。用指定的对象的内容.不需要写对象
}
```
var date = new Date();
with(date){
    var year = getFullYear();
    var month = getMonth()+1;
    var day = getDate();
    var week = getDay();
    var hour = getHours();
    var minute = getMinutes();
    var second = getSeconds();

    println(getweek(week));
}
```
## Math对象
ceil--返回大于等于附近最小的一个整数  
floor--返回小于等于附近最大的一个整数  
round--四舍五入
pow(num1,num2);----num1^num2，num1的num2次方  
parseInt()---是一个全局方法
```
for(变量 in 对象)//对对象进行变量的语句。
{
    
}
```
## js自定义对象
如果想自定义对象，应该先对对象进行描述。js是基于对象。  
对象调用成员有两种方式：对象.属性------对象["属性名"] 
 ```
 var myMap = {
     names={{name1:"Mikl"},{myname:"Jack"}
 }
 
 println(myMap.names[0].name1);
 
 //好处在于每个对象都可以取名字，而且很好的分辨
 ```