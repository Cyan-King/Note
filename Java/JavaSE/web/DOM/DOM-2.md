# DOM
a:link,a:visited---超链接访问前，超链接访问后  
取消超链接的默认点击效果，可以使用href设置:JavaScript:void(0)来操作  
思路：
1. 先有新闻数据，并用标签封装
2. 定义一些页面样式。
3. 确定事件源和事件，以及处理方式中被处理的节点。
    1. 事件源：a标签，事件：onclick
    2. 被处理的节点div-newstext

既然要给超链接加入自定义的事件处理，就要先取消超链接的默认点击效果。可以使用给href设置：javascript:void(0)完成。
4. 用js处理页面的行为。

功能：
1. 实现字体的大小
2. 实现字体的颜色改变  
3. 选择器class------.norm----.max-----.min

### 菜单列表 
overflow:-----
思路：
1. 标签封装数据，html
2. 定义CSS----我们在这里使用到了overflow布局
3. 明确事件源，事件，以及要处理的节点，DOM
4. 明确具体的操作方式，其实就是事件的处理内容。Javascript
    1. 将dl属性的overflow的值改成visiable即可---getElementsByTagName---获取标签节点
    2. 要先获取dl节点
    3. 改变该节点的style.overflow的属性

<hr/>

另一种方法我们直接定义一个开关class.open---class.close  
1. 先拿到dl属性的
2. 在拿到dl节点
3. 获取style中.close和.open
4. 在这里我们扩张程序，我们有很多个dl属性标签
5. 在这个判断里面我们使用的了oDLNode.className = "open"但判断，让我们可以随意的关闭列表
6. 那么我们就要明确点击对象点击的是那个标签的节点，我们就是用到了this来明确，也可以直接用1，2，3，4但是这样的话就不保险了代码的复用性就会大大的减低，容易出错
  <hr/>

7. 列表添加功能：展开一个列表的话，其他列表都关闭。

去除无序列表的样式使用 list-style:none
使用display---open:block----close---none

好友列表，实现功能：
1. 表单的展开和闭合效果
2. 要求一次只能展开一个

一次只展开一个列表标签
1. 获取所有节点
2. 遍历这些节点，对当前节点进行展开或者进行闭合操作，其他节点都进行闭合操作
```
//获取当前节点
var oDLNode = node.parentNode;
//获取所有的dl节点
var collDLNode = document.getElementsByTagName("dl ");
//遍历所有dl
```
<hr/>

在页面中创建一个5行6列的表格
1. 事件源，比如按钮
2. 必须有一个生成的表格节点存储位置

```
 //创建节点
 var oTabNode = document,crearElement("table");
 -----
 -----
 -----
 //添加节点,让这些节点有关系，进行指定层次的节点添加---由下向上添加
 oTabNode.appendChild(oTabNode);
 //获取div节点将这些节点放入到div当中去，也就是将table节点放进div节点当中
 document.getElementsByTagName('div')[0].appendChild(oTabNode);
 
```
使用表格节点对象中的方法来完成，使用insertRow()方法就完成表格对象中的行。tr是行但是table是由单元格td组成  
Row---行  
Cool---列  
5行六列
```
将表格节点添加到div中
 document.getElementsByTagName('div')[0].appendChild(oTabNode);
```
 使用disabled方法直接使按钮失去功能  
 ### 进行表的创建和删除操作
 创建方式：
 我们自由的创建表格，先要获取行和列的对象节点。  
 然后获取其中的值  
 <hr/>
 删除方式：  
 设置属性的id之类的我们使用setAttributr(name, value);  

 我们想要知道有表格这个对象才能删除，所有我们先要判断表格是否存在  

 想要获取行数，我们就要获取表格中的行的行数，所以我们要使用rows方法就可以了  

 存在的话我们使用deleteRow(num);其中的参数是角标所以要减一，这只是删除行的方法  

 而删除列就是每一行中的同一位置的单元格

 ### 设置行的间隔高亮色
  1. 因为要操作行的样式，所以要先获取表格对象
  2. 获取所有被操作的行对象
  3. 遍历并给每一行指定样式  

先加载JavaScript在加载html代码
使用显示高亮我们使用到了这两个方法：onmouseover和onmouseout

排序的方式：
1. 排序就需要数组。获取需要参与排序的行对象数组。
2. 对行数组中的每一个行的年龄单元格的数据进行比较，并完成行对象再数组中的位置置换。
3. 将排序好的数组重新添加到表格中 

```
//获取表格的对象节点
-------------------------

//获取表格中所有的行数
-------------------------

//定义一个临时容器，并将需要排序的对象存储到临时容器中
-------------------------

//遍历表格中的数据行数，并将数据存储到数组中
-------------------------

//对临时容器进行排序
-------------------------

//将排序好的对象添加进表格
-------------------------

```
### 商品全选
获取所有的名称为item的复选框  
判断checked状态，为true为选中，获取该节点value进行累加，checkboxed的状态默认为true
获取全选状态：将全选的box的checked状态赋值给所有的itembox的checked.