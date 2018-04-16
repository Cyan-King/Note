## bom对象

bom：broswer object model : 浏览器对象模型
![image](https://note.youdao.com/yws/public/resource/c4ee8f26251f3c03acf20a6f62fe79de/xmlnote/B395C36A0B784E3D951E47AFE7A8ED48/4309)
<h2>[location.href----------代码](https://github.com/Cyan-King/SE_web/blob/master/DOM/bom_location.html)</h2>

上一个页面使用history.back(),下一个页面使用history.forward()
![image](https://note.youdao.com/yws/public/resource/c4ee8f26251f3c03acf20a6f62fe79de/xmlnote/363F84B63D4E41DDBE024F205B901546/4318)
<h2>[history----代码](https://github.com/Cyan-King/SE_web/tree/master/DOM/history)</h2>

### window
1. 窗口对象
2. 顶层对象（所用的bom对象都是在window里面操作的）
    1. 方法
        1. window.alert() : 页面弹出一个框，显示内容
        2. confirm() : 确认框
        3. prompt() : 输入的对话框
            1. window.prompt("please input : ", "0");
            2. window.rpompt("在显示的内容","输入框里面的默认值");
        4. open() : 打开一个新的窗口
            1. open("打开的新窗口的地址url", "", "窗口特征，比如窗口宽度和高度")
            2. 创建一个按钮，点击这个按钮，打开一个新的窗口
            3. window.open("http://www.baidu.com","","width=200, height=100");
        5. close():关闭窗口(浏览器兼容性比较差)
            1. window.close()
        6. 做定时器
            1. setInterval("js代码", 毫秒值)
            2. setTimeout()
                1. 表示在毫秒数之后执行，但是这个只是执行一次
        7. clearInterVal():清除setInterVal设置的定时器
        8. clearTimeout():清除setTimeout设置的定时器
        9. <h2>[窗体案例的示例代码----window](https://github.com/Cyan-King/SE_web/blob/master/day33_DOM/method/DOM_Window_method.html)</h2>

## js的dom对象

dom： document object model:文档对象模型  
文档：超文本文档（超文本标记文档）html, xml  
对象：提供了属性和方法  
模型：使用属性和方法操作超文本标记型文档  
可以使用js里面的dom里面提供的对象，使用这些对象的属性和方法，对标记型文档进行操作  
想要对标记型文档进行操作，首先需要对标记型文档里面的所有属性进行封装成对象，需要把html里面的标签，属性，文本内容都封装成对象  
要向对标记型文档进行操作，必须进行解析标记型文档  
![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/2D25E56A302648CE89D8FDF5802D3C08/4431)  
解析工程： 根据html的层级结构，在内存中分配一个树形结构，需要把html中的每一个部分都封装成为对象  
1. document对象：整个文档
2. element对象： 标签对象
3. 属性对象
4. 文本对象
5. Node节点对象这个对象是这些对象的父对象，如果在对象里面找不到想要的方法，这个时候到Node对象里面去找  

DOM模型有三种：
![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/08132B3548AE4023AD3E57719F359DD8/4459)
DHTML

![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/D72E8A901DB9450B9E8D787F2426CF4C/4467)

## document对象
 getElementById():通过标签的id的属性值获得标签元素

  ![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/D72E8A901DB9450B9E8D787F2426CF4C/4467)  

  getElementsByname():通过标签的name的属性值的到标签，返回的是一个集合（数组）

  getElementsByTagName():通过标签名称的到标签元素  
  ![image](https://note.youdao.com/yws/public/resource/18d5568aa822693dc45649b9ade34d59/xmlnote/B9BF71BB72A3404F93084B4FF33B6F0C/4498)

  ## windows案例
    1. 创建一个页面
        1. 有两个输入框和一个按钮
        2. 按钮上有一个时间，弹出一个窗体：使用open
      2. 创建弹出的页面
        1. 表格
        2. 每一行都有一个按钮，一个编号，一个姓名
        3. 每个按钮都有一个点击事件：把当前的编号和姓名，赋值到第一个页面相应的位置。----需要使用window.opener