# day21
## IO字符流
作业：将C盘的一个文本文件复制到d盘  
分析：  
复制原理：  
读取C盘文件中的数据  
将这些数据写入到d盘当中。
连续带写。
文本文件复制运算图  
字符流的缓冲区
---------------------------------------------------------------------

字符流缓冲区：
BufferedReader
   :  newLine()
BufferedWriter
   :  readLine()


装饰设计模式：
   对一组对象的功能进行增强时，就可以使用该模式进行问题的解决。

装饰和继承都能实现一样的特点：进行功能的扩展增强。

有什么区别呢？

首先有一个继承体系  
Writer  
   |--TextWriter:用于操作文本  
   |--MediaWriter:用于操作媒体  

想要对操作的动作进行效率的提高  
按照面向对象，可以通过继承对具体的进行功能扩展。  
效率提高需要加入缓冲技术。

Writer  
   |--TextWriter:用于操作文本  
      |--BufferTextWriter:加入了缓冲技术  的操作文本的对象。
   |--MediaQeiter:用于操作媒体  
      |--BufferMediaWriter:  
     
​     
到这里就了。但是这样做好像不是很理想。  
如果这个体系进行功能的扩展，有多个流对象。  
那么这个流要提高效率，是不是也要产生子类呢？  是，这时就会发生只为提高功能，进行的继承。
导致继承体系越来越臃肿。不够灵活。

重新思考这个问题？
既然加入的都是同一种技术--缓冲。
前一种时让缓冲和具体的对象相结合。
可不可以将缓冲进行单独封装，那个对象需要缓冲就将那个对象和缓冲相关联。

``` Java
class Buffer{
  
   Buffer(TextWriter w)
   {}
  
   Buffer(MediaWriter w)
   {}
}
 
class Buffer extends Writer{
 
   BufferWriter(Writer w)
   {
     
   } 
 
}
```

Writer  
   |--TextWriter:用于操作文本  
   |--MediaWriter:用于操作媒体  
   |--BufferWriter:用于提高效率  

装饰比继承灵活。

特点：装饰类和被装饰类都必须所属同以接口或者父类。  
## IO字节流
InputStream          ---字节输入  
OutputStream        ---字节输出  

# day22
## IO流
键盘本身就是一个标准的输入设备。  
阻塞式方法，没有数据我们就等待  
# day23
## Properties集合
这个集合的特点：
该集合的键和值都是字符串类型
集合中的数据可以保存到流中或者可以从流中获取。

通常该集合应用于键值对形式存在的配置文件。

配置文件就是用于存储信息的文件
setProperties(String key, String value)存数据
getProperties()取数据

保存的话我们要使用store(outStream out, String comments)方法,详解的话我们可以查看API来准确的了解这个方法的功能和参数。

这个集合无法编译中文字符，最好要输入英文。。

使用store()方对文件进行关联，这样将集合键值对写到指定的文件当中
用load()方法读取文件，但是文件必须是键值对的形式。

