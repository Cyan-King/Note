# HTML
html就是超级文本标记语言的简写，是最基础的网页语言。---html语言代码不用区分大小写。  
hr---是水平线，凡是要数据都要用标签。  
操作思想：  
为了操作数据，都需要对数据进行不同标签的封装，通过标签中的属性对封装的数据进行操作。标签就相当于一个容器。对容器中的数据进行操作，就是在不断的改变容器的属性值。
<hr>
格式：  
<标签名 属性名='属性值'>数据内容</标签名>  
<标签名 属性名='属性值' />  
列表标签：dl  

上层项目：dt---  
下层项目：dd---封装的内容是会被缩进的。有自动缩进的效果。
## 有序和无序的项目列表
有序:ol----无序ul---他们都有缩进效果
## 演示图片标签
img ---border边框---alt图片说明文字，这是在图片无法出现的时候显现。 

## 表格标签：
行的标签是tr,单元格是td，让数据按照指定的格式排列----cellpadding单元格内边距-----cellspacing单元格外边距---th加粗并剧中
## 超链接：
如果超联系没有去指定某个属性的时候超链接就是无效的这个属性就是href，当有了href属性才有了点击效果。href属性的值的不同，解析的方式也不一样。  
<hr>
如果在该值中没有指定的协议。解析是，按照默认的协议来解析改制的。默认协议是file协议，所以我们需要用指定的协议例如：http。targer="_blank";在新的窗口打开。  
<hr>
mailto,邮件协议-----thounder,迅雷自定义的协议  
做一个超链接但是不想有任何超链接效果，自定义超链接效果。  

##  框架布局
Frame---框架，写在body外面,使用frameset标签  
rows----纵向  
cols----横向
``` html
<!--分为上下两部分，上面为30%，下面为剩余部分-->
<frameset rows="30%, *">

    <frame src="top.html" />



        <frameset cols="30%, *">
            <frame src="left.html" />
            <frame src="right.html" />
        </frameset>

</frameset>
```
idea自己开了一个服务器来维护界面，所以绝对路径无法在网页里面实现出来，只有不在里面打开就可以。还有就是..是上一级+/就是可以了，再要上一级..
## 表单标签：<form>
表单标签是最常用的标签，用于与服务器端的交互。  
如果你想要多个单选按钮只能选一个的话就将name都为一个名字
``` html
选择性别：<input type="radio" name="sex" />男 <input type="radio" name="sex" checked="checked" />女
```
我们可以设置默认属性checked="checked",这样的话默认就选中某个标签。
向服务端提交我们需要name属性和value属性，若是没有的话服务端就无法我们提交的信息，所有要向服务端提交数据，表单中的组件必须有name和value属性。value记录的是客户端传给服务端的值.
### type
不管怎么样写表单必须先写好表单:form
1. 输入姓名：text
2. 输入密码：password
3. 单选：radio
4. 多选（复选框）：checkbox
5. 选择文件：file
6. 图片组件：image---具有提交效果，就是一个漂亮的提交
7. 隐藏组件：hidden---数据不需要客户端知道，但是可以将其提交服务端。
8. 按钮：button
9. 重置：reset
10. 提交数据：submit
11. 下拉菜单：select---不是在type里面，在下拉菜单里面必须使用option,在设置下拉菜单可以设置默认select="select"。
12. 文本框：textarea
### GET和POST提交的区别

1. get提交，提交的信息都显示到地址栏中。post提交的信息不显示地址中
2. get提交，对于敏感信的数据信息不安全。post提交，对于敏感信息安全
3. get提交，对于大数据不行，因为地址栏存储体积有限。post提交，可以提交大体积数据。
4. get提交，将信息封装到了请求消息的请求行中。post提交，将信息封装到请求体中。  

服务端的一个区别：如果出现将中文提交到tomcat服务器，服务器默认会用iso8859-1进行解码会出现乱码。通过iso8859-1进行编码，在用指定的中文码表解码。即可。这种方式对get提交和ost提交都有效。  
但是对于post提交方式提交的中文，还有另一种解决办法，就是直接使用服务端一个对象request对象的setCharacterEncoding方法直接设置指定的中文码表就可以将中文数据解析出来。这个方法就对请求体中的数据进行解码。  
综上所述：表单提交，建议使用post。  
### 和服务端交互的三种方式：
1. 地址栏输入url地址。get
2. 超链接。get
3. 表单。get和post  

如果在客户端进行增强型的校验（只要有一个组件内容是错误，是无法继续提交的。只有全队才可以提交）。
![image](https://note.youdao.com/yws/public/resource/26b00020bcc30ceb0bdf8962b5712f02/xmlnote/F2C169AF04E14A20B85E840B3F2FA0C1/1977)
### other
``` html
<pre></pre>保留代码的格式
<b>加粗</b>
<i>加粗<i/>
<u>加下划线</u>
X<sub>2<sub>    X<sup>2</sup>
<marquee direction = "down" behavior="slide">嘿，原来我会飞</marquee>
```
## div
div一个是封装整行区域的，span是封装一个个体提取的
### 标签分为两大类
1. 块级标签（元素）：标签结束后都有换行。div p dl table title ol ul
2. 行内标签（元素）：标签结束后没有换行。span font span img input select a