行颜色以及间隔显示  
全选状态---按钮全选：全选---反选---取消全选

```
for (var x = 0; x < collMailNodes.length; x++){
    if(num > 1){
        collMailNodes[x].checked = !collMailNodes[x].checked;
    }
    else{
    //num接下来就只剩0和1了，在计算机中0就是真非0就是假
        collMailNodes[x].checked = num;
    }
}
```
display:none-----不显示 
```
var oDiv2Node = document.getElementById("div_2");
        if (node.value == "yes"){
            oDiv2Node.style.display = "block"
        }else {
            oDiv2Node.style.display = "none";
        }
```
 ## 性格调查：
  1. 判断是否又答案被选中，获取所有no1的radio,并比例判断checked状态 ，如果选中了我们要记录value的值
 ## 点击按钮改变颜色
所以我们我要获取这个按钮的赋值属性的颜色然后赋给文本框的颜色  
下拉菜单的事件是--onchange  
首先我们要获取所有的select中的option节点，所以我们要使用options[]方法，然后我们要获取select的选中状态，直白的说就是获取老子选中哪个？在这里我们就要使用selectedIndex方法，我们就可拿到我们想要的所有节点中的值然后改变颜色
## 省份和城市的下拉选框
1. 获取两个下拉菜单对象
2. 获取到底选择的是那个省。
3. 通过角标到容器获取相对应的城市数组
4. 清空子菜单中的内容
5. 遍历这个数组，并将这个数组的元素封装成option对象。添加到子菜单中

## 表单验证
<form>---------------------</form>----是表单的标签
怎样提交表单----onblur---
使用正则表达式我们要使用test()方法来运行正则表达式reg.test(name)
```
re = new regExp("pattern",["flags"]);
flags---是一个参数
有----g----*（全文查找出现的所有pattern）
i-----（忽略大小写）
m------（多行查找）
限定头尾^()$
```
提交事件----onsubmit--这是一个提交事件

确认密码事件：
1. 获取密码框内容
2. 获取确认密码框内容
3. 获取确认密码的span区域
4. 进行密码相同判断