## 自定义load()方法·  
1. 首先我们读取指定的文件
2. 再次我们遍历读取文件
3. 然后我们进行判断，因为字符串之首的是 
4. #而且不是键值对所以我们必须要进行判断
5. 使用字符串字首是否有#，若是有的话我们就
6. 可以跳过这行字符串进入下一行进行判断
7. 然后我们用分割符进分割键和值split()进行分割
8. 最后我们进行输出读取
  String [] arr = line.split(“#”);
  System.out.println(arr[0] + “::” + arr[1]);
## 修改配置文件  
修改配置文件我们首先需要：  
读取文件  
修改文件中的数据  
将修改完成的数据再次写入到文件当中  

在IO流中我们可以直接控制File类中的file对象
在修改数据的时候我们需要注意FileWriter的位置，  
因为我们要先读取数据---然后再修改数据--- 最后再将修改完的数据写入到文件当中
若是我们先做读取动作---然后做写入动作----最后做修改动作----这样做后的结果就是将要修该的数据写入到指定文件当中，将原有的数据覆盖掉，这样就不是修改了而是写入数据。

在键值少不冲突的情况下我们使用Properties，但是在键值对多的时候我们用xml文件

## PrintStream
支持各种各样的打印方法  
提供了各种数据类型的数据打印，并且保持数据的表示形式  
PrintStream不抛IOException  
printWriteStream  
printWrite:字符打印流  
构造参数：  
字符串路径 
File对象  
字节输出流  
字符输出流
为了保持数据的原有表现形式，我们可以直接使用printWrite但是这样的话我们无法保证数据的大小。
sequenceInputStream
序列流，读取流在读取完了指定的流之后再查找是否还有流来读取。

vector接口: 每个向量会试图通过维护 capacity 和 capacityIncrement 来优化存储管理。capacity 始终至少应与向量的大小相等；这个值通常比后者大些，因为随着将组件添加到向量中，其存储将按 capacityIncrement 的大小增加存储块。应用程序可以在插入大量组件前增加向量的容量；这样就减少了增加的重分配的量。

Enumeration<E>:实现 Enumeration 接口的对象，它生成一系列元素，一次生成一个。连续调用 nextElement 方法将返回一系列的连续元素。

在这里我们需要使用序列流（sequenceInputStream）来将几个文件进行合并，这样的话我们就要是有到了上面的连个接口   vertor<>和Enumeration<>  
# day24
文件的分割，我们一般都是定一个量。例如：我们要分割一个10M的文件，我们每读取2M数据写入到一个文件当中，然后再在下一个文件当中写入接下来得数据。所以·我们有几个文件我们就有几个流。
## ObjectInputStream和ObjectOutputStream
ObjectOutputStream  
对象的序列话或者序列的持久化  
能操作对象的流ObjectInputStream和ObjectOutputStream  
我们要使用序列化的对象，但是我们必须要使用Serializable接口才能使用序列化的对象，否则无法使用。  
我们要做的话将数据储存到硬盘上，使数据的生命周期持久化而不是为了解析他。  
我们是用ObjectOutputStream对象只能存储对象而无法解析对象中的数据所以  
ObjectInputStream和ObectInputStream对象只能读取ObjectOutputStream的文件  
序列化的Serializable接口的用法：用于给序列化的类加入ID号  
用于判断类和对象是否使同一个版本，若是版本不同的化，则反序列化会导致InvalidClassExecption异常  
## transient关键字： 非静态数据不想被序列化可以使用这个关键字修饰  
## RandomAccessFile
特点：  
该对象既能读又能写  
该对象内部维护了一个byte数组，并通过指针可以操作数组中的元素  
可以通过getFilePointer方法读取，并通过seek()方法设置。  
其实该对象将字节输入流和输出流进行了封装。
随机---文件---读取---写入  
该对象的源或者目的只能是文件，通过构造函数就可以看出。  
如果文件存在，不创建，如果文件不存在，创建
通过seek()设置指针的位置，通过这个方法我们就可以随机的读取。  
文件不会被覆盖，那这样的话文件会被写到哪里去了？  
它覆盖的是前面的那些数组角标的数据  
随机读取数据必须要有规律。  
## 管道流
PipedInputStream和PipedOutputStream输入输出可以直接进行链接，通过线程直接使用
需要使用多线程操作否则会出现死锁情况
用流操作基本数据对象时我们使用DataStream中的readUTF()方法读取，一定要记住要是用这个对象DataInputStream和DataOutputStream

ByteArrayOutputStream：关闭无效，此类中的方法在关闭次流后能可被调用，而不会产生任何IOException,他不读写其他设备，他只操作内存。

如果源是内存我们可以使用ByteArrayInputStream，如果目的是内存我们使用ByteArrayOutputStream。
这样的话我们就可以操作byte，char，string
## 编码表：
在实际开发中我们只用两种编码表UTF_8, GBK  
字符串à字节数组：编码  
字节数组à字符串：解码  
 编码：  
我们首先要编码的源通编码什么所以我们要有一个字符有串  
String str = “你大爷”;
在接下来我们要将字符串转化成为字节数组将其编码  
byte[] buf = str.getBytes(“utf-8”);//在这里我们将这个字符串编码成为了utf-8的格式  
解码：  
在接下来我们要将字节数组编译为字符串  
String s1 = new String(buf,”UTF-8”);  
这样就完成了一个简单的编译以及解码的过程了。  
## IO流
IO按照流分为两大类：输入流Input 输出流Output  
流按照操作数据分为字节流和字符流·
又分为读写  
读取数据是输如    Input  
写入数据是输出    Output  
分为四个顶层基类  
字节流抽象基类  
InputStream  OutputStream  
字符流抽象基类  
Reader Writer  
字节流的两个顶层父类  
IntputStream  
OutputSteam  
字符流的两个父类  
Reader----输入流  
Writer----输出流    
如果要操作文字，请有限考虑字符流  
FileWriter  
操作文件的类FileWriter  
如果文件不存在则创建一个文件  
如果文件存在则对这个文件进行覆盖  
因为文本中的字符串好存在于缓冲区中，所以我们需要是有flush()方法刷新到文本文件当中
使用close()关闭流之后就不能再次write()了。这样会产生异常，因为这个流已经关闭不在存在这些操作了。  
Windows下的换行是\r 
进行换行代码  
```
LINE_SEPARATOR  
System.getProperty(“line.separator”);
FileReader
```
在windows的读取结尾的标志是-1，因为字符的读取范围是0~65535之间，所以windows用-1来告诉我们，嘿，兄弟后面没有数据了。  
而且读取的数据都是二进制。  
读取数据的两种方法：  
不过这两种方法都使用用到了read()方法：  
第一种方法是一个一个的读取字节，read()  
第二种方法是使用字符串读取字节，read(char[] buf)---这种方法读取更加便捷和快速。不过需要先创建一个数组对象  
```
char[] buf = new char[1024];
```
若是不进行close()操作的话是无法删除文件的。  
文件的Copy  
文件的copy就是不停的进行读写操作  
先读取源（源文件）---然后再写入到指定的文件中或者可以形象的说就是目的地当中，就是这么简单。  
而我们的频繁的读写可以使用while循环去操作，这样更加的简便。  
```
while((ch = fr.read()) != -1)
while((len = fw.read(buf) != -1))
FileReader fr = new FileReader(“demo.txt”);//这句话就是关联，和源（源文件）关联上了。
```
缓冲区的原理就是在缓冲区中存储一些数据，再一个个取出来。  
装饰设计模式  
装是设计模式的本质就是和装修一样的，就是在本质上提高或者增加。

装饰和继续都可以实现一样的扩展功能。  
区别：  
流要提高效率我们会使用继承父类来增加功能，但是这样会使基础体系越来越臃肿，就不够灵活。在这个时候我们就用上了装饰设计模式。

在这里我们知道了：装饰比继承要灵活。

装饰类必须要和被装饰类所属于同一个类或者一个接口！  
## LineNumberReader
读取行号，一般用来读取.java文件
字节流  

字节流可以读取图片，音频文件  
InputStream  
available()方法可以用于读取文件的大小，也能用于读取文件，不过也只能读取小文件。并且这个方法可以分段读取，分散读取一个文件。

## OutputStream
键盘的录入
键盘的录入是系统的操作，就是获取用户在键盘上敲击的按键。
而这个功能就是System类中的in方法:System.in();
键盘录入之读取一个字节  
# 转换流对象
## InputStreamReader
这个类就是将字节转换成为字符的桥梁，转换流
又称之为解码。就是将看不懂的转换成为看的懂得。  
字节变字符  

## OutputStreamReader
这个类就是将字符转换成为字节的桥梁
字符变字节
这个可以叫做，编码。

因为在开发的时候我们不知道要使用那个对象，所以我们有了四个明确即可：

1.明确源和目的  
              源：InputStream  Reader  
              目的：OutputStream   Writer  

2.明确数据是否是纯文本数据：  
              源：         是纯文本数据：Reader  
                            不是纯文本数据：InputStream  
              目的：      是纯文本数据：Writer    
                            不是纯文本数据：OutputStream  

3.明确具体的设备
              源：        
                     硬盘：File  
                     键盘：System.in  
                     内存：数组  
                     网络：Socket流  
              目的：  
                     硬盘：File  
                     键盘：System.out  
                     内存：数组  
                     网络：Socket流  
4.明确是否有要添加额外的功能：  
              是：如果·要添加缓冲区的还就添加（buffer）

需求1：复制一个文本文件  
明确目的和源   
源：InputStream Reader  
目的：OutputStream Writer  
是否是纯文本数据  
是：  
       源：Reader(字符流)  
       目的：Writer  
明确设备  
源：硬盘：File  
目的：硬盘：File  

``` Java
FileReader fr = new FileReader(“a.txt”);
FileWriter fw = new FileWriter(“b.txt”);
```

```
是否有需求：
我要高效的(Buffer)
BufferedReader bufr = new BufferedReader(new FileReader(“a.txt”));
BufferedWriter bufw = new BufferedWriter(new FileWriter(“b.txt”));
```
需求2：键盘录入信息，把信息写到一个文本文件当中  
1.明确源和目的  
源：InputStream Reader  
目的：OutputStream Writer  
2明确是否是纯文本  
是：  
源：Reader  
目的：Writer  
3.明确设备：  
源： 键盘：System.in  
目的：     硬盘：File  

InputStream in = System.in;  
FileWriter fw = new FileWriter(“b.txt”);  
4.额外需求：  
转换：将字节流转换成文字符流  
```
InputStreamReader isr = new   InputStreamReader(System.in);  
FileWriter fw = new FileWriter(“b.txt”);  
```
我需要一个高效的程序
```
BufferedReader bufr = new BufferedReader(new InputStreamReader(System.in));
BufferedWriter bufw = new BUfferedWriter(new FileWriter(“b.txt”));
```
需求3：将一个人文本文件数据，显示在控制台  
1.明确源和目的  
       源：InputStream Reader  
       目的：OutputStream Writer  
2.明确是否是纯文本  
       是  
源：Reader  
目的：Writer  
3.明确设备  
源：硬盘：Fille  
目的：控制台：System.out  
 ```
FileReader fr = new FileReader(“a.txt”);
OutputStream os = new OutputStream(System.out);
 ```
4.是否需要额外需求  
需要转换： 
```
FileReader fr = new FileReader(“a.txt“);
OutputStreamWriter osw = new OutputStreamWriter(System.out));
```
添加需求，高效(Buffer)：
```
BufferedReader bufr = new BufferedReader(new FileReader(“a.txt”));
BufferedWriter bufw = new BufferedWriter(new OutputStreamWriter(System.out))
```
需求4：将键盘录入的数据显示在控制台上  
1明确源和目标  
       源：InputStream Reader  
       目的：OutputStream Writer  
2.明确是否是纯文本文件  
       是  
       源：Reader  
       目标：Writer  
3.明确设备  
源：键盘：SyStem.out  
目的：控制台：System.out  
 ```
InputStream in = System.in;
OutputStream out = System.out;
 ```
4.明确是否需要添加额外功能：  
        需要添加，转化：  
```
InputStreamReader isr = new InputStreamReader(System.in);
OutputStreamWriter osw = new OutputStreamaWriter(System.out);
```
       需要添加功能，高效的输入输出
```
BufferedReader bufr = new BufferedReader(new InputStreamReader(System.in));
BufferedWriter bufw = new BufferedWriter(ne OutputStreamWriter(System.out));
```
转换流的解码表在中文解码表中，一个文字就是2个字节。  
FileWriter:其实默认指定了转换流的默认码表，而这个默认的子对象，可以很方便的操作文本文件.  
简单的来说FileWriter就是：本机自带的编码表+操作文件的字节流。  
如果操作文本文件明确的要使用那个编码表的的话，FileWriter就不能使用了必须使用转换流。  
如果指定了编码表要用转换流来读取文本文件，而且还要是字节流对象InputStream,OutputStream  
什么时候使用转换流：  
源和目的对应的设备是字节流时，我们要操作的是文本数据，我可以用转换流做为桥梁，而这样可以提高操作效率。  
要操作的文本数据有指定的编码表，在这个时候我们必须是有转换流。  
字符流有六个：两个文件的，两个Buffer,还有两个转换的  
字节流有四个：两个文件的，两个Buffer  
# File类
这是一个将文件和文件夹封装的类。

File类中自带分割符的字段

File的功能：  
获取：  
创建和删除：createAnddelete  
判断：
重命名：  
renameTo  
调用File中的list方法封装的必须要是目录
在这里我们有到了文件的过滤器是外部的接口我们可以使用过滤器，过滤出我们想要的东西，例如：过滤后缀名，还有隐藏文件之类的  
## 递归
自己调用自己，这种编程手法我们称之为递归。
我们可以想象递归就是循环调用某几个方法吗？  
其实递归就是直接或者调用自身，或者我们也可以说是递归就是重复使用某个功能，参与运算的结果与上次有关！
递归图样)
## Properties集合