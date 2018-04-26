 - # schema约束

   dtd语法 <!ELEMENTS 元素名称 约束>
   schema符合xml1的语法，xml语句
   一个xml中可以又多个schema,多个schema使用名称空间区分（类似于java包名）
   dtd里面有PCDATA类型，但是在schema里面可以支持更多的数据类型---比如 年龄 只能是整数，在schema可以直接定义一个整数类型
   schema语法更加复杂，schema目前不能替代dtd

   ## schema的快速入门

   创建一个schema文件，后缀名是xsd ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/771C6085578648B180E6A25C4D7C2AE8/5337)

   ## schema步骤

   1. 看xml中有多少个元素---<element>
   2. 看是简单元素和复杂元素

   ```
   如果是复杂元素
   <complexType>
       <sequence>
           子元素
       </squence>
   </complexType>
   ```

   1. 简单元素，写在复杂元素的

   ```
   <element name="person">
       <complexType>
           <sequence>
               <element name="name" type="string"></element>
               <element name="age" type="int"></element>
           </sequence>
       </complexType>
   </element>
   ```

   1. 在被约束文件里面引入约束文件

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/6E287B0D33FA46278B5C53182B57B273/5382)

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/6E287B0D33FA46278B5C53182B57B273/5382)

   ```
   <sequence>:表示元素的出现的顺序
   <all>:元素只能出现一次
   <choice>:元素只能出现其中的一个
   maxOccurs="unbounded":表示元的出现次数
   <angy></any>:表示任意次数
   ```

   ```
   数据类型
   ```

   ## sax解析的原理

   解析xml有两种技术dom和sax
   根据xml的层级结果在内存中分别配一个树形结构
   把xml中标签，属性，微博v恶霸封装成对象
   sax方式：事件取动，边读边解析
   在javax.xml.parsers包里面

   - SAXParser:此类的示例可以从SAXParserFactory.newSAXParser()方法获得
     - parse(File f, DefaultHandler dh):两个参数：第一个参数：xml的路径===第二个参数：事件处理器 ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/A7CB7FFAE23149C0A83BAF503981A74F/5444)
   - SAXParserFactory:实例newInstance()方法得到
     - 当解析到开始标签时候，自动执行startElement方法
     - 当解析到文本时候，自动执行characters方法
     - 当解析结束标签的时候，自动执行endELement方法

   ### 使用jaxp的sax方式解析xml

   - sax方式不能实现增删改操作，只能进行查询操作

   1. 创建解析器工厂
   2. 使用解析器工厂创建解析器
   3. 执行parse方法
   4. 创建DefaultHandler

   ## dom4j

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/0E5FA116181B466AA7845DD7BD98B6C7/5475)

   sax解析

   1. 创建解析器--SAXReader
   2. 得到document
   3. 得到根节点-getRootElement()
   4. 得到p1---Element()---Elements()
   5. 得到p1下面的name
   6. 得到name里面的值

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/8133EF08B9C743E98F0EBD9851CDE608/5493)

   #### domj4实现添加操作

   dom4j的回写使用到了XMLWriter类，这是一个普通类是可以new的类，但是他有两个参数

   - 第一个参数是xml文件路径
   - 第二个参数是格式化代码 格式化可以用creatPretttPrint()可以有缩进的效果---这两个方法都是基于OutputFormat的静态类上面

   执行添加操作的化我们可以直接使用addElement("标签名称")方法-----而添加文本的话我们直接使用setText("文本")方法

   创建元素使用DocumentHelper类方法creatElement创建标签

   ### dom4j实现修改操作

   ### dom4j实现删除操作

   ### dom4j实现获得属性的操作

   使用attributeValue()方法可以直接得到属性值

   没有对文件内容进行修改就不需要进行回写操作

   ## 使用dom4j支持xpath的操作

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/6129A5782A38447292A0AA5AE9132C85/5545)

   ### 使用dom4j支持xpath具体操作

   ![image](https://note.youdao.com/yws/public/resource/34c5b899d9e7a6a160b12182520e2917/xmlnote/6EA141E18EB049C68F20AE14829AFACF/5557)

   ### 学生管理系统

   #### 实现添加效果

   1. 创建解析器
   2. 获得document
   3. 得到根节点
   4. 在根节点上创建stu---使用addElement()方法添加节点
   5. 在stu上依次添加id name age
   6. 在id name age上面一次添加值
   7. 进行回写操作

   #### 实现查询操作

   1. 创建解析器
   2. 得到document
   3. 获取到所有的id
   4. 返回list集合，遍历list集合
   5. 得到每一个id得节点
   6. id节点得值
   7. 判断id得值和传递得id值是否相同
   8. 如果相同，先获取id得父节点stu
   9. 通过stu获取name age值

   #### 实现删除操作

   1. 创建解析器
   2. 得到document
   3. 获取所有得id----使用xpath //id 返回list集合
   4. 遍历list集合
   5. 判断里面得id和传递得id是否相同
   6. 如果相同，把id所在得stu删除