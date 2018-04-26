onclick:鼠标点击事件
onchange:改变内容（一般和select一起使用）  
onfocus=====得到焦点  

# XML的简介
eXtensible Markup Language:可扩展标记型语言  
标记型语言：html是标记型语言---也是使用标签来操作  
可扩展：html里面的标签是固定，每个标签都是特定的含义  
标签可以自己定义，可以写中文的标签<person></person> , <猫></猫>  
xml用途：  
html用于显示数据吗，xmml也可以显示数据（不是主要功能）  
xml主要功能，为了存储数据

![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/13F10E6D3B684DBA8D0E61B1FBF70090/4713)

用来表示生活中有关系的数据

![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/6D8EF9A778B34496B318D02D494CAA70/4722)

经常用在文件配置
1. 比如现在连接数据库，肯定知道数据库的用户名和密码，数据名称
2. 如果修改数据库的信息，不需要修改源码，只要修改配置文件就可以了

## xml的语法
1. xml的文档声明

创建一个文件 后缀名时 .xml  
如果写xml，第一步必须要有一个文档声明（写了文档声明之后，表示写xml文件的内容）
``` xml
<?xml version="1.0" encoding="utf-8"?>
<person>
    <name><张三</name>
    <age>20</age>
</person>
```
属性：
 - version:xml版本 1.0（使用）1.1
 - endcoding:xml编码: gbk utf-8 iso08859-1(不包括中文)
 - standalone: 是否需要依赖其他文件 yes/no

xml的中问乱码问题解决
 - 画图分析乱码问题
 - 保存时候的编码和设置打开的编码一致，不会出现乱码

### 标签定义
 - 标签的定义又开始就必须有结束<person></person>
 - 标签没有内容，可以在标签内结束
 - 标签可以嵌套，必须要合理嵌套
 - 合理嵌套:<a></a> <b></b>
 - 不合理嵌套：<a><b></a></b>,这种方式是不正确的。
 - 在xml中把空格和换行都当初内容来接写
``` xml
<aa>1111</aa>
<aa>
    1111
</aa>
这两段代码含义是不一样的
```
### xml中标签的名称规则
 - xml代码区分大小写：<p> <P>:这两个标签不是一样的(前面是小写标签后面是大写标签)
 - xml的标签不能以数字和下划线(_)开头：<2a> <_aa>----这样是不正确的
 - xml的标签不能以xml， XML， Xml等开头----<xmla> <xmlb> <XMMLc> 这些都是不正确的
 - 不能包含空格----不能包含冒号：<a b> <b:c>
### xml中属性的定义
 - html是标签型文档，可以有属性
 - xml也是标记型文档，可以有属性
 - <person id1 = "aaa" id2="bbb"></person>
 - 属性定义的要求
 - (1) 一个标签上可以有多个属性：<person id1 = "aaa" id2="bbb"></person>
 - (2) 属性名称不能相同：<person id1 = "aaa" id2="bbb"></person>：这是不正确的，不能有两个id1
 - (3) 属性名称和属性值之间使用= ， 属性值使用引号包起来（可以是单引号，也可以使用双引号）
 - (4) xml属性的范围规范和元素的名称规范一致
### XML中的特殊字符
 - 如果我们想要在xml中显示a < b,不能正常显示因为把<当做标签。如果就是i选哪个要显示，就需要对特殊字符进行转义 < 进行转义
  ![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/8C4370F21B4845F5B4DF2A3C51DA5BD9/4861)
### CDATA区
1. 可以解决多个字符多需要转义的操作 if(a < b && b < c && d < f)-----把这些内容放到CDATA，这样的话就不需要转义了
``` xml
<![ CDATA[<b>if(a < b && b < c && d < f)</b>]]>
```
2. 把特殊字符，当做文本内容，而不是标签

### PI指令（处理指令）
 - 可以在xml中设置样式
 - 写法： 
``` xml
<?xml-stylessheeet type="text/css" href="css路径"?>
```
 - 设置样式，只能对英文标签名称起作用，对于中文的标签名称不起作用的。
    ![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/34C951CF8E6A4B25936E6714EBB157BB/4899)

## xml的约束
为什么xml需要约束？
 - 比如现在定义一个person的xml文件，只想要这个文件里面保存人的信息，比如name， age等，但是如果在xml文件中写了一个标签<猫>，发现可以正常显示，因为符合语法规范，但是猫肯定不是人的信息，xml的标签是自定义的，需要技术老规定xml中只能出现的元素，这个时候需要约束。
 - xml的约束的技术 ---- dtd约束 和 schema约束

### dtd约束
 - 创建一个文件 后缀名 .dtd
 - 步骤：
1. 看到xml中有几个元素， 就在dtd文件中写几个<!ELEMENT>
2. 判断元素是简单元素还是复杂元素：
     - 简单元素：没有子元素
     ``` xml
     简单元素写法
     <!ELEMENT 元素名称(#PCDATA)>
     <!ELEMENT name (#PCDATA)>
     <!ELEMENT age (#PCDATA)>
     ```
     - 复杂元素：有子元素的元素
     ``` xml
     复杂元素写法
     <!ELEMENT 元素名称(子元素)>
     <!ELEMENT  person(name,age)>
     <!ELEMENT name (#PCDATA)>
     <!ELEMENT age (#PCDATA)>
     ```
     - 需要在xml文件中引入dat文件
       <!DOCTYPE 根元素名称 SYSTEM "dtd文件的路径">

