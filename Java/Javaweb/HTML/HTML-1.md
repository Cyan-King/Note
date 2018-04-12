1. - 标签相当于一个容器，想要修改容器内数据的样式，只需要改变容器的属性值，就可以实现容器内数据样式的变化。  

     ## html常用的标签
     1. 文字标签和注释标签
     2. ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/51C5ABAC2B184B60AD0158945BFE1986/3706)  
     3. ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/3C30E6EC698B4494BE3C853A2ABFA581/3715)

     ### 无序列表的type属性
     type:空心圆circle----实心圆disc----s实心方块square------默认disc

     ###  图像标签
     alt:图片上显示的文字，把鼠标移动到图片上，提留片刻显示内容 
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/3C30E6EC698B4494BE3C853A2ABFA581/3715)

     ### 路径的介绍
     #### 分类：两类
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/6F689648082247ED9CE881DE372A57A0/3728)
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/E1B43B26BC2546C8BAFFA23D27B4B20E/3734)
     <hr/>
     自动缩进用dl--dd==dt的列表标签，这边标签分为上层标签和小层标签

     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/F4927D0C752649F0BFFFCDE49EF81A55/3747)

     ### 超链接标签
       1. href：链接的资源的地址
       2. target：设置打开的方式
         1. _blank:在另一个页面打开
         2. _self:在当前页面打开，这是默认属性 

     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/A8AC84EDEEC6421EA57D6279EE2EF3A7/3769)
     <pre>
     .pre---这个是原样输出标签
     </pre>
     ### 定位资源
     ``` html
     如果我们要定位资源，就是定位一个位置，我们先要个这个链接标签定义一个名字---name
     <a name="top">顶部</a>
     --------------------------------
     --------------------------------
     --------------------------------
     --------------------------------
     <a href="#top">回到顶部</a>
     ```
     ### 表格标签
     可以对数据格式化
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/345499C86F3F49C38D3F4C23E4A4F3AE/3801)
     cellspacing = 0;------这是消除单元格中的间隙，其实不是姿势使表格和单元个的间隙为0
     - border：表格线
     - bordercolor:表格线颜色
     - cellspacing:单元格直接的距离
     - width：表格宽度
     - height：表格高度
     - th：可以实现剧中和加粗
     - Rowspan:跨行单元格合并
     - colspan:跨列单元格合并

     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/1ECE89EBE9F3476D87BD63923B881828/3826)


     ### 表单标签
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/1008E04D6F3A4D079E26A1D789796CFC/3832)

     <h2>我们提交达到的值是从value的属性值中的到的</h2>

     #### 文件输入项
     ```html
     <input type="file" />
     ```

     #### 下拉选择框 (不是input里面的标签)
     ```html
     <select name="birth">
     <option value="1997">1997</option>
     <option value="1998">1998</option>
     <option value="1999">1999</option>
     </select>
     ```

     #### 文本域
     ``` html
     <textArea></textArea>
     ```

     #### 隐藏像 （不会出现在页面上，但是在htm代码里面）
     ``` html
     <input type="hidden" />
     ```

     ##### 提交按钮
     subimt

     <h2>需要提交的话我们使用action,提交指定的页面</h2>
     <h2>method: 表单的提交方式</h2>

     ### get和post的区别（笔试题目）
     1. get请求地址栏会携带提交的数据，post不会携带
     2. get请求的安全级别较高，post安全级别较高
     3. get请求数据大小的限制，post没有限制

     #### enctype:一般请求不需要这个属性，做文件上传时候需要设置这个属性！

     ### 使用图片提交
     ``` html
     <input type="image" src="filepath" />
     ```

     ``` html
     几个默认选项
     checked = "checked"
     selected = "se;ected"
     ```

     #### 重置按钮
     reset-------重置按钮

     #### 普通按钮
     button--------普通按钮

     ### 案例效果图
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/16DE59E0D7FE479D85E57234457158A1/3912)

     ### 表单案例效果图---2
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/A07C245F2B744B9382489E3E34C0FF9A/3916)

     ### html中的其他的常用标签的使用
     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/6E6D1199E5AE4A1681B1813682FF1CCA/3926)

     ### html头标签的使用
     ``` html
     <meat http-equiv="refresh" content="3, http://baidu.com" />
     实行一页面的跳转---3秒后跳转
     ```
     base标签------设置超链接属性----<base traget="blank" />可以同一的设置标签的打开方式  
     link标签：可以引入外部文件

     ### 框架标签
     ```
     <frameset>
         - rows:按照行进行划分
             <frameset rows="80, *">
         
         -cols：按照列进行划分
             <frameset cols="80, *">
             
     </frameset>



     使用框架标签时候，不能写到bodu里面，只能把body去掉
     ```

     [这里有代码示例在，在GitHub里面，之前做过这个](https://github.com/Cyan-King/SE_web/tree/master/day29/Frame)

     ![image](https://note.youdao.com/yws/public/resource/46763b505c2780ccbc57b46ba78da559/xmlnote/857F048EBE704A60BE059C1FED2930A2/3964)

