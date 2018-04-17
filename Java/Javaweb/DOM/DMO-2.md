creatElement----为指定标签创建一个元素的实例  
createTextNode-----从指定值中创建文本字符串
![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/9F93129F3B76486380FC5ED1FCE1C790/4529)

## 元素对象（Element对象）
![image](https://note.youdao.com/yws/public/resource/719c28ebc452c442013e8542238efc32/xmlnote/556D46294ECA44F88D5ED0EBD4763268/4542)
![image](https://note.youdao.com/yws/public/resource/719c28ebc452c442013e8542238efc32/xmlnote/078B193A335440FFA5BE9B6C1B66B467/4545)
![image](https://note.youdao.com/yws/public/resource/719c28ebc452c442013e8542238efc32/xmlnote/0364A8B18474456C9567A32764B45756/4547)

# Node对象
获取子标签：使用childNode属性---兼容性很差  
 获取文本：
 ![image](https://note.youdao.com/yws/public/resource/719c28ebc452c442013e8542238efc32/xmlnote/40BC360171FD4C818C4C94B741608838/4566)
 ``` DOM
 <ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
 </ul>
 ```
 父节点：ul是li的父节点-----parentNode
 子节点：il是ul的子节点
  1. childNOdes:得到所有子节点，但是兼容性很差
  2. firstChild:获取指定节点的第一个子节点
  3. lastChild:获取指定节点的最后一个子节点

## dom树
### appendChild方法：
添加子节点到末尾----特点：类似于剪切粘贴的效果[appendChild代码](https://github.com/Cyan-King/SE_web/blob/master/DOM/dom_appendChild_demo.html)  
### insertBefore(newNode, oldNode)方法：
在某个节点之前插入一个新的节点，这有两个参数：(要插入的节点，在谁之前插入)，[insertBefore代码](https://github.com/Cyan-King/SE_web/blob/master/DOM/dom_insert_demo.html)  
### removeChild方法：删除节点
### replaceChild(newNode, oldNode)方法：替换节点
不能自己替换字节，通过父节点才能进行这个替换  
cloneNode(boolean)----复制节点  
![image](https://note.youdao.com/yws/public/resource/719c28ebc452c442013e8542238efc32/xmlnote/C692D0CB8F544A1ABA0BD9E18F593DBE/4625)  
## innerHTML属性
``` DOM
var tab = "<table>"
tab += "</table>"
```
[checkbox的操作的：全选--全不选--反转---案例代码](https://github.com/Cyan-King/SE_web/blob/master/DOM/dom_checkbox.html)、
使用复选框实现全选和全不选
1. 得到上面那个复选框
2. 判断复选框是否是选中-----if条件，checked == true
3. 如果是选中，下面是全选
4. 如果不是选中，下面是选不选

5. 先获取标签元素---getElementsByTagName()
6. 判断是否被算中---selected
7. 如果选中，把选中的添加到右边去
8. 得到select2
9. 添加选中的部分-appendChild方法

### 省市联动
在这里我们用到改变事件----onchang()
创建一个数组存储数据---创建一个二维数组 

### [自动生成表格的代码](https://github.com/Cyan-King/SE_web/blob/master/day34_DOM/Demo/creatTable.html)