![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/CFDFECC5848C4AE89C557B7EC45B8CDB/4959)

打开xml文件使用浏览器打开的，浏览器只负责校验xml语法，不辅助约束，如果想要校验xml约束，需要使用工具

### dtd的三种引入方式
1。 引入外部的dtd文件
``` dtd
<!DOCTYPE 根元素名称 SYSTEM (dtd路径)>
```
2. 内部的dtd
``` dtd
<!DOCTYPE 根元素 [
        <!ELEMENT person (name, age)>
        <!ELEMENT name (#PCDATA)>
        <!ELEMENT age (#PCDATA)>
        ]>
```
3. 使用外部的dit文件
``` dtd
<!DOCTYPE 根元素 PUBLIC "DTD名称" "DTD文档的URL">

```

### 使用dtd定义元素
 - 语法：<!ELEMENT 元素名 约束>
 - 简单元素：没有子元素的元素
    - <!ELEMENT name (#PCDATA)>
    - EMAPTY : 元素为空（没有内容）
        - <sex></sex>
    - ANY : 任意
 - 复杂元素：
    - <!ELEMENT person (name, age)>
    - <!ELEMENT 元素名称 (子元素)>
    - 表示子元素出现的次数
        - +：表示一次或者多次
        - ?：表示零次或者一次
        - *：表示零次或者多次
    - 子元素直接使用逗号隔开，表示元素出现的顺序
    - 子元素直接使用|隔开，表示元素只能出现范围里面的一个就可以了

### 使用dtd定义属性
 语法：<!ATTLIST 元素名称 属性名称 属性类型 属性的约束>  
 属性类型：
 - CDTAT:字符串
 - 枚举：表示只能在一定的范围内出现值，但是只能每次出现其中的一个
    - 红绿灯效果只能出现aa--bb--cc三种之一的一种效果
    - (aa|bb|cc)
    - #REQUIRED----表示该属性必须出现
    - #IMPLIED:属性可有可无
    - #FIXED：表示属性的取值为一个固定值。语法：#FIXED "固定值"
    - 直接值：表示属性的取值未改默认值

![image](https://note.youdao.com/yws/public/resource/60ebfdf052d60a1252c1b0929482c5dd/xmlnote/1715D9E1D4B442749E1D824D8110AA56/5091)

### 实体的定义
 - 语法：<!ENTITY 实体名称 "实体的值">
 - <!ENTITY TEST "HAHAHAH">
 - 使用实体 &实体名称; 比如&TEST
 - 注意
    - 定义实体需要卸载内部dtd里面，如果卸载外部的dtd里面，在某些浏览器下，内容得不到

### xml解析：（dom和sax解析）
#### dom解析的
#### dom解析过程
 - 根据xml的层级结构在内存中分配一个树形结构，在xml的标签，属性和文本都封装成对象
 - 缺点：如果加载过大的xml文件，就会造成内存溢出
 - 优点：很方便是实现正山改操作
#### sax解析过程：
 - 采用事件驱动，边读边解析
 - 从上到下，一行一行的解析，解析到了某一个对象，把对象名称返回、

sax：不会造成内存溢出，但是也不能进行增删改操作

## jaxp的api的查看
 - jaxp是javase的一部分
 - jaxp解析器在jdk的javax.xml.parsers包里面
    - 四个类：分别是针对dom和sax解析使用的类
    - dom：
        - DocumentBuilder:解析器类
            - 这个类是一个抽象类，不能new，此类的示例可以从DocumentBuilderFactory.newDocumentBuilder()方法获取
            - 一个方法。可以解析xml parse("XML路径")返回时Document整个文档
            - 返回的document是一个接口，父节点时Node，如果在document里面找不到想要的方法，到Note里面去找
            - 在document里面方法
                - getElementsByTagName(String tagname):这个方法可以得到标签，返回集合NodeList
                - creatElement(String tagName):创建标签
                - creatTextNode(String data):创建文本
                - appendChild(Node newChild):把文本添加到标签下面
                - removeChild(node oldChild )
        - DocumentBuilderFactory:解析器工厂
    - sax:
        - SAXParser:解析器类
        - SAXParserFactory:解析器工厂

### 使用jaxp执行查询的结构
1. 查询xml文件所有name属性的值
    - 创建解析器工厂
    - 创建解析器---根据解析器工厂创建解析器
    - 解析xml返回document----
    - 的到name元素----getElementsByTagName()
    - 遍历集合---getLength()和item()
    - 的name元素里面的值----getTextContent
2. 添加节点
    - 创建解析工厂
    - 使用解析工厂创建解析器
    - 使用解析器解析xml文件---返回document
    - 在这里我们是要添加一个标签而这个标签是在p1标签里面
    - 所以我们要获取p1的标签
    - 获取指定的p1标签
    - 创建sex标签使用creatElement()
    - 创建sex标签中的文本creatTextNode()
    - 将文本添加到sex的节点
    - 将节点添加到p1中
    - 因为以上的操作都是内存里面的操作，我们要做一个回写操作将内存中的操作写到文件中去
    - 在这里我们又使用到了一个抽象类
3. 修改节点内容
    - 在这里我们使用setTextContent()来做修改操作
4. 删除节点
    - 得到删除的节点
    - 的到要删除的父节点---得到父节点使用getparentNode方法
    - 进行删除操作使用removeChild()
5. 使用jaxp遍历节点
 - 使用递归
 - 的到根节点
 - 这样遍历下去