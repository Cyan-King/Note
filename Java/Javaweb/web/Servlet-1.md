# Servlet
每一个Servlet都是唯一的，它们能处理的请求是不同的！------tomcat发送不同的请求给Servlet  
servlet的功能是:接收请求数据---处理请求---完成响应
![image](https://note.youdao.com/yws/public/resource/ff1478fb86eb6c0dce0106ba027b7bf6/xmlnote/A656FA20094A4E8ABEEFC62F03EB9BCD/6169)
## 实现Servlet的方式
实现Servlet有三种方式：
1. 实现javax.servlet.Servlet接口
2. 继承javax.servlet.GenericServlet类
3. 继承javax.servlet.http.HttpServlet类

生命周期其实就是从开始到结束之间发生的事情
 - init(ServletConfig)---他会在Servlet对象创建之后马上执行，并只执行一次----创建之后的初始化方法
 - destroy()---他会在Servilet被销毁之前调用，并且只能被调用一次-----销毁之后的释放放方法
 - service(ServletRequest request, ServletResponse response)---他会被调用多次，每次处理请求都会执行他


getServletConfig----获取Servlet的配置信息  
getServletInfo---获取Servlet的信息  
Servlet:Servlet有五个方法----有三个生命周期方法--init()---service()---destroy()  
### 特性：
 - 单例,一个类只有一个对象，当然可能存在多个servlet类
 - 线程不安全的，所以他的效率是高的

Servlet类由我们来写，单对象由服务器来创建，并且由服务器来调用相应的方法


### servletConfig

``` web.xml
<servlet>
    <servlet-name>xxxxx</servlet-name>
    <servlet-class>com.wei.Server.Aservlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>xxxxx</servlet-name>
    <url-patterm>/Aservlet<url-pattern>
</servlet-mapping>
```
一个ServletConfig对象，对应一段web.xml中Servlet的配置信息

String getServletName(),获取的是<servlet-name>中的内容   
ServletContext getServletContext():获取Servlet上下文对象    
String getInitparameter(String name):通常名称获取指定初始化参数的值  
Enumeration getInitPatameterNames():获取所有初始化参数的名称
### GenericServlet
### HttpServlet
![image](https://note.youdao.com/yws/public/resource/ff1478fb86eb6c0dce0106ba027b7bf6/xmlnote/1EAE743738CD4155A86B16558DC09347/6296)
![image](https://note.youdao.com/yws/public/resource/ff1478fb86eb6c0dce0106ba027b7bf6/xmlnote/70E2CF44BCE5498B9803B03ADE36FD18/6299)
HttpServlet虽然是一个抽象类但是他没有一个抽象方法

```
action的提交方式----必须要是这样的提交方式
action="/项目名称/Servlet路径"
action="/Javaweb_day09-1/EServ;"
```

<h3>注意事项：就是修改过xml文件之后我们就需要重新启动一下tomcat这个服务器，要不然就会出现404错误，还有get()和post()都是很重要的,表单要是不添加的话就会出现错误。值得我们注意的是servlet要使用的话我们需要在xml文件中进行添加操作，而在这个时候我们要记得重启tomcat服务器</h3>

### Servlet细节
1. 不要zaiservlet中创建成员变量，创建局部变量
2. 可以创建无状态成员
3. 可以创建有状态成员，但是只能是只读状态
4. 在服务器启动的时候完成Servlet的创建
5. url-pattern----这是一个Servlet的访问路径---一个servlet-mapping中可以有多个访问路径
6. 匹配的越详细优先级就越高

### web.xml文件的继承
1. servlet-name的优先级最低，如果一个请求没有人来处理，他就会来处理来报404

## servletcontext
一个项目中只有一个servletcontext对象，我可以再N个servlet中获取这唯一的对象，使他可以和多个servlet传输数据，再tomcat创建的时候servletContext出生，tomcat服务器关闭的时候servletcontext死亡

### servletcontext概述
servletcontext是Javaweb的四大域对象之一。  
Javaweb的四大域对象分别是：PackContext, servletRequest, HttpSession, ServletContext。------域对象的理解就是：域对象就是用来在多个servlet中传递数据。  
域对象必须要有两项功能，存数据和去数据，这是为什么呢？我们来说一说，就是这样的：我们在多个servlet中传输数据，就是将数据存储到域对象中然后另一个域对象来去，这样就可以通过域对象来做到很好的数据的传输了。  
这里我们就有这几个方法来存取数据：
![image](https://note.youdao.com/yws/public/resource/ff1478fb86eb6c0dce0106ba027b7bf6/xmlnote/231FF98DFFAA491C922E48017F3632F5/6444)
##### 使用servletContext保存数据
getAttribut----查看属性-----
```
-----使用servletContext保存数据
获取servletContext
servletContext application = this.getServletContext();
application.setAttribute("name", "张三");
------使用servletContext获取数据
servletContext application = this.getServletCOntext();
String name = (String)application.getAttribute("name");//----需要强转一下
System.out.println(name);
```
注意：一个servlet要对应一段web.xml中的servlet配置信息,刚开始就是没有添加web.xml中的配置信息，报了404错误
``` web.xml
    <servlet>
        <servlet-name>AServlet</servlet-name><!--添加servlet的名字这个可以随便去，不过我们还是要规范一点的号-->
        <servlet-class>com.wei.servlet.AServlet</servlet-class><!--这里是我们servlet的文件-->
    </servlet>
    <servlet>
        <servlet-name>BServlet</servlet-name>
        <servlet-class>com.wei.servlet.BServlet</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>AServlet</servlet-name><!--和上面的Servlet-name的名字一定要匹配-->
        <url-pattern>/AServlet</url-pattern><!--这个是servlet文件的名称记得名字之前要加斜杠哦"/"-->
    </servlet-mapping>
    <servlet-mapping>
        <servlet-name>BServlet</servlet-name>
        <url-pattern>/BServlet</url-pattern>
    </servlet-mapping>
```
##### 获取初始化参数
Servlet也可以获取初始化参数，但是是获取局部参数。一个servlet只能获取自己的初始化参数，不能获取别人的，也就是说初始化参数只为一个servlet准备。  
可以配置公共的servlet，可以给所有的servlet用，只用servletContext使用。  
我们使用到了这段代码经行初始化
``` java
    ServletContext app = this.getServletContext();
    String value = app.getInitParameter("context-name");
    System.out.println(value);
```
配置信息的话我们就使用context-param这标签初始化  
###### 获取资源的相关方法
获取路劲下的资源：
1. 得到classLoader
2. 先得到Class，再得到ClassLoader
3. 调用其getResourceAsStream(),得到InputStream