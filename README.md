# Java-# JAVA面试知识梳理

## 0.  java大纲

![img](https://images.gitbook.cn/f3c480e0-3be2-11e9-82f8-0f2e500ca934)

## 一、java基础

### 1.基础

#### 1.1 JDK & JRE 区别

- JDK：Java Development Kit 的简称，Java 开发工具包，提供了 Java 的开发环境和运行环境。
- JRE：Java Runtime Environment 的简称，Java 运行环境，为 Java 的运行提供了所需环境。

​       具体来说 JDK 其实包含了 JRE，同时还包含了编译 Java 源码的编译器 Javac，还包含了很多 Java 程序调试和分析的工具。简单来说：如果你需要运行 Java 程序，只需安装 JRE 就可以了，如果你需要编写 Java 程序，需要安装 JDK。

#### 1.2 java7 & java8 区别

相对于java7，Java8的新特性如下：

- 接口的默认方法；Java 8允许给接口添加一个非抽象的方法实现，只需要使用 default关键字即可，这个特征又叫做扩展方法。
- Lambda 表达式；eg：接受2个参数(数字)，并返回他们的差值  (x, y) -> x – y  
- 函数式接口；
- 方法与构造函数引用；
- Lambda 作用域；在lambda表达式中访问外层作用域和老版本的匿名对象中的方式很相似。你可以直接访问标记了final的外层局部变量，或者实例的字段以及静态变量。
- 访问局部变量；可以直接在lambda表达式中访问外层的局部变量。

**Lambda 表达式**

lambda 表达式是一个可传递的代码块， 可以在以后执行一次或多次。 lambda 表达式就是一个代码块， 以及必须传人代码的变量规范 。

#### 1.3 java applet

**(1) Java Applet 基础**

Applet 是一种 Java 程序。它一般运行在支持 Java 的 Web 浏览器内。因为它有完整的 Java API支持,所以Applet 是一个全功能的 Java 应用程序。

如下所示是独立的 Java 应用程序和 applet 程序之间重要的不同：

- Java 中 Applet 类继承了 java.applet.Applet 类。
- Applet 类没有定义 main()，所以一个 Applet 程序不会调用 main() 方法。
- Applet 被设计为嵌入在一个 HTML 页面。
- 当用户浏览包含 Applet 的 HTML 页面，Applet 的代码就被下载到用户的机器上。
- 要查看一个 Applet 需要 JVM。 JVM 可以是 Web 浏览器的一个插件，或一个独立的运行时环境。
- 用户机器上的 JVM 创建一个 Applet 类的实例，并调用 Applet 生命周期过程中的各种方法。
- Applet 有 Web 浏览器强制执行的严格的安全规则，Applet 的安全机制被称为沙箱安全。
- Applet 需要的其他类可以用 Java 归档（JAR）文件的形式下载下来。

**(2) Applet的生命周期**

Applet 类中的四个方法给我们提供了一个框架，你可以在该框架上开发小程序：

- **init:** 该方法的目的是为你的 Applet 提供所需的任何初始化。在 Applet 标记内的 param 标签被处理后调用该方法。
- **start:** 浏览器调用 init 方法后，该方法被自动调用。每当用户从其他页面返回到包含 Applet 的页面时，则调用该方法。
- **stop:** 当用户从包含 Applet 的页面移除的时候，该方法自动被调用。因此，可以在相同的 Applet 中反复调用该方法。
- **destroy:** 此方法仅当浏览器正常关闭时调用。因为 Applet 只有在 HTML 网页上有效，所以你不应该在用户离开包含 Applet 的页面后遗漏任何资源。
- **paint:** 该方法在 start() 方法之后立即被调用，或者在 Applet 需要重绘在浏览器的时候调用。paint() 方法实际上继承于 java.awt。

**(3) Applet 类**

每一个 Applet 都是 java.applet.Applet 类的子类，基础的 Applet 类提供了供衍生类调用的方法,以此来得到浏览器上下文的信息和服务。

这些方法做了如下事情：

- 得到 Applet 的参数
- 得到包含 Applet 的 HTML 文件的网络位置
- 得到 Applet 类目录的网络位置
- 打印浏览器的状态信息
- 获取一张图片
- 获取一个音频片段
- 播放一个音频片段
- 调整此 Applet 的大小

除此之外，Applet 类还提供了一个接口，该接口供 Viewer 或浏览器来获取 Applet 的信息，并且来控制 Applet 的执行。

Viewer 可能是：

- 请求 Applet 作者、版本和版权的信息
- 请求 Applet 识别的参数的描述
- 初始化 Applet
- 销毁 Applet
- 开始执行 Applet
- 结束执行 Applet

Applet 类提供了对这些方法的默认实现，这些方法可以在需要的时候重写。

**(4) Applet 的调用**

Applet 是一种 Java 程序。它一般运行在支持 Java 的 Web 浏览器内。因为它有完整的 Java API 支持,所以 Applet 是一个全功能的 Java 应用程序。

<applet> 标签是在HTML文件中嵌入 Applet 的基础。

<applet> 标签的属性指定了要运行的 Applet 类。width 和 height 用来指定 Applet 运行面板的初始大小。Applet 必须使用 </applet> 标签来关闭。

如果 Applet 接受参数，那么参数的值需要在 <param> 标签里添加，该标签位于 <applet> 和 </applet> 之间。浏览器忽略了 applet 标签之间的文本和其他标签。

不支持 Java 的浏览器不能执行 <applet> 和 </applet>。因此，在标签之间显示并且和 applet 没有关系的任何东西，在不支持的 Java 的浏览器里是可见的。

Viewer 或者浏览器在文档的位置寻找编译过的 Java 代码，要指定文档的路径，得使用 <applet> 标签的 codebase 属性指定。

**(5) 应用程序转换成 Applet**

将图形化的 Java 应用程序（是指，使用AWT的应用程序和使用 java 程序启动器启动的程序）转换成嵌入在web页面里的applet是很简单的。

下面是将应用程序转换成 Applet 的几个步骤：

- 编写一个 HTML 页面，该页面带有能加载 applet 代码的标签。
- 编写一个 JApplet 类的子类，将该类设置为 public。否则，Applet 不能被加载。
- 消除应用程序的 main()方法。不要为应用程序构造框架窗口，因为你的应用程序要显示在浏览器中。
- 将应用程序中框架窗口的构造方法里的初始化代码移到 Applet 的 init() 方法中，你不必显示的构造 Applet 对象，浏览器将通过调用 init() 方法来实例化一个对象。
- 移除对 setSize() 方法的调用，对于 Applet 来讲，大小已经通过 HTML 文件里的 width 和 height 参数设定好了。
- 移除对 setDefaultCloseOperation() 方法的调用。Applet 不能被关闭，它随着浏览器的退出而终止。
- 如果应用程序调用了 setTitle() 方法，消除对该方法的调用。applet 不能有标题栏。（当然你可以给通过 html 的 title 标签给网页自身命名）
- 不要调用 setVisible(true),Applet 是自动显示的。

**(6) 事件处理**

Applet 类从 Container 类继承了许多事件处理方法。Container 类定义了几个方法，例如：processKeyEvent() 和processMouseEvent()，用来处理特别类型的事件，还有一个捕获所有事件的方法叫做 processEvent。

为了响应一个事件，Applet 必须重写合适的事件处理方法。

#### 1.4 语法基础

**(1) == 和 equals 的区别是什么？**

**== 解读**

对于基本类型和引用类型 == 的作用效果是不同的，如下所示：

- 基本类型：比较的是值是否相同；
- 引用类型：比较的是引用是否相同；

**equals 解读**

equals 本质上就是 ==，只不过 String 和 Integer 等重写了 equals 方法，把它变成了值比较。

总结 ：== 对于基本类型来说是值比较，对于引用类型来说是比较的是引用；而 equals 默认情况下是引用比较，只是很多类重新了 equals 方法，比如 String、Integer 等把它变成了值比较，所以一般情况下 equals 比较的是值是否相等。

**(2) 两个对象的 hashCode() 相同，则 equals() 也一定为 true，对吗？**

不对，两个对象的 hashCode() 相同，equals() 不一定 true。因为在散列表中，hashCode() 相等即两个键值对的哈希值相等，然而哈希值相等，并不一定能得出键值对相等。

**(3) final 在 Java 中有什么作用？**

- final 修饰的类叫最终类，该类不能被继承。
- final 修饰的方法不能被重写。
- final 修饰的变量叫常量，常量必须初始化，初始化之后值就不能被修改。

**(4) String 属于基础的数据类型吗？**

String 不属于基础类型，基础类型有 8 种：byte、boolean、char、short、int、float、long、double，而 String 属于对象。

**(5) Java 中操作字符串都有哪些类？它们之间有什么区别？**

操作字符串的类有：String、StringBuffer、StringBuilder。

String 和 StringBuffer、StringBuilder 的区别在于 String 声明的是不可变的对象，每次操作都会生成新的 String 对象，然后将指针指向新的 String 对象，而 StringBuffer、StringBuilder 可以在原有对象的基础上进行操作，所以在经常改变字符串内容的情况下最好不要使用 String。

StringBuffer 和 StringBuilder 最大的区别在于，StringBuffer 是线程安全的，而 StringBuilder 是非线程安全的，但 StringBuilder 的性能却高于 StringBuffer，所以在单线程环境下推荐使用 StringBuilder，多线程环境下推荐使用 StringBuffer。

**(6) String str="i"与 String str=new String("i")一样吗？**

不一样，因为内存的分配方式不一样。String str="i"的方式，Java 虚拟机会将其分配到常量池中；而 String str=new String("i") 则会被分到堆内存中。

**(7) 如何将字符串反转？**

使用 StringBuilder 或者 stringBuffer 的 reverse() 方法。

**(8) String 类的常用方法都有那些？**

- indexOf()：返回指定字符的索引。
- charAt()：返回指定索引处的字符。
- replace()：字符串替换。
- trim()：去除字符串两端空白。
- split()：分割字符串，返回一个分割后的字符串数组。
- getBytes()：返回字符串的 byte 类型数组。
- length()：返回字符串长度。
- toLowerCase()：将字符串转成小写字母。
- toUpperCase()：将字符串转成大写字符。
- substring()：截取字符串。
- equals()：字符串比较。

**(9) 抽象类相关**：

抽象类不一定非要有抽象方法。

抽象类不能用final修饰。定义抽象类就是让其他类继承的，如果定义为 final 该类就不能被继承，这样彼此就会产生矛盾。

抽象类和普通类区别：

- 普通类不能包含抽象方法，抽象类可以包含抽象方法。
- 抽象类不能直接实例化，普通类可以直接实例化。

抽象类和接口区别：

- 实现：抽象类的子类使用 extends 来继承；接口必须使用 implements 来实现接口。
- 构造函数：抽象类可以有构造函数；接口不能有。
- 实现数量：类可以实现很多个接口；但是只能继承一个抽象类。
- 访问修饰符：接口中的方法默认使用 public 修饰；抽象类中的方法可以是任意访问修饰符。

**(10) Java 中 IO 流分为几种？**

按功能来分：输入流（input）、输出流（output）。

按类型来分：字节流和字符流。

字节流和字符流的区别是：字节流按 8 位传输以字节为单位输入输出数据，字符流按 16 位传输以字符为单位输入输出数据。

![img](https://www.runoob.com/wp-content/uploads/2013/12/iostream2xx.png)

**(11) BIO、NIO、AIO 有什么区别？**

- BIO：Block IO 同步阻塞式 IO，就是我们平常使用的传统 IO，它的特点是模式简单使用方便，并发处理能力低。
- NIO：Non IO 同步非阻塞 IO，是传统 IO 的升级，客户端和服务器端通过 Channel（通道）通讯，实现了多路复用。
- AIO：Asynchronous IO 是 NIO 的升级，也叫 NIO2，实现了异步非堵塞 IO ，异步 IO 的操作基于事件和回调机制。

**(12) Files的常用方法都有哪些？**

- Files. exists()：检测文件路径是否存在。
- Files. createFile()：创建文件。
- Files. createDirectory()：创建文件夹。
- Files. delete()：删除一个文件或目录。
- Files. copy()：复制文件。
- Files. move()：移动文件。
- Files. size()：查看文件个数。
- Files. read()：读取文件。
- Files. write()：写入文件。

**(13) java三大特性**

- 封装：封装指的是属性私有化，根据需要提供setter和getter方法来访问属性。即隐藏具体属性和实现细节，仅对外开放接口，控制程序中属性的访问级别。

  封装目的：增强安全性和简化编程，使用者不必在意具体实现细节，而只是通过外部接口即可访问类的成员。

- 继承：继承是指将多个相同的属性和方法提取出来，新建一个父类。Java中一个类只能继承一个父类，且只能继承访问权限非private的属性和方法。 子类可以重写父类中的方法，命名与父类中同名的属性。

  继承目的：代码复用。

- 多态：多态可以分为两种：设计时多态和运行时多态。

  设计时多态：即重载，是指Java允许方法名相同而参数不同（返回值可以相同也可以不相同）。
  运行时多态：即重写，是指Java运行根据调用该方法的类型决定调用哪个方法。

  多态目的：增加代码的灵活度。

  **总结**：Java中应尽量减少继承关系，以降低耦合度。

  使用多态时，父类在在调用方法时，优先调用子类的方法。

  如果子类没有重写父类的方法，则再调用父类的方法。

**(14) Java 重写(Override)与重载(Overload)**

**重写(Override)**

重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。**即外壳不变，核心重写！**重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。

重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。例如： 父类的一个方法申明了一个检查异常 IOException，但是在重写这个方法的时候不能抛出 Exception 异常，因为 Exception 是 IOException 的父类，只能抛出 IOException 的子类异常。

**重载(Overload)**

重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。

每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。

最常用的地方就是构造器的重载。

**(15) JavaBean是什么？**

Java语言欠缺属性、事件、多重继承功能。所以，如果要在Java程序中实现一些面向对象编程的常见需求，只能手写大量胶水代码。Java Bean正是编写这套胶水代码的惯用模式或约定。这些约定包括getXxx、setXxx、isXxx、addXxxListener、XxxEvent等。遵守上述约定的类可以用于若干工具或库。	

 JavaBean是一个遵循特定写法的Java类，它通常具有如下特点：

- 这个Java类必须具有一个无参的构造函数
- 属性必须私有化。
- 私有化的属性必须通过public类型的方法暴露给其它程序，并且方法的命名也必须遵守一定的命名规范。

JavaBean的属性可以是任意类型，并且一个JavaBean可以有多个属性。每个属性通常都需要具有相应的setter、 getter方法，setter方法称为属性修改器，getter方法称为属性访问器。
　　属性修改器必须以小写的set前缀开始，后跟属性名，且属性名的第一个字母要改为大写，例如，name属性的修改器名称为setName，password属性的修改器名称为setPassword。
　　属性访问器通常以小写的get前缀开始，后跟属性名，且属性名的第一个字母也要改为大写，例如，name属性的访问器名称为getName，password属性的访问器名称为getPassword。
　　一个JavaBean的某个属性也可以只有set方法或get方法，这样的属性通常也称之为只写、只读属性。

**(16) 下面的方法可用在 Servlet 程序中读取 HTTP 头。这些方法通过 *HttpServletRequest* 对象可用：**

- Cookie[] getCookies() ：返回一个数组，包含客户端发送该请求的所有的 Cookie 对象。
- Object getAttribute(String name)：以对象形式返回已命名属性的值，如果没有给定名称的属性存在，则返回 null。
- String getHeader(String name)：以字符串形式返回指定的请求头的值。Cookie也是头的一种；
- String getParameter(String name)：以字符串形式返回请求参数的值，或者如果参数不存在则返回 null。

### 2.容器(集合类)

#### 2.1 Java 容器有哪些

Java容器类类库的用途是保存对象，可以将其分为2个概念。

Collection 存储着对象的集合，而 Map 存储着键值对（两个对象）的映射表。

2.1.1：Collection

一个独立元素的序列，这些元素都服从一条或多条规则。其中List必须按照插入的顺序保存元素、Set不能有重复的元素、Queue按照排队规则来确定对象的产生顺序（通常也是和插入顺序相同）

2.1.2：Map

一组成对的值键对对象，允许用键来查找值。ArrayList允许我们用数字来查找值，它是将数字和对象联系在一起。而Map允许我们使用一个对象来查找某个对象，它也被称为关联数组。或者叫做字典。

java 容器分为 Collection 和 Map 两大类，其下又有很多子类，如下所示：

- **Collection**

- List
  - ArrayList ：基于动态数组实现，支持随机访问。
  - LinkedList ：基于双向链表实现，只能顺序访问，但是可以快速地在链表中间插入和删除元素。不仅如此，LinkedList 还可以用作栈、队列和双向队列。
  - Vector ：和 ArrayList 类似，但它是线程安全的。
  - Stack ：Stack 类表示后进先出（LIFO）的对象堆栈。它通过五个操作对类 Vector 进行了扩展 ，允许将向量视为堆栈。它提供了通常的 push 和 pop 操作，以及取堆栈顶点的 peek 方法、测试堆栈是否为空的 empty 方法、在堆栈中查找项并确定到堆栈顶距离的 search 方法。

- Set
  - HashSet ：基于哈希表实现，支持快速查找，但不支持有序性操作。并且失去了元素的插入顺序信息，也就是说使用 Iterator 遍历 HashSet 得到的结果是不确定的。
  - LinkedHashSet ：具有 HashSet 的查找效率，并且内部使用双向链表维护元素的插入顺序。
  - TreeSet  ：基于红黑树实现，支持有序性操作，例如根据一个范围查找元素的操作。但是查找效率不如 HashSet，HashSet 查找的时间复杂度为 O(1)，TreeSet 则为 O(logN)。

  Queue

  - LinkedList：可以用它来实现双向队列。
  - PriorityQueue：基于堆结构实现，可以用它来实现优先队列。

- **Map**

- HashMap ：基于哈希表实现。
  - LinkedHashMap ：使用双向链表来维护元素的顺序，顺序为插入顺序或者最近最少使用（LRU）顺序。

- TreeMap ：基于红黑树实现。

- ConcurrentHashMap ：底层采用分段的数组+链表实现，线程**安全**

- Hashtable ：和 HashMap 类似，但它是线程安全的，这意味着同一时刻多个线程同时写入 HashTable 不会导致数据不一致。它是遗留类，不应该去使用它，而是使用 ConcurrentHashMap 来支持线程安全，ConcurrentHashMap 的效率会更高，因为 ConcurrentHashMap 引入了分段锁。

#### 2.2 Collection 和 Collections 

- Collection 是一个集合接口，它提供了对集合对象进行基本操作的通用接口方法，所有集合都是它的子类，比如 List、Set 等。
- Collections 是一个包装类，包含了很多静态方法，不能被实例化，就像一个工具类，比如提供的排序方法： Collections. sort(list)。

在 Java 类库中，集合类的基本接口是 Collection 接口。这个接口有两个基本方法 ：add 和 iterator

add方法用于向集合中添加元素。如果添加元素确实改变了集合就返回 true, 如果集合没有发生变化就返回 false。例如， 如果试图向集中添加一个对象， 而这个对象在集中已经存在，这个添加请求就没有实效，因为集中不允许有重复的对象。
iterator方法用于返回一个实现了 Iterator 接口的对象。可以使用这个迭代器对象依次访问集合中的元素。

Iterator 接口包含 4 个方法：

 E next();
boolean hasNextO;
void remove0;
default void forEachRemaining(Consumer<? super E> action);

 通过反复调用 next 方法， 可以逐个访问集合中的每个元素。但是，如果到达了集合的末尾，next 方法将抛出一个 NoSuchElementException。 

因此，需要在调用 next 之前调用 hasNext方法。如果迭代器对象还有多个供访问的元素， 这个方法就返回true。如果想要査看集合中的所有元素，就请求一个迭代器，并在 hasNext 返回 true 时反复地调用 next 方法。

在 Java SE 8中， 甚至不用写循环。可以调用 forEachRemaining 方法并提供一 lambda表达式（它会处理一个元素）。 将对迭代器的每一个元素调用这个 lambda 表达式，直到再没有元素为止。
iterator.forEachRemai ni ng(el ement -> do something with element);  

Iterator 接口的 remove 方法将会删除上次调用 next 方法时返回的元素。在大多数情况下，在决定删除某个元素之前应该先看一下这个元素是很具有实际意义的。然而， 如果想要删除指定位置上的元素， 仍然需要越过这个元素。  

更重要的是，对 next 方法和 remove 方法的调用具有互相依赖性。如果调用 remove 之前没有调用next 将是不合法的。 如果这样做， 将会抛出一个 IllegalStateException 异常。 

如果想删除两个相邻的元素， 不能直接地这样调用：
it.remove()；
it.remove0；// Error!
相反地， 必须先调用 next 越过将要删除的元素。
it,remove() ;
it.next0；
it.remove(); // OK 

#### 2.3 List、Map、Set

**(1) 三者区别：**

List、Set、Map 的区别主要体现在两个方面：元素是否有序、是否允许元素重复。

三者之间的区别，如下表：

![img](https://images.gitbook.cn/6e7001c0-3be3-11e9-af57-196eefd310b5)

**(2) 三者存取元素的特点**：

List以特定索引来存取元素，可以有重复元素。Set不能存放重复元素（用对象的equals()方法来区分元素是否重复）。Map保存键值对（key-value pair）映射，映射关系可以是一对一或多对一。Set和Map容器都有基于哈希存储和排序树的两种实现版本，基于哈希存储的版本理论存取时间复杂度为O(1)，而基于排序树版本的实现在插入或删除元素时会按照元素或元素的键（key）构成排序树从而达到排序和去重的效果。

#### 2.4 HashMap 和 Hashtable 

**(1) HashMap的实现原理：**

HashMap 基于 Hash 算法实现的，我们通过 put(key,value)存储，get(key)来获取。当传入 key 时，HashMap 会根据 key. hashCode() 计算出 hash 值，根据 hash 值将 value 保存在 bucket 里。当计算出的 hash 值相同时，我们称之为 hash 冲突，HashMap 的做法是用链表和红黑树存储相同 hash 值的 value。当 hash 冲突的个数比较少时，使用链表否则使用红黑树。

**(2) HashMap和HashTable区别：**

HashMap和Hashtable都实现了Map接口，因此很多特性非常相似。但是，他们有以下不同点：

- 存储：HashMap 允许 key 和 value 为 null，而 Hashtable 不允许。
- 线程安全：Hashtable 是线程安全的，而 HashMap 是非线程安全的。
- 推荐使用：在 Hashtable 的类注释可以看到，Hashtable 是保留类不建议使用，推荐在单线程环境下使用 HashMap 替代，如果需要多线程使用则用 ConcurrentHashMap 替代。

#### 2.5 TreeMap

**(1) 定义**

TreeMap是一个有序的key-value集合，基于红黑树（Red-Black tree）的 NavigableMap实现。该映射根据其键的自然顺序进行排序，或者根据创建映射时提供的 Comparator进行排序，具体取决于使用的构造方法。

**(2) TreeMap的特性：**

- 根节点是黑色
- 每个节点都只能是红色或者黑色
- 每个叶节点（NIL节点，空节点）是黑色的。
- 如果一个节点是红色的，则它两个子节点都是黑色的，也就是说在一条路径上不能出现两个红色的节点。
- 从任一节点到其每个叶子的所有路径都包含相同数目的黑色节点。

**(3)如何决定使用 HashMap 还是 TreeMap？**

对于在 Map 中插入、删除、定位一个元素这类操作，HashMap 是最好的选择，因为相对而言 HashMap 的插入会更快，但如果你要对一个 key 集合进行有序的遍历，那 TreeMap 是更好的选择。

#### 2.6 HashSet

**(1) 实现原理：**

HashSet 是基于 HashMap 实现的，HashSet 底层使用 HashMap 来保存所有元素，因此 HashSet 的实现比较简单，相关 HashSet 的操作，基本上都是直接调用底层 HashMap 的相关方法来完成，HashSet 不允许重复的值。

#### 2.7 ConcurrentHashMap

**(1) 原理：**

ConcurrentHashMap 类中包含两个静态内部类 HashEntry 和 Segment。HashEntry 用来封装映射表的键 / 值对；Segment 用来充当锁的角色，每个 Segment 对象守护整个散列映射表的若干个桶。每个桶是由若干个 HashEntry 对象链接起来的链表。一个 ConcurrentHashMap 实例中包含由若干个 Segment 对象组成的数组。HashEntry 用来封装散列映射表中的键值对。在 HashEntry 类中，key，hash 和 next 域都被声明为 final 型，value 域被声明为 volatile 型。

在ConcurrentHashMap 中，在散列时如果产生“碰撞”，将采用“分离链接法”来处理“碰撞”：把“碰撞”的 HashEntry 对象链接成一个链表。由于 HashEntry 的 next 域为 final 型，所以新节点只能在链表的表头处插入。 下图是在一个空桶中依次插入 A，B，C 三个 HashEntry 对象后的结构图：

图1. 插入三个节点后桶的结构示意图：

![img](https://uploadfiles.nowcoder.com/images/20180925/308572_1537878284540_B6C31D01D41C9E1714958F9C56D01D8F)

注意：由于只能在表头插入，所以链表中节点的顺序和插入的顺序相反。

Segment 类继承于 ReentrantLock 类，从而使得 Segment 对象能充当锁的角色。每个 Segment 对象用来守护其（成员对象 table 中）包含的若干个桶。

**(2) ConcurrentHashMap锁加在了哪些地方？**

加在每个Segment 上面。

**(3) Concurrenthashmap优势以及1.7和1.8区别**

Concurrenthashmap线程安全的，1.7是在jdk1.7中采用Segment + HashEntry的方式进行实现的，lock加在Segment上面。1.7size计算是先采用不加锁的方式，连续计算元素的个数，最多计算3次：1、如果前后两次计算结果相同，则说明计算出来的元素个数是准确的；2、如果前后两次计算结果都不同，则给每个Segment进行加锁，再计算一次元素的个数；

1.8中放弃了Segment臃肿的设计，取而代之的是采用Node + CAS + Synchronized来保证并发安全进行实现，1.8中使用一个volatile类型的变量baseCount记录元素的个数，当插入新数据或则删除数据时，会通过addCount()方法更新baseCount，通过累加baseCount和CounterCell数组中的数量，即可得到元素的总个数；

**(4) HashMap 和 ConcurrentHashMap的区别：**

hashmap是线程不安全的，put时在多线程情况下，会形成环从而导致死循环。CoucurrentHashMap是线程安全的，采用分段锁机制，减少锁的粒度。

#### 2.8 Array、ArrayList、LinkedList、Vector

**(1) Array 和 ArrayList 有何区别？**

- Array 可以存储基本数据类型和对象，ArrayList 只能存储对象。
- Array 是指定固定大小的，而 ArrayList 大小是自动扩展的。
- Array 内置方法没有 ArrayList 多，比如 addAll、removeAll、iteration 等方法只有 ArrayList 有。

**(2) ArrayList 和 LinkedList 的区别是什么？**

- 数据结构实现：ArrayList 是动态数组的数据结构实现，而 LinkedList 是双向链表的数据结构实现。
- 随机访问效率：ArrayList 比 LinkedList 在随机访问的时候效率要高，因为 LinkedList 是线性的数据存储方式，所以需要移动指针从前往后依次查找。
- 增加和删除效率：在非首尾的增加和删除操作，LinkedList 要比 ArrayList 效率要高，因为 ArrayList 增删操作要影响数组内的其他数据的下标。

综合来说，在需要频繁读取集合中的元素时，更推荐使用 ArrayList，而在插入和删除操作较多时，更推荐使用 LinkedList。

**(3) ArrayList 和 Vector 的区别是什么？**

- 线程安全：Vector 使用了 Synchronized 来实现线程同步，是线程安全的，而 ArrayList 是非线程安全的。
- 性能：ArrayList 在性能方面要优于 Vector。
- 扩容：ArrayList 和 Vector 都会根据实际的需要动态的调整容量，只不过在 Vector 扩容每次会增加 1 倍，而 ArrayList 只会增加 50%。

**(4) 如何实现数组和 List 之间的转换？**

- 数组转 List：使用 Arrays. asList(array) 进行转换。
- List 转数组：使用 List 自带的 toArray() 方法。

#### 2.9 迭代器 Iterator

Iterator 接口提供遍历任何 Collection 的接口。我们可以从一个 Collection 中使用迭代器方法来获取迭代器实例。迭代器取代了 Java 集合框架中的 Enumeration，迭代器允许调用者在迭代过程中移除元素。

**(1) Iterator 怎么使用？有什么特点？**

Iterator 使用代码如下：

```
List<String> list = new ArrayList<>();
Iterator<String> it = list. iterator();
while(it. hasNext()){
  String obj = it. next();
  System. out. println(obj);
}
```

Iterator 的特点是更加安全，因为它可以确保，在当前遍历的集合元素被更改的时候，就会抛出 ConcurrentModificationException 异常。

**(2) Iterator 和 ListIterator 有什么区别？**

- Iterator 可以遍历 Set 和 List 集合，而 ListIterator 只能遍历 List。
- Iterator 只能单向遍历，而 ListIterator 可以双向遍历（向前/后遍历）。
- ListIterator 从 Iterator 接口继承，然后添加了一些额外的功能，比如添加一个元素、替换一个元素、获取前面或后面元素的索引位置。

#### 2.10 补充知识

**(1) 在 Queue 中 poll()和 remove()有什么区别？**

- 相同点：都是返回第一个元素，并在队列中删除返回的对象。
- 不同点：如果没有元素 poll()会返回 null，而 remove()会直接抛出 NoSuchElementException 异常。

代码示例：

```
Queue<String> queue = new LinkedList<String>();
queue. offer("string"); // add
System. out. println(queue. poll());
System. out. println(queue. remove());
System. out. println(queue. size());
```

**(2) 哪些集合类是线程安全的？**

Vector、Hashtable、Stack 都是线程安全的，而像 HashMap 则是非线程安全的，不过在 JDK 1.5 之后随着 Java. util. concurrent 并发包的出现，它们也有了自己对应的线程安全类，比如 HashMap 对应的线程安全类就是 ConcurrentHashMap。

**(3) 怎么确保一个集合不能被修改？**

可以使用 Collections. unmodifiableCollection(Collection c) 方法来创建一个只读集合，这样改变集合的任何操作都会抛出 Java. lang. UnsupportedOperationException 异常。

示例代码如下：

```
List<String> list = new ArrayList<>();
list. add("x");
Collection<String> clist = Collections. unmodifiableCollection(list);
clist. add("y"); // 运行时此行报错
System. out. println(list. size());
```



### 3.多线程

#### 3.1 并行 & 并发

- 并行：多个处理器或多核处理器同时处理多个任务。
- 并发：多个任务在同一个 CPU 核上，按细分的时间片轮流(交替)执行，从逻辑上来看那些任务是同时执行。

并发 = 两个队列和一台咖啡机。

并行 = 两个队列和两台咖啡机。

#### 3.2 线程和进程的区别

 **(1) 定义**：进程是具有一定独立功能的程序关于某个数据集合上的一次运行活动,进程是系统进行资源分配和调度的一个独立单位。线程是进程的一个实体,是CPU调度和分派的基本单位,它是比进程更小的能独立运行的基本单位.线程自己基本上不拥有系统资源,只拥有一点在运行中必不可少的资源(如程序计数器,一组寄存器和栈),但是它可与同属一个进程的其他的线程共享进程所拥有的全部资源。

**(2) 关系**：一个线程可以创建和撤销另一个线程;同一个进程中的多个线程之间可以并发执行。相对进程而言，线程是一个更加接近于执行体的概念，它可以与同进程中的其他线程共享数据，但拥有自己的栈空间，拥有独立的执行序列。

**(3) 区别**：进程和线程的主要差别在于它们是不同的操作系统资源管理方式。进程有独立的地址空间，一个进程崩溃后，在保护模式下不会对其它进程产生影响，而线程只是一个进程中的不同执行路径。线程有自己的堆栈和局部变量，但线程之间没有单独的地址空间，一个线程死掉就等于整个进程死掉，所以多进程的程序要比多线程的程序健壮，但在进程切换时，耗费资源较大，效率要差一些。但对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。

1) 简而言之,**一个程序至少有一个进程,一个进程至少有一个线程.**

2) 线程的划分尺度小于进程，使得多线程程序的并发性高。

3) 另外，进程在执行过程中拥有独立的内存单元，而多个线程共享内存，从而极大地提高了程序的运行效率。

4) 线程在执行过程中与进程还是有区别的。每个独立的线程有一个程序运行的入口、顺序执行序列和程序的出口。但是线程不能够独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。

5) 从逻辑角度来看，多线程的意义在于一个应用程序中，有多个执行部分可以同时执行。但操作系统并没有将多个线程看做多个独立的应用，来实现进程的调度和管理以及资源分配。这就是进程和线程的重要区别。

**(4) 优缺点**：线程和进程在使用上各有优缺点：线程执行开销小，但不利于资源的管理和保护；而进程正相反。同时，线程适合于在SMP机器上运行，而进程则可以跨机器迁移。

#### **3.3 线程**

**(1) 使用线程**

有三种使用线程的方法：

- 实现 Runnable 接口；
- 实现 Callable 接口；
- 继承 Thread 类。

实现 Runnable 和 Callable 接口的类只能当做一个可以在线程中运行的任务，不是真正意义上的线程，因此最后还需要通过 Thread 来调用。可以理解为任务是通过线程驱动从而执行的。

**实现 Runnable 接口**

需要实现接口中的 run() 方法。

```
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        // ...
    }
}
```

使用 Runnable 实例再创建一个 Thread 实例，然后调用 Thread 实例的 start() 方法来启动线程。

```
public static void main(String[] args) {
    MyRunnable instance = new MyRunnable();
    Thread thread = new Thread(instance);
    thread.start();
}
```

**实现 Callable 接口**

与 Runnable 相比，Callable 可以有返回值，返回值通过 FutureTask 进行封装。

```
public class MyCallable implements Callable<Integer> {
    public Integer call() {
        return 123;
    }
}
```

```
public static void main(String[] args) throws ExecutionException, InterruptedException {
    MyCallable mc = new MyCallable();
    FutureTask<Integer> ft = new FutureTask<>(mc);
    Thread thread = new Thread(ft);
    thread.start();
    System.out.println(ft.get());
}
```

**继承 Thread 类**

同样也是需要实现 run() 方法，因为 Thread 类也实现了 Runable 接口。

当调用 start() 方法启动一个线程时，虚拟机会将该线程放入就绪队列中等待被调度，当一个线程被调度时会执行该线程的 run() 方法。

```
public class MyThread extends Thread {
    public void run() {
        // ...
    }
}
```

```
public static void main(String[] args) {
    MyThread mt = new MyThread();
    mt.start();
}
```

**实现接口 VS 继承 Thread**

实现接口会更好一些，因为：

- Java 不支持多重继承，因此继承了 Thread 类就无法继承其它类，但是可以实现多个接口；
- 类可能只要求可执行就行，继承整个 Thread 类开销过大。

**(2) 基础线程机制**

**Executor：**

Executor 管理多个异步任务的执行，而无需程序员显式地管理线程的生命周期。这里的异步是指多个任务的执行互不干扰，不需要进行同步操作。

主要有三种 Executor：

- CachedThreadPool：一个任务创建一个线程；
- FixedThreadPool：所有任务只能使用固定大小的线程；
- SingleThreadExecutor：相当于大小为 1 的 FixedThreadPool。

```
public static void main(String[] args) {
    ExecutorService executorService = Executors.newCachedThreadPool();
    for (int i = 0; i < 5; i++) {
        executorService.execute(new MyRunnable());
    }
    executorService.shutdown();
}
```

**Daemon：**

守护线程是程序运行时在后台提供服务的线程，不属于程序中不可或缺的部分。

当所有非守护线程结束时，程序也就终止，同时会杀死所有守护线程。

main() 属于非守护线程。

在线程启动之前使用 setDaemon() 方法可以将一个线程设置为守护线程。

```
public static void main(String[] args) {
    Thread thread = new Thread(new MyRunnable());
    thread.setDaemon(true);
}
```

守护线程是运行在后台的一种特殊进程。它独立于控制终端并且周期性地执行某种任务或等待处理某些发生的事件。在 Java 中垃圾回收线程就是特殊的守护线程。

**sleep()：**

Thread.sleep(millisec) 方法会休眠当前正在执行的线程，millisec 单位为毫秒。

sleep() 可能会抛出 InterruptedException，因为异常不能跨线程传播回 main() 中，因此必须在本地进行处理。线程中抛出的其它异常也同样需要在本地进行处理。

```
public void run() {
    try {
        Thread.sleep(3000);
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
}
```

**yield()：**

对静态方法 Thread.yield() 的调用声明了当前线程已经完成了生命周期中最重要的部分，可以切换给其它线程来执行。该方法只是对线程调度器的一个建议，而且也只是建议具有相同优先级的其它线程可以运行。

```
public void run() {
    Thread.yield();
}
```

**(3) 中断**

一个线程执行完毕之后会自动结束，如果在运行过程中发生异常也会提前结束。

**InterruptedException**

通过调用一个线程的 interrupt() 来中断该线程，如果该线程处于阻塞、限期等待或者无限期等待状态，那么就会抛出 InterruptedException，从而提前结束该线程。但是不能中断 I/O 阻塞和 synchronized 锁阻塞。

对于以下代码，在 main() 中启动一个线程之后再中断它，由于线程中调用了 Thread.sleep() 方法，因此会抛出一个 InterruptedException，从而提前结束线程，不执行之后的语句。

```
public class InterruptExample {

    private static class MyThread1 extends Thread {
        @Override
        public void run() {
            try {
                Thread.sleep(2000);
                System.out.println("Thread run");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

```
public static void main(String[] args) throws InterruptedException {
    Thread thread1 = new MyThread1();
    thread1.start();
    thread1.interrupt();
    System.out.println("Main run");
}
```

```
Main run
java.lang.InterruptedException: sleep interrupted
    at java.lang.Thread.sleep(Native Method)
    at InterruptExample.lambda$main$0(InterruptExample.java:5)
    at InterruptExample$$Lambda$1/713338599.run(Unknown Source)
    at java.lang.Thread.run(Thread.java:745)
```

**interrupted()**

如果一个线程的 run() 方法执行一个无限循环，并且没有执行 sleep() 等会抛出 InterruptedException 的操作，那么调用线程的 interrupt() 方法就无法使线程提前结束。

但是调用 interrupt() 方法会设置线程的中断标记，此时调用 interrupted() 方法会返回 true。因此可以在循环体中使用 interrupted() 方法来判断线程是否处于中断状态，从而提前结束线程。

```
public class InterruptExample {

    private static class MyThread2 extends Thread {
        @Override
        public void run() {
            while (!interrupted()) {
                // ..
            }
            System.out.println("Thread end");
        }
    }
}
```

```
public static void main(String[] args) throws InterruptedException {
    Thread thread2 = new MyThread2();
    thread2.start();
    thread2.interrupt();
}
```

```
Thread end
```

**Executor 的中断操作**

调用 Executor 的 shutdown() 方法会等待线程都执行完毕之后再关闭，但是如果调用的是 shutdownNow() 方法，则相当于调用每个线程的 interrupt() 方法。

以下使用 Lambda 创建线程，相当于创建了一个匿名内部线程。

```
public static void main(String[] args) {
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> {
        try {
            Thread.sleep(2000);
            System.out.println("Thread run");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    });
    executorService.shutdownNow();
    System.out.println("Main run");
}
```

```
Main run
java.lang.InterruptedException: sleep interrupted
    at java.lang.Thread.sleep(Native Method)
    at ExecutorInterruptExample.lambda$main$0(ExecutorInterruptExample.java:9)
    at ExecutorInterruptExample$$Lambda$1/1160460865.run(Unknown Source)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
    at java.lang.Thread.run(Thread.java:745)
```

如果只想中断 Executor 中的一个线程，可以通过使用 submit() 方法来提交一个线程，它会返回一个 Future<?> 对象，通过调用该对象的 cancel(true) 方法就可以中断线程。

```
Future<?> future = executorService.submit(() -> {
    // ..
});
future.cancel(true);
```

**(4) 互斥同步**

Java 提供了两种锁机制来控制多个线程对共享资源的互斥访问，第一个是 JVM 实现的 synchronized，而另一个是 JDK 实现的 ReentrantLock。

**synchronized**

**a. 同步一个代码块**

```
public void func() {
    synchronized (this) {
        // ...
    }
}
```

它只作用于同一个对象，如果调用两个对象上的同步代码块，就不会进行同步。

对于以下代码，使用 ExecutorService 执行了两个线程，由于调用的是同一个对象的同步代码块，因此这两个线程会进行同步，当一个线程进入同步语句块时，另一个线程就必须等待。

```
public class SynchronizedExample {

    public void func1() {
        synchronized (this) {
            for (int i = 0; i < 10; i++) {
                System.out.print(i + " ");
            }
        }
    }
}
public static void main(String[] args) {
    SynchronizedExample e1 = new SynchronizedExample();
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> e1.func1());
    executorService.execute(() -> e1.func1());
}
```

```
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9
```

对于以下代码，两个线程调用了不同对象的同步代码块，因此这两个线程就不需要同步。从输出结果可以看出，两个线程交叉执行。

```
public static void main(String[] args) {
    SynchronizedExample e1 = new SynchronizedExample();
    SynchronizedExample e2 = new SynchronizedExample();
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> e1.func1());
    executorService.execute(() -> e2.func1());
}
```

```
0 0 1 1 2 2 3 3 4 4 5 5 6 6 7 7 8 8 9 9
```

**b. 同步一个方法**

```
public synchronized void func () {
    // ...
}
```

它和同步代码块一样，作用于同一个对象。

**c. 同步一个类**

```
public void func() {
    synchronized (SynchronizedExample.class) {
        // ...
    }
}
```

作用于整个类，也就是说两个线程调用同一个类的不同对象上的这种同步语句，也会进行同步。

```
public class SynchronizedExample {

    public void func2() {
        synchronized (SynchronizedExample.class) {
            for (int i = 0; i < 10; i++) {
                System.out.print(i + " ");
            }
        }
    }
}
```

```
public static void main(String[] args) {
    SynchronizedExample e1 = new SynchronizedExample();
    SynchronizedExample e2 = new SynchronizedExample();
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> e1.func2());
    executorService.execute(() -> e2.func2());
}
```

```
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9
```

**d. 同步一个静态方法**

```
public synchronized static void fun() {
    // ...
}
```

作用于整个类。

**ReentrantLock**

ReentrantLock 是 java.util.concurrent（J.U.C）包中的锁。

```
public class LockExample {

    private Lock lock = new ReentrantLock();

    public void func() {
        lock.lock();
        try {
            for (int i = 0; i < 10; i++) {
                System.out.print(i + " ");
            }
        } finally {
            lock.unlock(); // 确保释放锁，从而避免发生死锁。
        }
    }
}
public static void main(String[] args) {
    LockExample lockExample = new LockExample();
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> lockExample.func());
    executorService.execute(() -> lockExample.func());
}
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9
```

**比较：**

**1. 锁的实现**

synchronized 是 JVM 实现的，而 ReentrantLock 是 JDK 实现的。

**2. 性能**

新版本 Java 对 synchronized 进行了很多优化，例如自旋锁等，synchronized 与 ReentrantLock 大致相同。

**3. 等待可中断**

当持有锁的线程长期不释放锁的时候，正在等待的线程可以选择放弃等待，改为处理其他事情。

ReentrantLock 可中断，而 synchronized 不行。

**4. 公平锁**

公平锁是指多个线程在等待同一个锁时，必须按照申请锁的时间顺序来依次获得锁。

synchronized 中的锁是非公平的，ReentrantLock 默认情况下也是非公平的，但是也可以是公平的。

**5. 锁绑定多个条件**

一个 ReentrantLock 可以同时绑定多个 Condition 对象。

**使用选择**

除非需要使用 ReentrantLock 的高级功能，否则优先使用 synchronized。这是因为 synchronized 是 JVM 实现的一种锁机制，JVM 原生地支持它，而 ReentrantLock 不是所有的 JDK 版本都支持。并且使用 synchronized 不用担心没有释放锁而导致死锁问题，因为 JVM 会确保锁的释放。

**(5) 线程之间的协作**

当多个线程可以一起工作去解决某个问题时，如果某些部分必须在其它部分之前完成，那么就需要对线程进行协调。

**join()**

在线程中调用另一个线程的 join() 方法，会将当前线程挂起，而不是忙等待，直到目标线程结束。

对于以下代码，虽然 b 线程先启动，但是因为在 b 线程中调用了 a 线程的 join() 方法，b 线程会等待 a 线程结束才继续执行，因此最后能够保证 a 线程的输出先于 b 线程的输出。

**wait() 、notify() 、notifyAll()**

调用 wait() 使得线程等待某个条件满足，线程在等待时会被挂起，当其他线程的运行使得这个条件满足时，其它线程会调用 notify() 或者 notifyAll() 来唤醒挂起的线程。

它们都属于 Object 的一部分，而不属于 Thread。

只能用在同步方法或者同步控制块中使用，否则会在运行时抛出 IllegalMonitorStateException。

使用 wait() 挂起期间，线程会释放锁。这是因为，如果没有释放锁，那么其它线程就无法进入对象的同步方法或者同步控制块中，那么就无法执行 notify() 或者 notifyAll() 来唤醒挂起的线程，造成死锁。

**notify()和 notifyAll()有什么区别？**

notifyAll()会唤醒所有的线程，notify()之后唤醒一个线程。notifyAll() 调用后，会将全部线程由等待池移到锁池，然后参与锁的竞争，竞争成功则继续执行，如果不成功则留在锁池等待锁被释放后再次参与竞争。而 notify()只会唤醒一个线程，具体唤醒哪一个线程由虚拟机控制。

**sleep() 和 wait() 有什么区别？**

- 类的不同：sleep() 来自 Thread，wait() 来自 Object。
- 释放锁：sleep() 不释放锁；wait() 释放锁。
- 用法不同：sleep() 时间到会自动恢复；wait() 可以使用 notify()/notifyAll()直接唤醒。

**await() 、signal() 、signalAll()**

java.util.concurrent 类库中提供了 Condition 类来实现线程之间的协调，可以在 Condition 上调用 await() 方法使线程等待，其它线程调用 signal() 或 signalAll() 方法唤醒等待的线程。

相比于 wait() 这种等待方式，await() 可以指定等待的条件，因此更加灵活。

使用 Lock 来获取一个 Condition 对象。

**线程的 run() 和 start() 有什么区别？**

start() 方法用于启动线程，run() 方法用于执行线程的运行时代码。run() 可以重复调用，而 start() 只能调用一次。

**(6) 线程有哪些状态？**

线程的状态：

- NEW 尚未启动
- RUNNABLE 正在执行中
- BLOCKED 阻塞的（被同步锁或者IO锁阻塞）
- WAITING 永久等待状态
- TIMED_WAITING 等待指定的时间重新被唤醒的状态
- TERMINATED 执行完成

一个线程只能处于一种状态，并且这里的线程状态特指 Java 虚拟机的线程状态，不能反映线程在特定操作系统下的状态。

**新建（NEW）**

创建后尚未启动。

**可运行（RUNABLE）**

正在 Java 虚拟机中运行。但是在操作系统层面，它可能处于运行状态，也可能等待资源调度（例如处理器资源），资源调度完成就进入运行状态。所以该状态的可运行是指可以被运行，具体有没有运行要看底层操作系统的资源调度。

**阻塞（BLOCKED）**

请求获取 monitor lock 从而进入 synchronized 函数或者代码块，但是其它线程已经占用了该 monitor lock，所以出于阻塞状态。要结束该状态进入从而 RUNABLE 需要其他线程释放 monitor lock。

**无限期等待（WAITING）**

等待其它线程显式地唤醒。

阻塞和等待的区别在于，阻塞是被动的，它是在等待获取 monitor lock。而等待是主动的，通过调用 Object.wait() 等方法进入。

| 进入方法                                   | 退出方法                             |
| ------------------------------------------ | ------------------------------------ |
| 没有设置 Timeout 参数的 Object.wait() 方法 | Object.notify() / Object.notifyAll() |
| 没有设置 Timeout 参数的 Thread.join() 方法 | 被调用的线程执行完毕                 |
| LockSupport.park() 方法                    | LockSupport.unpark(Thread)           |

**限期等待（TIMED_WAITING）**

无需等待其它线程显式地唤醒，在一定时间之后会被系统自动唤醒。

| 进入方法                                 | 退出方法                                        |
| ---------------------------------------- | ----------------------------------------------- |
| Thread.sleep() 方法                      | 时间结束                                        |
| 设置了 Timeout 参数的 Object.wait() 方法 | 时间结束 / Object.notify() / Object.notifyAll() |
| 设置了 Timeout 参数的 Thread.join() 方法 | 时间结束 / 被调用的线程执行完毕                 |
| LockSupport.parkNanos() 方法             | LockSupport.unpark(Thread)                      |
| LockSupport.parkUntil() 方法             | LockSupport.unpark(Thread)                      |

调用 Thread.sleep() 方法使线程进入限期等待状态时，常常用“使一个线程睡眠”进行描述。调用 Object.wait() 方法使线程进入限期等待或者无限期等待时，常常用“挂起一个线程”进行描述。睡眠和挂起是用来描述行为，而阻塞和等待用来描述状态。

**死亡（TERMINATED）**

可以是线程结束任务之后自己结束，或者产生了异常而结束。

#### 3.4 线程池

**(1) 简介**

**线程池的概念：**

线程池就是首先创建一些线程，它们的集合称为线程池。使用线程池可以很好地提高性能，线程池在系统启动时即创建大量空闲的线程，程序将一个任务传给线程池，线程池就会启动一条线程来执行这个任务，执行结束以后，该线程并不会死亡，而是再次返回线程池中成为空闲状态，等待执行下一个任务。

**线程池的工作机制**

 a. 在线程池的编程模式下，任务是提交给整个线程池，而不是直接提交给某个线程，线程池在拿到任务后，就在内部寻找是否有空闲的线程，如果有，则将任务交给某个空闲的线程。

b. 一个线程同时只能执行一个任务，但可以同时向一个线程池提交多个任务。

**使用线程池的原因：**

多线程运行时间，系统不断的启动和关闭新线程，成本非常高，会过渡消耗系统资源，以及过渡切换线程的危险，从而可能导致系统资源的崩溃。这时，线程池就是最好的选择了。

**(2) 创建线程池有哪几种方式？**

线程池创建有七种方式，最核心的是最后一种：

- newSingleThreadExecutor()：它的特点在于工作线程数目被限制为 1，操作一个无界的工作队列，所以它保证了所有任务的都是被顺序执行，最多会有一个任务处于活动状态，并且不允许使用者改动线程池实例，因此可以避免其改变线程数目；
- newCachedThreadPool()：它是一种用来处理大量短时间工作任务的线程池，具有几个鲜明特点：它会试图缓存线程并重用，当无缓存线程可用时，就会创建新的工作线程；如果线程闲置的时间超过 60 秒，则被终止并移出缓存；长时间闲置时，这种线程池，不会消耗什么资源。其内部使用 SynchronousQueue 作为工作队列；
- newFixedThreadPool(int nThreads)：重用指定数目（nThreads）的线程，其背后使用的是无界的工作队列，任何时候最多有 nThreads 个工作线程是活动的。这意味着，如果任务数量超过了活动队列数目，将在工作队列中等待空闲线程出现；如果有工作线程退出，将会有新的工作线程被创建，以补足指定的数目 nThreads；
- newSingleThreadScheduledExecutor()：创建单线程池，返回 ScheduledExecutorService，可以进行定时或周期性的工作调度；
- newScheduledThreadPool(int corePoolSize)：和newSingleThreadScheduledExecutor()类似，创建的是个 ScheduledExecutorService，可以进行定时或周期性的工作调度，区别在于单一工作线程还是多个工作线程；
- newWorkStealingPool(int parallelism)：这是一个经常被人忽略的线程池，Java 8 才加入这个创建方法，其内部会构建ForkJoinPool，利用Work-Stealing算法，并行地处理任务，不保证处理顺序；
- ThreadPoolExecutor()：是最原始的线程池创建，上面1-3创建方式都是对ThreadPoolExecutor的封装。

**(3) ThreadPoolExecutor类**

java.uitl.concurrent.ThreadPoolExecutor类是线程池中最核心的一个类，因此如果要透彻地了解Java中的线程池，必须先了解这个类。在ThreadPoolExecutor类中提供了四个构造方法，其中各个构造函数的参数含义为：

- corePoolSize: 线程池核心线程个数
- maximunPoolSize: 线程池最大线程数量
- keepAliveTime: 空闲线程存活时间
- unit: 时间单位
- workQueue: 用于保存等待执行任务的阻塞队列
- threadFactory: 创建线程的工厂
- handler: 线程池对拒绝任务的处理策略

**(3) 实现原理：**

线程池主要是解决两个问题：

一个是当执行大量异步任务时能够提供较好的性能，能复用线程处理任务；

二是能够对线程池进行资源限制和管理。

一个任务提交的线程池，首先会判断核心线程池是否已满，未满就会创建worker线程执行任务，已满判断阻塞队列是否已满，阻塞队列未满加入阻塞队列，已满就判断线程池线程数量是否已经达到最大值，没有就新建线程执行任务，达到最大值的话执行拒绝策略。

拒绝策略有：直接抛出异常、使用调用者所在线程执行、丢弃一个旧任务，执行当前任务、直接丢弃什么都不做。

**(4) 线程池都有哪些状态？**

- RUNNING：这是最正常的状态，接受新的任务，处理等待队列中的任务。
- SHUTDOWN：不接受新的任务提交，但是会继续处理等待队列中的任务。
- STOP：不接受新的任务提交，不再处理等待队列中的任务，中断正在执行任务的线程。
- TIDYING：所有的任务都销毁了，workCount 为 0，线程池的状态在转换为 TIDYING 状态时，会执行钩子方法 terminated()。
- TERMINATED：terminated()方法结束后，线程池的状态就会变成这个。

**(5) 线程池中 submit() 和 execute() 方法有什么区别？**

- execute()：只能执行 Runnable 类型的任务。
- submit()：可以执行 Runnable 和 Callable 类型的任务。

Callable 类型的任务可以获取执行的返回值，而 Runnable 执行无返回值。

**(6) 在 Java 程序中怎么保证多线程的运行安全？**

- 方法一：使用安全类，比如 Java. util. concurrent 下的类。
- 方法二：使用自动锁 synchronized。
- 方法三：使用手动锁 Lock。

#### 3.5 Synchronized 

**(1)  synchronized 底层实现原理？**

synchronized 是由一对 monitorenter/monitorexit 指令实现的，monitor 对象是同步的基本实现单元。在 Java 6 之前，monitor 的实现完全是依靠操作系统内部的互斥锁，因为需要进行用户态到内核态的切换，所以同步操作是一个无差别的重量级操作，性能也很低。但在 Java 6 的时候，Java 虚拟机 对此进行了大刀阔斧地改进，提供了三种不同的 monitor 实现，也就是常说的三种不同的锁：偏向锁（Biased Locking）、轻量级锁和重量级锁，大大改进了其性能。

**(2)  synchronized 和 volatile 的区别是什么？**

- volatile 是变量修饰符；synchronized 是修饰类、方法、代码段。
- volatile 仅能实现变量的修改可见性，不能保证原子性；而 synchronized 则可以保证变量的修改可见性和原子性。
- volatile 不会造成线程的阻塞；synchronized 可能会造成线程的阻塞。

**(3) Synchronized和Lock的区别：**

- synchronized 可以给类、方法、代码块加锁；而 lock 只能给代码块加锁。
- synchronized 不需要手动获取锁和释放锁，使用简单，发生异常会自动释放锁，不会造成死锁；而 lock 需要自己加锁和释放锁，如果使用不当没有 unLock()去释放锁就会造成死锁。
- 通过 Lock 可以知道有没有成功获取锁，而 synchronized 却无法办到。


- synchronized 是Java内置关键字，Lock是Java类
- synchronized 不同线程获取锁只有一个线程能获取成功，其他线程会一直阻塞直到获取锁，Lock有阻塞锁，也有非阻塞锁，阻塞锁还有尝试设置，功能更强
- synchronized 可重入，不可中断，非公平，Lock锁可重入，可判断，有公平锁，非公平锁
- Lock锁适合大量同步代码的同步问题，synchronized锁适合代码少量的同步问题

**(4)  synchronized 和 ReentrantLock 区别是什么？**

synchronized 早期的实现比较低效，对比 ReentrantLock，大多数场景性能都相差较大，但是在 Java 6 中对 synchronized 进行了非常多的改进。

主要区别如下：

- ReentrantLock 使用起来比较灵活，但是必须有释放锁的配合动作；
- ReentrantLock 必须手动获取与释放锁，而 synchronized 不需要手动释放和开启锁；
- ReentrantLock 只适用于代码块锁，而 synchronized 可用于修饰方法、代码块等。

**(5) 多线程中 synchronized 锁升级的原理是什么？**

synchronized 锁升级原理：在锁对象的对象头里面有一个 threadid 字段，在第一次访问的时候 threadid 为空，jvm 让其持有偏向锁，并将 threadid 设置为其线程 id，再次进入的时候会先判断 threadid 是否与其线程 id 一致，如果一致则可以直接使用此对象，如果不一致，则升级偏向锁为轻量级锁，通过自旋循环一定次数来获取锁，执行一定次数之后，如果还没有正常获取到要使用的对象，此时就会把锁从轻量级升级为重量级锁，此过程就构成了 synchronized 锁的升级。

锁的升级的目的：锁升级是为了减低了锁带来的性能消耗。在 Java 6 之后优化 synchronized 的实现方式，使用了偏向锁升级为轻量级锁再升级到重量级锁的方式，从而减低了锁带来的性能消耗。

**(6) Synchronized 可重入怎么实现**：

可重入是指：当一个线程持有一个锁对象之后，再次去获取同一个锁时能够成功获取。

因为synchronized使用的是锁对象，当某个线程第一次持有锁后，会修改锁对象的mark word锁状态为偏向锁，偏向锁锁会在当前线程的栈帧中建立一个锁记录空间，mark word会将指针指向栈中的锁记录。当线程再次获取锁对象的时候，会检查mark word 中的指针是否指向当前线程的栈帧，如果是就直接获取锁，如果不是就需要竞争.

#### 3.6 线程安全

当多个线程访问某个类时，不管运行时环境采用何种调度方式或者这些进程将如何交替执行，并且在主调代码中不需要任何额外的同步或协调，这个类都能表现出正确的行为，那么就称这个类是线程安全的。

**(1) 线程安全主要体现在以下三个方面：**

**原子性：**提供了互斥访问，同一时刻只能有一个线程对它进行操作

**可见性**：一个线程对主内存的修改可以及时的被其他线程观察到

**有序性**：一个线程观察其他线程中的指令执行顺序，由于指令重排序的存在，该观察结果一般杂乱无序

**(2) atomic** 

Atomic包是java.util.concurrent下的另一个专门为线程安全设计的java的包，包含多个原子性操作的类。基本特性就是在多线程情况下，当多个线程想要同时操作这些类的某些实例方法时，具有排他性，也就是当某个线程在执行某个方法时，不会被其他线程打断，其他线程会在外部等待，一直等到该方法执行完毕，才由JVM从等待队列中选择另一个线程进入，这只是一种逻辑上的理解。实际上是借助硬件的相关指令来实现的，不会阻塞线程(只是在硬件级别去阻塞了)。可以对基本数据，数组中的基本数据，对类中的基本数据进行操作。原子变量类相当于一种泛化的volatile变量，能够支持原子的和有条件的读写操作。

我们先看一下传统的锁是怎样保证线程安全的：

class LockDemo {

    private int a;
    
    public synchronized void setA(int b) {
        this.a = b;
    }
    
    public synchronized int getA() {
        return a;
    }
    
    public synchronized void addA() {
        ++a;
    }
    
    public synchronized void reduceA() {
        --a;
    }

}

其实这样的synchronized已经能满足我们日常的线程安全需求了，synchronized是基于代码阻塞的机制，也就是当某个线程占用资源时，其他线程是无法进入的，如果这个线程出现问题的时候，出现大量线程阻塞，CPU就会耗费大量资源来处理阻塞在外的这些线程，但是CPU的任务本不该如此，还极可能出现死锁等问题，对于这样的简单操作反而显得有些笨重，所以应该有更合适更高效的方法来处理这样的问题。所以就有了CAS：

Compare and swap(CAS)

当前的处理器基本都支持CAS，这是一种基于硬件的处理，每一个CAS操作都包含三个运算符：内存地址V ， 一个期望值A和新值B，操作的时候如果这个地址上存放的值等于期望的值A，那么就赋值为B，如果没有，那么就不做任何操作。简而言之，你的值和我的期望值相等，就给你新值，否则不干活了。

CAS是怎么保证线程安全的呢，其实在语言层次我们是没有做任何关于同步的操作的，也没有任何锁。Atomic包下这些类将这些操作都交给了CPU和内存，利用CPU多处理的能力，实现硬件的阻塞，再加上volatile变量的特性即可实现基于原子性的操作的线程安全。所以CAS不是没有阻塞 ，只是阻塞不是语言层面，而是在硬件层面，这样便会更高效。

**(3) atomic 原理：**

atomic 主要利用 CAS (Compare And Wwap) 和 volatile 和 native 方法来保证原子操作，从而避免 synchronized 的高开销，执行效率大为提升。

#### 3.7 ThreadLocal

**(1) ThreadLocal 是什么**

ThreadLocal，很多地方叫做线程本地变量，也有些地方叫做线程本地存储，其实意思差不多。可能很多朋友都知道ThreadLocal为变量在每个线程中都创建了一个副本，那么每个线程可以访问自己内部的副本变量。

ThreadLocal 为每个使用该变量的线程提供独立的变量副本，所以每一个线程都可以独立地改变自己的副本，而不会影响其它线程所对应的副本。

ThreadLocal 的经典使用场景是数据库连接和 session 管理等。

**(2) ThreadLocal的接口方法**

ThreadLocal类接口很简单，只有4个方法，我们先来了解一下：

- void set(Object value)设置当前线程的线程局部变量的值。


- public Object get()该方法返回当前线程所对应的线程局部变量。


- public void remove()将当前线程局部变量的值删除，目的是为了减少内存的占用，该方法是JDK 5.0新增的方法。需要指出的是，当线程结束后，对应该线程的局部变量将自动被垃圾回收，所以显式调用该方法清除线程的局部变量并不是必须的操作，但它可以加快内存回收的速度。


- protected Object initialValue()返回该线程局部变量的初始值，该方法是一个protected的方法，显然是为了让子类覆盖而设计的。这个方法是一个延迟调用方法，在线程第1次调用get()或set(Object)时才执行，并且仅执行1次。ThreadLocal中的缺省实现直接返回一个null。

　　值得一提的是，在JDK5.0中，ThreadLocal已经支持泛型，该类的类名已经变为ThreadLocal<T>。API方法也相应进行了调整，新版本的API方法分别是void set(T value)、T get()以及T initialValue()。

**(3) ThreadLocal是如何为每个线程创建变量的副本的：**

　　首先，在每个线程Thread内部有一个ThreadLocal.ThreadLocalMap类型的成员变量threadLocals，这个threadLocals就是用来存储实际的变量副本的，键值为当前ThreadLocal变量，value为变量副本（即T类型的变量）。

　　初始时，在Thread里面，threadLocals为空，当通过ThreadLocal变量调用get()方法或者set()方法，就会对Thread类中的threadLocals进行初始化，并且以当前ThreadLocal变量为键值，以ThreadLocal要保存的副本变量为value，存到threadLocals。

　　然后在当前线程里面，如果要使用副本变量，就可以通过get方法在threadLocals里面查找。

**(4) Thread同步机制的比较**

　　ThreadLocal和线程同步机制相比有什么优势呢？ThreadLocal和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。

　　在同步机制中，通过对象的锁机制保证同一时间只有一个线程访问变量。这时该变量是多个线程共享的，使用同步机制要求程序慎密地分析什么时候对变量进行读写，什么时候需要锁定某个对象，什么时候释放对象锁等繁杂的问题，程序设计和编写难度相对较大。

　　而ThreadLocal则从另一个角度来解决多线程的并发访问。ThreadLocal会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。ThreadLocal提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进ThreadLocal。

　　由于ThreadLocal中可以持有任何类型的对象，低版本JDK所提供的get()返回的是Object对象，需要强制类型转换。但JDK 5.0通过泛型很好的解决了这个问题，在一定程度地简化ThreadLocal的使用，代码清单 9 2就使用了JDK 5.0新的ThreadLocal<T>版本。

　　概括起来说，对于多线程资源共享的问题，同步机制采用了“以时间换空间”的方式，而ThreadLocal采用了“以空间换时间”的方式。前者仅提供一份变量，让不同的线程排队访问，而后者为每一个线程都提供了一份变量，因此可以同时访问而互不影响。

　　Spring使用ThreadLocal解决线程安全问题我们知道在一般情况下，只有无状态的Bean才可以在多线程环境下共享，在Spring中，绝大部分Bean都可以声明为singleton作用域。就是因为Spring对一些Bean（如RequestContextHolder、TransactionSynchronizationManager、LocaleContextHolder等）中非线程安全状态采用ThreadLocal进行处理，让它们也成为线程安全的状态，因为有状态的Bean就可以在多线程中共享了。

#### 3.8 死锁

**(1) 什么是死锁？**

当线程 A 持有独占锁a，并尝试去获取独占锁 b 的同时，线程 B 持有独占锁 b，并尝试获取独占锁 a 的情况下，就会发生 AB 两个线程由于互相持有对方需要的锁，而发生的阻塞现象，我们称为死锁。

**(2) 怎么防止死锁？**

- 尽量使用 tryLock(long timeout, TimeUnit unit)的方法(ReentrantLock、ReentrantReadWriteLock)，设置超时时间，超时可以退出防止死锁。
- 尽量使用 Java. util. concurrent 并发类代替自己手写锁。
- 尽量降低锁的使用粒度，尽量不要几个功能用同一把锁。
- 尽量减少同步的代码块。

#### **3.9 CountDownLatch 、CyclicBarrier、**Semaphore 

JAVA并发包中有三个类用于同步一批线程的行为，分别是CountDownLatch、Semaphore和CyclicBarrier。

**(1) CountDownLatch**

CountDownLatch是一个计数器闭锁，通过它可以完成类似于阻塞当前线程的功能，即：一个线程或多个线程一直等待，直到其他线程执行的操作完成。CountDownLatch用一个给定的计数器来初始化，该计数器的操作是原子操作，即同时只能有一个线程去操作该计数器。调用该类await方法的线程会一直处于阻塞状态，直到其他线程调用countDown方法使当前计数器的值变为零，每次调用countDown计数器的值减1。当计数器值减至零时，所有因调用await()方法而处于等待状态的线程就会继续往下执行。这种现象只会出现一次，因为计数器不能被重置，如果业务上需要一个可以重置计数次数的版本，可以考虑使用CycliBarrier。

在某些业务场景中，程序执行需要等待某个条件完成后才能继续执行后续的操作；典型的应用如并行计算，当某个处理的运算量很大时，可以将该运算任务拆分成多个子任务，等待所有的子任务都完成之后，父任务再拿到所有子任务的运算结果进行汇总。

**(2) Semaphore**

Semaphore与CountDownLatch相似，不同的地方在于Semaphore的值被获取到后是可以释放的，并不像CountDownLatch那样一直减到底。它也被更多地用来**限制流量**，类似阀门的 功能。如果限定某些资源最多有N个线程可以访问，那么超过N个主不允许再有线程来访问，同时当现有线程结束后，就会释放，然后允许新的线程进来。有点类似于锁的lock与 unlock过程。相对来说他也有两个主要的方法：

用于获取权限的acquire(),其底层实现与CountDownLatch.countdown()类似;
用于释放权限的release()，其底层实现与acquire()是一个互逆的过程。

**(3) CyclicBarrier**

CyclicBarrier也是一个同步辅助类，它允许一组线程相互等待，直到到达某个公共屏障点（common barrier point）。通过它可以完成多个线程之间相互等待，只有当每个线程都准备就绪后，才能各自继续往下执行后面的操作。类似于CountDownLatch，它也是通过计数器来实现的。当某个线程调用await方法时，该线程进入等待状态，且计数器加1，当计数器的值达到设置的初始值时，所有因调用await进入等待状态的线程被唤醒，继续执行后续操作。因为CycliBarrier在释放等待线程后可以重用，所以称为循环barrier。CycliBarrier支持一个可选的Runnable，在计数器的值到达设定值后（但在释放所有线程之前），该Runnable运行一次，注，Runnable在每个屏障点只运行一个。

与CountDownLatch 不同点：

- CountDownLatch 允许一个线程或多个线程等待特定情况，同步完成线程中其他任务。举例：百米赛跑，就绪运动员等待发令枪发动才能起步。
- CyclicBarrier 和CountDownLatch一样都可以协同多个线程，让指定数量的线程等待其它所有的线程都满足某些条件之后才继续执行。举例：排队上摩天轮时，每到齐四个人，就可以上同一个车厢。
- CountDownLatch主要是实现了1个或N个线程需要等待其他线程完成某项操作之后才能继续往下执行操作，描述的是1个线程或N个线程等待其他线程的关系。CyclicBarrier主要是实现了多个线程之间相互等待，直到所有的线程都满足了条件之后各自才能继续执行后续的操作，描述的多个线程内部相互等待的关系。
- CountDownLatch是一次性的，而CyclicBarrier则可以被重置而重复使用。

**(4) 举 例：**

CountDownLatch和CyclicBarrier都是java.util.concurrent包下面的多线程工具类。

从字面上理解，CountDown表示减法计数，Latch表示门闩的意思，计数为0的时候就可以打开门闩了。Cyclic Barrier表示循环的障碍物。两个类都含有这一个意思：对应的线程都完成工作之后再进行下一步动作，也就是大家都准备好之后再进行下一步。然而两者最大的区别是，进行下一步动作的动作实施者是不一样的。这里的“动作实施者”有两种，一种是主线程（即执行main函数），另一种是执行任务的其他线程，后面叫这种线程为“其他线程”，区分于主线程。对于CountDownLatch，当计数为0的时候，下一步的动作实施者是main函数；对于CyclicBarrier，下一步动作实施者是“其他线程”。下面举例说明：

对于CountDownLatch，其他线程为游戏玩家，比如英雄联盟，主线程为控制游戏开始的线程。在所有的玩家都准备好之前，主线程是处于等待状态的，也就是游戏不能开始。当所有的玩家准备好之后，下一步的动作实施者为主线程，即开始游戏。

对于CyclicBarrier，假设有一家公司要全体员工进行团建活动，活动内容为翻越三个障碍物，每一个人翻越障碍物所用的时间是不一样的。但是公司要求所有人在翻越当前障碍物之后再开始翻越下一个障碍物，也就是所有人翻越第一个障碍物之后，才开始翻越第二个，以此类推。类比地，每一个员工都是一个“其他线程”。当所有人都翻越的所有的障碍物之后，程序才结束。而主线程可能早就结束了，这里我们不用管主线程。

总结：CountDownLatch和CyclicBarrier都有让多个线程等待同步然后再开始下一步动作的意思，但是CountDownLatch的下一步的动作实施者是主线程，具有不可重复性；而CyclicBarrier的下一步动作实施者还是“其他线程”本身，具有往复多次实施动作的特点。


### 4. 反射

#### 4.1 什么是反射？

反射是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为 Java 语言的反射机制。

Java反射就是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意方法和属性；并且能改变它的属性。而这也是Java被视为动态（或准动态，为啥要说是准动态，因为一般而言的动态语言定义是程序运行时，允许改变程序结构或变量类型，这种语言称为动态语言。从这个观点看，Perl，Python，Ruby是动态语言，C++，Java，C#不是动态语言。）语言的一个关键性质。

反射就是把java类中的各种成分映射成一个个的Java对象
例如：一个类有：成员变量、方法、构造方法、包等等信息，利用反射技术可以对一个类进行解剖，把个个组成部分映射成一个个对象。
     （其实：一个类中这些成员方法、构造方法、在加入类中都有一个类来描述）
如图是类的正常加载过程：反射的原理在与class对象。
熟悉一下加载的时候：Class对象的由来是将class文件读入内存，并为之创建一个Class对象。

![img](https://img-blog.csdn.net/20170513133210763)

#### 4.2 反射能做什么？

我们知道反射机制允许程序在运行时取得任何一个已知名称的class的内部信息，包括包括其modifiers(修饰符)，fields(属性)，methods(方法)等，并可于运行时改变fields内容或调用methods。那么我们便可以更灵活的编写代码，代码可以在运行时装配，无需在组件之间进行源代码链接，降低代码的耦合度；还有动态代理的实现等等；但是需要注意的是反射使用不当会造成很高的资源消耗！

#### **4.3 反射的具体实现**

下面是一个基本的类 Person

```
 1 package com.ys.reflex;
 2 public class Person {
 3     //私有属性
 4     private String name = "Tom";
 5     //公有属性
 6     public int age = 18;
 7     //构造方法
 8     public Person() {    
 9     }
10     //私有方法
11     private void say(){
12         System.out.println("private say()...");
13     }
14     //公有方法
15     public void work(){
16         System.out.println("public work()...");
17     }
18 }
```

**①、得到 Class 的三种方式**

```
 1 //1、通过对象调用 getClass() 方法来获取,通常应用在：比如你传过来一个 Object
 2 //  类型的对象，而我不知道你具体是什么类，用这种方法
 3 　　Person p1 = new Person();
 4 　　Class c1 = p1.getClass();
 5         
 6 //2、直接通过 类名.class 的方式得到,该方法最为安全可靠，程序性能更高
 7 //  这说明任何一个类都有一个隐含的静态成员变量 class
 8 　　Class c2 = Person.class;
 9         
10 //3、通过 Class 对象的 forName() 静态方法来获取，用的最多，
11 //   但可能抛出 ClassNotFoundException 异常
12 　　Class c3 = Class.forName("com.ys.reflex.Person");
```

需要注意的是：**一个类在 JVM 中只会有一个 Class 实例,**即我们对上面获取的 c1,c2,c3进行 equals 比较，发现都是true

②、**通过 Class 类获取成员变量、成员方法、接口、超类、构造方法等**

查阅 API 可以看到 Class 有很多方法：

　　getName()：获得类的完整名字。
　　getFields()：获得类的public类型的属性。
　　getDeclaredFields()：获得类的所有属性。包括private 声明的和继承类
　　getMethods()：获得类的public类型的方法。
　　getDeclaredMethods()：获得类的所有方法。包括private 声明的和继承类
　　getMethod(String name, Class[] parameterTypes)：获得类的特定方法，name参数指定方法的名字，   parameterTypes 参数指定方法的参数类型。
　　getConstructors()：获得类的public类型的构造方法。
　　getConstructor(Class[] parameterTypes)：获得类的特定构造方法，parameterTypes 参数指定构造方法的参数类型。
　　newInstance()：通过类的不带参数的构造方法创建这个类的一个对象。

我们通过一个例子来综合演示上面的方法：

```
 1 //获得类完整的名字
 2 String className = c2.getName();
 3 System.out.println(className);//输出com.ys.reflex.Person
 4         
 5 //获得类的public类型的属性。
 6 Field[] fields = c2.getFields();
 7 for(Field field : fields){
 8    System.out.println(field.getName());//age
 9 }
10         
11 //获得类的所有属性。包括私有的
12 Field [] allFields = c2.getDeclaredFields();
13 for(Field field : allFields){
14     System.out.println(field.getName());//name    age
15 }
16         
17 //获得类的public类型的方法。这里包括 Object 类的一些方法
18 Method [] methods = c2.getMethods();
19 for(Method method : methods){
20     System.out.println(method.getName());//work waid equls toString hashCode等
21 }
22         
23 //获得类的所有方法。
24 Method [] allMethods = c2.getDeclaredMethods();
25 for(Method method : allMethods){
26     System.out.println(method.getName());//work say
27 }
28         
29 //获得指定的属性
30 Field f1 = c2.getField("age");
31 System.out.println(f1);
32 //获得指定的私有属性
33 Field f2 = c2.getDeclaredField("name");
34 //启用和禁用访问安全检查的开关，值为 true，则表示反射的对象在使用时应该取消 java 语言的访问检查；反之不取消
35 f2.setAccessible(true);
36 System.out.println(f2);
37                 
38 //创建这个类的一个对象
39 Object p2 =  c2.newInstance();
40 //将 p2 对象的  f2 属性赋值为 Bob，f2 属性即为 私有属性 name
41 f2.set(p2,"Bob");
42 //使用反射机制可以打破封装性，导致了java对象的属性不安全。 
43 System.out.println(f2.get(p2)); //Bob
44         
45 //获取构造方法
46 Constructor [] constructors = c2.getConstructors();
47 for(Constructor constructor : constructors){
48     System.out.println(constructor.toString());//public com.ys.reflex.Person()
49 }
```

#### 4.4 反射总结

灵活使用反射能让我们代码更加灵活，这里比如JDBC原生代码注册驱动，hibernate 的实体类，Spring 的 AOP等等都有反射的实现。但是凡事都有两面性，反射也会消耗系统的性能，增加复杂性等，合理使用才是真！

#### 4.5 其他

**(1) java序列化**

Java 序列化是为了保存各种对象在内存中的状态，并且可以把保存的对象状态再读出来。

以下情况需要使用 Java 序列化：

- 想把的内存中的对象状态保存到一个文件中或者数据库中时候；
- 想用套接字在网络上传送对象的时候；
- 想通过RMI（远程方法调用）传输对象的时候。

**(2) 动态代理**

动态代理是运行时动态生成代理类。

动态代理的应用有 spring aop、hibernate 数据查询、测试框架的后端 mock、rpc，Java注解对象获取等。

**(3) 怎么实现动态代理？**

JDK 原生动态代理和 cglib 动态代理。JDK 原生动态代理是基于接口实现的，而 cglib 是基于继承当前类的子类实现的。

jdk代理？？？ cglib代理？？？

### 5. 对象拷贝

？？？

#### 5.1 为什么要使用克隆？

克隆的对象可能包含一些已经修改过的属性，而 new 出来的对象的属性都还是初始化时候的值，所以当需要一个新的对象来保存当前对象的“状态”就靠克隆方法了。

#### 5.2 如何实现对象克隆？

- 实现 Cloneable 接口并重写 Object 类中的 clone() 方法。
- 实现 Serializable 接口，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆。

#### 5.3 深拷贝和浅拷贝区别？

- 浅克隆：当对象被复制时只复制它本身和其中包含的值类型的成员变量，而引用类型的成员对象并没有复制。
- 深克隆：除了对象本身被复制外，对象所包含的所有成员变量也将复制。

### 6. Java Web

#### 6.1  JSP 和 servlet 

JSP 是 servlet 技术的扩展，本质上就是 servlet 的简易方式。servlet 和 JSP 最主要的不同点在于，servlet 的应用逻辑是在 Java 文件中，并且完全从表示层中的 html 里分离开来，而 JSP 的情况是 Java 和 html 可以组合成一个扩展名为 JSP 的文件。JSP 侧重于视图，servlet 主要用于控制逻辑。

#### 6.2  JSP的内置对象和作用

JSP 有 9 大内置对象：

- request：封装客户端的请求，其中包含来自 get 或 post 请求的参数；
- response：封装服务器对客户端的响应；
- pageContext：通过该对象可以获取其他对象；
- session：封装用户会话的对象；
- application：封装服务器运行环境的对象；
- out：输出服务器响应的输出流对象；
- config：Web 应用的配置对象；
- page：JSP 页面本身（相当于 Java 程序中的 this）；
- exception：封装页面抛出异常的对象。

#### 6.3 JSP 的 4 种作用域

- page：代表与一个页面相关的对象和属性。
- request：代表与客户端发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个 Web 组件；需要在页面显示的临时数据可以置于此作用域。
- session：代表与某个用户与服务器建立的一次会话相关的对象和属性。跟某个用户相关的数据应该放在用户自己的 session 中。
- application：代表与整个 Web 应用程序相关的对象和属性，它实质上是跨越整个 Web 应用程序，包括多个页面、请求和会话的一个全局作用域。

#### 6.4 session 和 cookie 的区别

- 存储位置不同：session 存储在服务器端；cookie 存储在浏览器端。
- 安全性不同：cookie 安全性一般，在浏览器存储，可以被伪造和修改。
- 容量和个数限制：cookie 有容量限制，每个站点下的 cookie 也有个数限制。
- 存储的多样性：session 可以存储在 Redis 中、数据库中、应用程序中；而 cookie 只能存储在浏览器中。

#### 6.5 session 的工作原理

session 的工作原理是客户端登录完成之后，服务器会创建对应的 session，session 创建完之后，会把 session 的 id 发送给客户端，客户端再存储到浏览器中。这样客户端每次访问服务器时，都会带着 sessionid，服务器拿到 sessionid 之后，在内存找到与之对应的 session 这样就可以正常工作了。

**如果客户端禁止 cookie 能实现 session 还能用吗？**

可以用，session 只是依赖 cookie 存储 sessionid，如果 cookie 被禁用了，可以使用 url 中添加 sessionid 的方式保证 session 能正常使用。

#### 6.6 如何避免 SQL 注入

- 使用预处理 PreparedStatement。
- 使用正则表达式过滤掉字符中的特殊字符。

#### 6.7  XSS 攻击

XSS 攻击：即跨站脚本攻击，它是 Web 程序中常见的漏洞。原理是攻击者往 Web 页面里插入恶意的脚本代码（css 代码、Javascript 代码等），当用户浏览该页面时，嵌入其中的脚本代码会被执行，从而达到恶意攻击用户的目的，如盗取用户 cookie、破坏页面结构、重定向到其他网站等。

预防 XSS 的核心是必须对输入的数据做过滤处理。

#### 6.8 CSRF 攻击

CSRF：Cross-Site Request Forgery（中文：跨站请求伪造），可以理解为攻击者盗用了你的身份，以你的名义发送恶意请求，比如：以你名义发送邮件、发消息、购买商品，虚拟货币转账等。

防御手段：

- 验证请求来源地址；
- 关键操作添加验证码；
- 在请求地址添加 token 并验证。

### 7. 异常

#### 7.1 throw 和 throws 的区别

- throw：是真实抛出一个异常。
- throws：是声明可能会抛出一个异常。

#### 7.2 final、finally、finalize 

- final：是修饰符，如果修饰类，此类不能被继承；如果修饰方法和变量，则表示此方法和此变量不能在被改变，只能使用。
- finally：是 try{} catch{} finally{} 最后一部分，表示不论发生任何情况都会执行，finally 部分可以省略，但如果 finally 部分存在，则一定会执行 finally 里面的代码。
- finalize： 是 Object 类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法。

#### 7.3 try-catch-finally 

 **(1) try-catch-finally 中哪个部分可以省略？**

try-catch-finally 其中 catch 和 finally 都可以被省略，但是不能同时省略，也就是说有 try 的时候，必须后面跟一个 catch 或者 finally。

**(2) try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？**

finally 一定会执行，即使是 catch 中 return 了，catch 中的 return 会等 finally 中的代码执行完之后，才会执行。

#### 7.4  常见的异常类

- NullPointerException 空指针异常
- ClassNotFoundException 指定类不存在
- NumberFormatException 字符串转换为数字异常
- IndexOutOfBoundsException 数组下标越界异常
- ClassCastException 数据类型转换异常
- FileNotFoundException 文件未找到异常
- NoSuchMethodException 方法不存在异常
- IOException IO 异常
- SocketException Socket 异常

### 8. 网络

#### 8.1 HTTP 和 HTTPS

 **(1) HTTP**：

超文本传输协议 (HTTP-Hypertext transfer protocol)，是互联网上应用最为广泛的一种网络协议，是一种详细规定了浏览器和万维网服务器之间互相通信的规则，通过因特网传送万维网文档的数据传送协议。用于从WWW服务器传输超文本到本地浏览器的传输协议，它可以使浏览器更加高效，使网络传输减少。

**浏览器从接收到一个URL，到最后展示出页面，经历了哪些过程？**

1.DNS解析 2.TCP连接 3.发送HTTP请求 4.服务器处理请求并返回HTTP报文 5.浏览器解析渲染页面

**http 响应码 301 和 302 代表的是什么？有什么区别？**

301：永久重定向。

302：暂时重定向。

它们的区别是，301 对搜索引擎优化（SEO）更加有利；302 有被提示为网络拦截的风险。

**forward 和 redirect 的区别？**

forward 是转发 和 redirect 是重定向：

- 地址栏 url 显示：foward url 不会发生改变，redirect url 会发生改变；
- 数据共享：forward 可以共享 request 里的数据，redirect 不能共享；
- 效率：forward 比 redirect 效率高。

**HTTP的会出现的问题**:

http协议属于明文传输协议，交互过程以及数据传输都没有进行加密，通信双方也没有进行任何认证，通信过程非常容易遭遇劫持、监听、篡改，严重情况下，会造成恶意的流量劫持等问题，甚至造成个人隐私泄露(比如银行卡卡号和密码泄露)等严重的安全问题。

**(2) HTTPS**: 

是以安全为目标的HTTP通道，简单讲是HTTP的安全版，即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL(安全套接层)。现在它被广泛用于万维网上安全敏感的通讯，例如交易支付方面。 HTTPS协议可以分为两种:一是通过建立一个信息安全通道，来保证数据传输的安全;二是通过确认网站的真实性。

HTTPS在HTTP的基础上加入了SSL/TLS协议，依靠SSL证书来验证服务器的身份，并为客户端和服务器端之间建立“SSL加密通道”，确保用户数据在传输过程中处于加密状态，同时防止服务器被钓鱼网站假冒，而HTTP协议无法加密数据，所有通信数据都在网络中明文“裸奔”。通过网络的一些技术手段，就可还原HTTP报文内容。

**(3) HTTPS如何保证数据安全？**

客户端向服务器端发起SSL连接请求;(在此过程中依然存在数据被中间方盗取的可能，下面将会说明如何保证此过程的安全)

1. 服务器把公钥发送给客户端，并且服务器端保存着唯一的私钥
2. 客户端用公钥对双方通信的对称秘钥进行加密，并发送给服务器端
3. 服务器利用自己唯一的私钥对客户端发来的对称秘钥进行解密，在此过程中，中间方无法对其解密(即使是客户端也无法解密，因为只有服务器端拥有唯一的私钥)，这样保证了对称秘钥在收发过程中的安全，此时，服务器端和客户端拥有了一套完全相同的对称秘钥。
4. 进行数据传输，服务器和客户端双方用公有的相同的对称秘钥对数据进行加密解密，可以保证在数据收发过程中的安全，即是第三方获得数据包，也无法对其进行加密，解密和篡改。

​  **(4) 二者的区别**：

1. HTTP 是超文本传输协议，属于明文传输协议，HTTPS 则是具有安全性的基于ssl加密的传输协议
2. HTTP 和 HTTPS 使用的是连接方式不同，而且用的端口也不一样,前者是80,后者是443。
3. HTTP 是简单的无状态的连接。HTTPS 协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议 要比 HTTP 协议安全
4. HTTPS 内容经过对称加密，每个连接生成一个唯一的加密密钥(**对称秘钥**:对称密钥加密又叫专用密钥加密，即发送和接收数据的双方必使用相同的密钥对明文进行加密和解密运算。)
5. HTTPS 内容传输经过完整性校验

#### 8.2 Tcp 和 Udp 

tcp 和 udp 是 OSI 模型中的运输层中的协议。tcp 提供可靠的通信传输，而 udp 则常被用于让广播和细节控制交给应用的通信传输。

**两者的区别大致如下：**

- tcp 面向连接，udp 面向非连接即发送数据前不需要建立链接；
- tcp 提供可靠的服务（数据传输），udp 无法保证；
- tcp 面向字节流，udp 面向报文；
- tcp 数据传输慢，udp 数据传输快；

**tcp 粘包是怎么产生的？**

tcp 粘包可能发生在发送端或者接收端，分别来看两端各种产生粘包的原因：

- 发送端粘包：发送端需要等缓冲区满才发送出去，造成粘包；
- 接收方粘包：接收方不及时接收缓冲区的包，造成多个包接收。

#### 8.3 网络协议模型

**(1) OSI七层协议模型**

OSI的七层协议主要包括：物理层（physical layer）、数据链路层（data link layer）、网络层（network layer）、运输层（transport layer）、会话层（session layer）、表示层（presentation layer）、应用层（application layer）。

**(2) TCP/IP四层协议模型**

TCP/IP是一个四层的体系结构，他包括（从下到上顺序）：网络接口层、网际层（用网际层这个名字是强调这一层是为了解决不同的网络的互联问题）、运输层、应用层。不过从实质上讲，TCP/IP只有最上面的三层，因为最下面的网络接口层并没有具体内容。

**(3) 五层协议体系结构**

五层体系的协议结构是综合了OSI和TCP/IP的优点的一种协议，包括（从下到上）：物理层、数据链路层、网络层、运输层、应用层。（最底下两层可以称为网络接口层）

注：五层协议的体系结构只是为介绍网络原理而设计的，实际应用还是TCP/IP四层体系结构。

OSI由于体系比较复杂，而且设计先于实现，有许多设计过于思想，不太方便计算机软件实现，因而完全实现OSI参考模型的系统不多，应用的范围有限。而TCP/IP协议最早在计算机系统中实现，在Linux、Windows平台中都有稳定的实现，并且提供了简单方便的编程接口（API），可以在其上开发出丰富的应用程序，因此得到了广泛的应用。TCP/IP协议已成为目前互联网事实上的国际标准和工业标准。

**(4) 每一层的协议如下：**

物理层：RJ45、CLOCK、IEEE802.3（中继器、集线器）

数据链路层：PPP、FR、HDLC、VLAN、MAC（网桥、交换机）

网络层：IP、ICMP、ARP、RARP、OSPF、IPX、RIP、IGRP（交换机）

传输层：TCP、UDP、SPX

会话层：NFS、SQL、NETBIOS、RPC

表示层：JPEG、MPEG、ASII

应用层：FTP、DNS、Telnet、SMTP、HTTP、WWW、NFS

**(5) 每一层的作用如下：**

1、物理层

主要定义物理设备标准，例如网线的接口类型、光线的接口类型、各种传输介质的传输速率等。他的主要作用是传入比特流（就是由1、0转化为电流强弱来进行传输，到达目的地后再转化为1、0，也就是我们通常所说的数模转换与模数转换）。这一层的数据叫做比特流。

2、数据链路层

定义了如何让数据格式化进行传输，以及如何让控制对物理介质的访问。这一层通常还提供了错误检测和纠正，以保证数据的可靠传输。

3、网络层

在位于不同地理位置的网络中的两个主机之间提供连接和路径选择。Internet的发展使得从世界各站点访问信息的用户数大大增加，而网络层正是管理这种连接的层。

4、运输层

定义了一些传输数据的协议和端口号（WWW端口80等），如：TCP（传输控制协议TCP，传输效率低，可靠性强，用于传输可靠性要求高，数据量大的数据）和UDP（用户数据报协议UDP，与TCP特性恰恰相反，用于传输可靠性要求不高、数据量小的数据，如QQ聊天数据就是通过这种方式传输的）。主要是将从下层的接收的数据进行分段和传输，到达目的地后再进行传输。常常把这一层数据叫做段。

5、会话层

通过运输层（端口号：传输端口与接收端口）建立数据传输的通路。主要在你的系统之间发起会话或者就受会话请求（设备之间需要相互认识可以是IP地址也可以是MAC地址或者主机名）。

6、表示层

可以确保一个系统的应用层所发送的信息可以被另一个系统的应用层读取。例如，PC程序与另一台程序计算机进行通信，其中一台计算机使用扩展二一十进制交换码（EBCDIC），而另一台则使用美国信息交换标准码（ASCII）来表示相同的字符。如有必要，表示层会通过使用一种通用格式来实现多种数据格式之间的转换。

7、应用层

是最靠近用户的OSI层。这一层为用户的应用程序（如：电子邮件、文件传输和仿真终端）提供网络服务。

#### 8.4 TCP的连接和释放过程

由于TCP连接是全双工的，因此每个方向都必须单独进行关闭。这个原则是当一方完成它的数据发送任务后就能发送一个FIN来终止这个方向的连接。收到一个 FIN只意味着这一方向上没有数据流动，一个TCP连接在收到一个FIN后仍能发送数据。首先进行关闭的一方将执行主动关闭，而另一方执行被动关闭。

**(1) 三次握手的过程**

1）主机A向主机B发送TCP连接请求数据包，其中包含主机A的初始序列号seq(A)=x。（其中报文中同步标志位SYN=1，ACK=0，表示这是一个TCP连接请求数据报文；序号seq=x，表明传输数据时的第一个数据字节的序号是x）；

2）主机B收到请求后，会发回连接确认数据包。（其中确认报文段中，标识位SYN=1，ACK=1，表示这是一个TCP连接响应数据报文，并含主机B的初始序列号seq(B)=y，以及主机B对主机A初始序列号的确认号ack(B)=seq(A)+1=x+1）

3）第三次，主机A收到主机B的确认报文后，还需作出确认，即发送一个序列号seq(A)=x+1；确认号为ack(A)=y+1的报文；

**(2) 四次挥手过程**

假设主机A为客户端，主机B为服务器，其释放TCP连接的过程如下：
1） 关闭客户端到服务器的连接：首先客户端A发送一个FIN，用来关闭客户到服务器的数据传送，然后等待服务器的确认。其中终止标志位FIN=1，序列号seq=u。
2） 服务器收到这个FIN，它发回一个ACK，确认号ack为收到的序号加1。
3） 关闭服务器到客户端的连接：也是发送一个FIN给客户端。

4） 客户段收到FIN后，并发回一个ACK报文确认，并将确认序号seq设置为收到序号加1。 首先进行关闭的一方将执行主动关闭，而另一方执行被动关闭。

![img](https://uploadfiles.nowcoder.com/images/20180927/308572_1538027722640_EBFE71FE6E03CBB1AAE38A25DC56AFB2)

![img](https://uploadfiles.nowcoder.com/images/20180927/308572_1538027843891_F17231DF387BA79A4CCC2E7CDD1C110E)

**(3) 为什么要三次握手？**

如果采用两次握手，那么只要服务器发出确认数据包就会建立连接，但由于客户端此时并未响应服务器端的请求，那此时服务器端就会一直在等待客户端，这样服务器端就白白浪费了一定的资源。若采用三次握手，服务器端没有收到来自客户端的再此确认，则就会知道客户端并没有要求建立请求，就不会浪费服务器的资源。

如果不是三次握手，只有两次

如果客户端发出请求连接时，报文延时了，于是客户端重新发送了一次连接请求消息

后来收到了确认，建立了连接，然后完成了数据传输，关闭了连接

此时，服务器收到了那个迟到的请求消息，此时他应该是个废物了

但是如果只有两次握手，服务器收到请求就响应建立了连接了

但是如果是三次，客户端不会再次确认，服务器也就随后知道了这消息有问题，不会建立连接

**(4) 为什么要四次挥手**？

是一个互相确认的过程，你说不玩了，别人答应了，还要等别人都搞好了再告诉你可以走了，你才能走

客户端：我不想玩了

服务器：好的我知道了

服务器：你可以走了

客户端：好的我走了

就如同在网吧上网，你点击下机之后，再去网管那边结账

结账清楚了之后才彻底结束，而不是你说走就走了，难道你办会员卡了么

这个过程很好理解，客户端发出请求后，并不意味着服务器都已经完成响应

#### 8.5 SSL四次握手的过程

1、 客户端发出请求

首先，客户端（通常是浏览器）先向服务器发出加密通信的请求，这被叫做ClientHello请求。

2、服务器回应

服务器收到客户端请求后，向客户端发出回应，这叫做SeverHello。

3、客户端回应

客户端收到服务器回应以后，首先验证服务器证书。如果证书不是可信机构颁布、或者证书中的域名与实际域名不一致、或者证书已经过期，就会向访问者显示一个警告，由其选择是否还要继续通信。

4、服务器的最后回应

服务器收到客户端的第三个随机数pre-master key之后，计算生成本次会话所用的"会话密钥"。然后，向客户端最后发送下面信息。

（1）编码改变通知，表示随后的信息都将用双方商定的加密方法和密钥发送。

（2）服务器握手结束通知，表示服务器的握手阶段已经结束。这一项同时也是前面发送的所有内容的hash值，用来供客户端校验。

至此，整个握手阶段全部结束。接下来，客户端与服务器进入加密通信，就完全是使用普通的HTTP协议，只不过用"会话密钥"加密内容。

#### 8.6 DNS寻址过程

1、在浏览器中输入[www.qq.com](http://www.qq.com/)域名，操作系统会先检查自己本地的hosts文件是否有这个网址映射关系，如果有，就先调用这个IP地址映射，完成域名解析。

2、如果hosts里没有这个域名的映射，则查找本地DNS解析器缓存，是否有这个网址映射关系，如果有，直接返回，完成域名解析。

3、如果hosts与本地DNS解析器缓存都没有相应的网址映射关系，首先会找TCP/ip参数中设置的首选DNS服务器，在此我们叫它本地DNS服务器，此服务器收到查询时，如果要查询的域名，包含在本地配置区域资源中，则返回解析结果给客户机，完成域名解析，此解析具有权威性。

4、如果要查询的域名，不由本地DNS服务器区域解析，但该服务器已缓存了此网址映射关系，则调用这个IP地址映射，完成域名解析，此解析不具有权威性。

5、如果本地DNS服务器本地区域文件与缓存解析都失效，则根据本地DNS服务器的设置（是否设置转发器）进行查询，如果未用转发模式，本地DNS就把请求发至13台根DNS，根DNS服务器收到请求后会判断这个域名(.com)是谁来授权管理，并会返回一个负责该顶级域名服务器的一个IP。本地DNS服务器收到IP信息后，将会联系负责.com域的这台服务器。这台负责.com域的服务器收到请求后，如果自己无法解析，它就会找一个管理.com域的下一级DNS服务器地址(qq.com)给本地DNS服务器。当本地DNS服务器收到这个地址后，就会找qq.com域服务器，重复上面的动作，进行查询，直至找到[www.qq.com](http://www.qq.com/)主机。

6、如果用的是转发模式，此DNS服务器就会把请求转发至上一级DNS服务器，由上一级服务器进行解析，上一级服务器如果不能解析，或找根DNS或把转请求转至上上级，以此循环。不管是本地DNS服务器用是是转发，还是根提示，最后都是把结果返回给本地DNS服务器，由此DNS服务器再返回给客户机。

从客户端到本地DNS服务器是属于递归查询，而DNS服务器之间就是的交互查询就是迭代查询。

#### 8.7 get 和 post 

- get 请求会被浏览器主动缓存，而 post 不会。
- get 传递参数有大小限制，而 post 没有。
- post 参数传输更安全，get 的参数会明文限制在 url 上，post 不会。

#### 8.8 如何实现跨域

实现跨域有以下几种方案：

- 服务器端运行跨域 设置 CORS 等于 *；
- 在单个接口使用注解 @CrossOrigin 运行跨域；
- 使用 jsonp 跨域；

#### 8.9 JSONP 实现原理

jsonp：JSON with Padding，它是利用script标签的 src 连接可以访问不同源的特性，加载远程返回的“JS 函数”来执行的。

### 9. 设计模式

#### 9.1 说说你熟悉的设计模式

- 单例模式：保证被创建一次，节省系统开销。
- 工厂模式（简单工厂、抽象工厂）：解耦代码。
- 观察者模式：定义了对象之间的一对多的依赖，这样一来，当一个对象改变时，它的所有的依赖者都会收到通知并自动更新。
- 外观模式：提供一个统一的接口，用来访问子系统中的一群接口，外观定义了一个高层的接口，让子系统更容易使用。
- 模版方法模式：定义了一个算法的骨架，而将一些步骤延迟到子类中，模版方法使得子类可以在不改变算法结构的情况下，重新定义算法的步骤。
- 状态模式：允许对象在内部状态改变时改变它的行为，对象看起来好像修改了它的类。

#### 9.2 简单工厂和抽象工厂

- 简单工厂：用来生产同一等级结构中的任意产品，对于增加新的产品，无能为力。
- 工厂方法：用来生产同一等级结构中的固定产品，支持增加任意产品。
- 抽象工厂：用来生产不同产品族的全部产品，对于增加新的产品，无能为力；支持增加产品族。



## 二、java框架

各种框架怎么配置？

### 1. Spring

#### 1.1 简介

**(1) 概念**

 Spring是一个轻量级的IoC和AOP容器框架。是为Java应用程序提供基础性服务的一套框架，目的是用于简化企业应用程序的开发，它使得开发者只需要关心业务需求。常见的配置方式有三种：基于XML的配置、基于注解的配置、基于Java的配置。

主要由以下几个模块组成：

Spring Core：核心类库，提供IOC服务；

Spring Context：提供框架式的Bean访问方式，以及企业级功能（JNDI、定时任务等）；

Spring AOP：AOP服务；

Spring DAO：对JDBC的抽象，简化了数据访问异常的处理；

Spring ORM：对现有的ORM框架的支持；

Spring Web：提供了基本的面向Web的综合特性，例如多方文件上传；

Spring MVC：提供面向Web应用的Model-View-Controller实现。

**(2) 优点**：

- Spring提供了AOP技术，支持将一些通用任务，如安全、事务、日志、权限等进行集中式管理，从而提供更好的复用。
- spring 提供 ioc 技术，容器会帮你管理依赖的对象，从而不需要自己创建和管理依赖对象了，更轻松的实现了程序的解耦。
- spring属于低侵入式设计，代码的污染极低；
- spring 提供了事务支持，使得事务操作变的更加方便。
- spring对于主流的应用框架提供了集成支持，可以很方便的集成其他框架，比如 MyBatis、hibernate 等。

#### **1.2 AOP理解：**

OOP面向对象，允许开发者定义纵向的关系，但并适用于定义横向的关系，导致了大量代码的重复，而不利于各个模块的重用。

AOP，一般称为面向切面，作为面向对象的一种补充，用于将那些与业务无关，但却对多个对象产生影响的公共行为和逻辑，抽取并封装为一个可重用的模块，这个模块被命名为“切面”（Aspect），减少系统中的重复代码，降低了模块间的耦合度，同时提高了系统的可维护性。可用于权限认证、日志、事务处理。

AOP实现的关键在于 代理模式，AOP代理主要分为静态代理和动态代理。静态代理的代表为AspectJ；动态代理则以Spring AOP为代表。

（1）AspectJ是静态代理的增强，所谓静态代理，就是AOP框架会在编译阶段生成AOP代理类，因此也称为编译时增强，他会在编译阶段将AspectJ(切面)织入到Java字节码中，运行的时候就是增强之后的AOP对象。

（2）Spring AOP使用的动态代理，所谓的动态代理就是说AOP框架不会去修改字节码，而是每次运行时在内存中临时为方法生成一个AOP对象，这个AOP对象包含了目标对象的全部方法，并且在特定的切点做了增强处理，并回调原对象的方法。

Spring AOP中的动态代理主要有两种方式，**JDK动态代理**和**CGLIB动态代理**：

​        ①JDK动态代理只提供接口的代理，不支持类的代理。核心InvocationHandler接口和Proxy类，InvocationHandler 通过invoke()方法反射来调用目标类中的代码，动态地将横切逻辑和业务编织在一起；接着，Proxy利用 InvocationHandler动态创建一个符合某一接口的的实例,  生成目标类的代理对象。

        ②如果代理类没有实现 InvocationHandler 接口，那么Spring AOP会选择使用CGLIB来动态代理目标类。CGLIB（Code Generation Library），是一个代码生成的类库，可以在运行时动态的生成指定类的一个子类对象，并覆盖其中特定方法并添加增强代码，从而实现AOP。CGLIB是通过继承的方式做的动态代理，因此如果某个类被标记为final，那么它是无法使用CGLIB做动态代理的。

（3）静态代理与动态代理区别在于生成AOP代理对象的时机不同，相对来说AspectJ的静态代理方式具有更好的性能，但是AspectJ需要特定的编译器进行处理，而Spring AOP则无需特定的编译器处理。

**AOP实现原理：**

通过JDK代理，和CGLIB代理两种方式生成动态代理，构造不同的回调方法来对拦截器链的调用，比如JdkDynamicAopProxy的invoke方法，Cglib2AopProxy中的DynamicAdvisedInterceptor的intercept方法，首先获取配置的拦截器链，通过ReflectiveMethodInvocation的proceed方法实现对拦截器链的调用, 首先需要根据配置来对拦截器进行匹配，匹配成功后，拦截器发挥作用，在对拦截器调用完成后，再对目标对象的方法调用，这样一个普通的Java对象的功能就得到了增强。

 **哪些方法不被AOP增强：**

1. 基于JDK代理，除public外的其他所有方法，包括public static也不能被增强
2. 基于CGLIB代理，由于其通过生成目标类子类的方式来增强，因此不能被子类继承的方法都不能被增强，private、static、final 方法

**六种增强类型：**

1. @Before 前置增强，相当于BeforeAdvice
2. @AfterReturning 后置增强，相当于AfterReturningAdvice
3. @Around 环绕增强，相当于MethodInterceptor
4. @AfterThrowing 抛出增强，相当于ThrowsAdvice
5. @After Final增强，不管抛出异常还是正常退出，都会执行，没有对应的增强接口，一般用于释放资源
6. @DeclareParents 引介增强，相当于IntroductionInterceptor

#### **1.3 IoC理解：**

IoC让相互协作的组件保持松散的耦合，而AOP编程允许你把遍布于应用各层的功能分离出来形成可重用的功能组件。

（1）IOC就是控制反转，是指创建对象的控制权的转移，以前创建对象的主动权和时机是由自己把控的，而现在这种权力转移到Spring容器中，并由容器根据配置文件去创建实例和管理各个实例之间的依赖关系，对象与对象之间松散耦合，也利于功能的复用。DI依赖注入，和控制反转是同一个概念的不同角度的描述，即 应用程序在运行时依赖IoC容器来动态注入对象需要的外部资源。

（2）最直观的表达就是，IOC让对象的创建不用去new了，可以由spring自动生产，使用java的反射机制，根据配置文件在运行时动态的去创建对象以及管理对象，并调用对象的方法的。

（3）Spring的IOC有三种注入方式 ：构造器注入、setter方法注入、根据注解注入。

#### 1.4 Spring Bean

**(1) Spring Bean的生命周期**

 首先说一下Servlet的生命周期：实例化，初始init，接收请求service，销毁destroy；

 Spring上下文中的Bean生命周期也类似，如下：

（1）实例化Bean：

对于BeanFactory容器，当客户向容器请求一个尚未初始化的bean时，或初始化bean的时候需要注入另一个尚未初始化的依赖时，容器就会调用createBean进行实例化。对于ApplicationContext容器，当容器启动结束后，通过获取BeanDefinition对象中的信息，实例化所有的bean。

（2）设置对象属性（依赖注入）：

实例化后的对象被封装在BeanWrapper对象中，紧接着，Spring根据BeanDefinition中的信息 以及 通过BeanWrapper提供的设置属性的接口完成依赖注入。

（3）处理Aware接口：

接着，Spring会检测该对象是否实现了xxxAware接口，并将相关的xxxAware实例注入给Bean：

①如果这个Bean已经实现了BeanNameAware接口，会调用它实现的setBeanName(String beanId)方法，此处传递的就是Spring配置文件中Bean的id值；

②如果这个Bean已经实现了BeanFactoryAware接口，会调用它实现的setBeanFactory()方法，传递的是Spring工厂自身。

③如果这个Bean已经实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文；

（4）BeanPostProcessor：

如果想对Bean进行一些自定义的处理，那么可以让Bean实现了BeanPostProcessor接口，那将会调用postProcessBeforeInitialization(Object obj, String s)方法。

（5）InitializingBean 与 init-method：

如果Bean在Spring配置文件中配置了 init-method 属性，则会自动调用其配置的初始化方法。

（6）如果这个Bean实现了BeanPostProcessor接口，将会调用postProcessAfterInitialization(Object obj, String s)方法；由于这个方法是在Bean初始化结束时调用的，所以可以被应用于内存或缓存技术；

以上几个步骤完成后，Bean就已经被正确创建了，之后就可以使用这个Bean了。

（7）DisposableBean：

当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用其实现的destroy()方法；

（8）destroy-method：

最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法。

**(2) Spring Bean的作用域**

spring 支持 5 种作用域，如下：

- singleton：单例模式，IOC容器中只会存在一个共享的Bean实例，是Spring的默认模式；

- prototype：原型模式，每次从IOC容器获取Bean的时候，都会创建一个新的Bean实例；

  *Web 环境下的作用域*：

- request：每次 http 请求都会创建一个 bean；

- session：同一个 http session 共享一个 bean 实例；

- global-session：用于 portlet 容器，因为每个 portlet 有单独的 session，globalsession 提供一个全局性的 http session。

注意： 使用 prototype 作用域需要慎重的思考，因为频繁创建和销毁 bean 会带来很大的性能开销。

**(3) spring 自动装配 bean 的方式**

- no：默认值，表示没有自动装配，应使用显式 bean 引用进行装配。
- byName：它根据 bean 的名称注入对象依赖项。
- byType：它根据类型注入对象依赖项。
- 构造函数：通过构造函数来注入依赖项，需要设置大量的参数。
- autodetect：容器首先通过构造函数使用 autowire 装配，如果不能，则通过 byType 自动装配。

**(4) Spring 框架中的 Bean 是线程安全的么？**

spring 中的 bean 默认是单例模式，spring 框架并没有对单例 bean 进行多线程的封装处理。

实际上大部分时候 spring bean 无状态的（比如 dao 类），所有某种程度上来说 bean 也是安全的，但如果 bean 有状态的话（比如 view model 对象），那就要开发者自己去保证线程安全了，最简单的就是改变 bean 的作用域，把“singleton”变更为“prototype”，这样请求 bean 相当于 new Bean()了，所以就可以保证线程安全了。

- 有状态就是有数据存储功能。
- 无状态就是不会保存数据。

#### 1.5 Spring中的注解

传统的Spring做法是使用.xml文件来对bean进行注入或者是配置aop、事物，这么做有两个缺点：
1、如果所有的内容都配置在.xml文件中，那么.xml文件将会十分庞大；如果按需求分开.xml文件，那么.xml文件又会非常多。总之这将导致配置文件的可读性与可维护性变得很低。
2、在开发中在.java文件和.xml文件之间不断切换，是一件麻烦的事，同时这种思维上的不连贯也会降低开发的效率。
为了解决这两个问题，Spring引入了注解，通过"@XXX"的方式，让注解与Java Bean紧密结合，既大大减少了配置文件的体积，又增加了Java Bean的可读性与内聚性。

不使用注解：

先看一个不使用注解的Spring示例，在这个示例的基础上，改成注解版本的，这样也能看出使用与不使用注解之间的区别，先定义一个老虎：

```
package com.spring.model;

public class Tiger {
    
    private String tigerName="TigerKing";
    
    public String toString(){
        return "TigerName:"+tigerName;
    }
}
```

再定义一个猴子：

```
package com.spring.model;

public class Monkey {
    
    private String monkeyName = "MonkeyKing";
    
    public String toString(){
        return "MonkeyName:" + monkeyName;
    }

}
```

定义一个动物园：

```
package com.spring.model;

public class Zoo {
    private Tiger tiger;
    private Monkey monkey;
    
    public Tiger getTiger() {
        return tiger;
    }
    public void setTiger(Tiger tiger) {
        this.tiger = tiger;
    }
    public Monkey getMonkey() {
        return monkey;
    }
    public void setMonkey(Monkey monkey) {
        this.monkey = monkey;
    }
    
    public String toString(){
        return tiger + "\n" + monkey;
    }
    
}
```

spring的配置文件这么写：

```
<?xml version="1.0" encoding="UTF-8"?>
<beans
    xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context
    http://www.springframework.org/schema/context/spring-context-3.0.xsd
    ">
    
     <bean id="zoo" class="com.spring.model.Zoo" >
        <property name="tiger" ref="tiger" />
        <property name="monkey" ref="monkey" />
    </bean>
    
    <bean id="tiger" class="com.spring.model.Tiger" />
    <bean id="monkey" class="com.spring.model.Monkey" />

</beans>
```

测试方法：

```
public class TestAnnotation {
    /**
     * 不使用注解
     */
    @Test
    public void test(){
        //读取配置文件
        ApplicationContext ctx=new ClassPathXmlApplicationContext("applicationContext2.xml");
        Zoo zoo=(Zoo) ctx.getBean("zoo");
        System.out.println(zoo.toString());
    }
}
```

**(1)  @Autowired**

@Autowired顾名思义，就是自动装配，其作用是为了消除代码Java代码里面的getter/setter与bean属性中的property。当然，getter看个人需求，如果私有属性需要对外提供的话，应当予以保留。

@Autowired默认按类型匹配的方式，在容器查找匹配的Bean，当**有且仅有一个匹配的Bean**时，Spring将其注入@Autowired标注的变量中。

因此，引入@Autowired注解，先看一下spring配置文件怎么写：

```
13     <context:component-scan base-package="com.spring" />
14     
15     <bean id="zoo" class="com.spring.model.Zoo" />
16     <bean id="tiger" class="com.spring.model.Tiger" />
17     <bean id="monkey" class="com.spring.model.Monkey" />
18 
```

注意第13行，使用必须告诉spring一下我要使用注解了，告诉的方式有很多，<context:component-scan base-package="xxx" />是一种最简单的，spring会自动扫描xxx路径下的注解。

看到第15行，原来zoo里面应当注入两个属性tiger、monkey，现在不需要注入了。再看下，Zoo.java也很方便，把getter/setter都可以去掉：

```
package com.spring.model;

import org.springframework.beans.factory.annotation.Autowired;

public class Zoo {
    
    @Autowired
    private Tiger tiger;
    
    @Autowired
    private Monkey monkey;
    
    public String toString(){
        return tiger + "\n" + monkey;
    }
    
}
```

这里@Autowired注解的意思就是，当Spring发现@Autowired注解时，将自动在代码上下文中找到和其匹配（默认是类型匹配）的Bean，并自动注入到相应的地方去。

有一个细节性的问题是，假如bean里面有两个property，Zoo.java里面又去掉了属性的getter/setter并使用@Autowired注解标注这两个属性那会怎么样？答案是Spring会按照xml优先的原则去Zoo.java中寻找这两个属性的getter/setter，导致的结果就是初始化bean报错。 

因为，@Autowired注解要去寻找的是一个Bean，Tiger和Monkey的Bean定义都给去掉了，自然就不是一个Bean了，Spring容器找不到也很好理解。那么，如果属性找不到我不想让Spring容器抛出异常，而就是显示null，可以吗？可以的，其实异常信息里面也给出了提示了，就是将@Autowired注解的required属性设置为false即可：

```
package com.spring.model;

import org.springframework.beans.factory.annotation.Autowired;

public class Zoo {
    
    @Autowired(required=false)
    private Tiger tiger;
    
    @Autowired(required=false)
    private Monkey monkey;
    
    public String toString(){
        return tiger + "\n" + monkey;
    }
    
}
```

此时，找不到tiger、monkey两个属性，Spring容器不再抛出异常而是认为这两个属性为null。

**(2) @Qualifier（指定注入Bean的名称）**

如果容器中有一个以上匹配的Bean，则可以通过@Qualifier注解限定Bean的名称。看下面的例子：

定义一个Car接口：

两个实现类BMWCar和BenzCar：

再写一个CarFactory，引用car（这里先不用@Qualifier注解）：

配置文件：

测试方法：

运行会报错，因为Car接口有两个实现类，Spring并不知道应当引用哪个实现类。

出现这种情况通常有两种解决办法：
(1)、在配置文件中删除其中一个实现类，Spring会自动去base-package下寻找Car接口的实现类，发现Car接口只有一个实现类，便会直接引用这个实现类。
(2)、实现类就是有多个该怎么办？此时可以使用@Qualifier注解来指定Bean的名称：

```
public class CarFactory {
    
    @Autowired
    @Qualifier("bmwCar")
    private ICar car;
    
    public String toString(){
        return car.getCarName();
    } 
}
```

此处会注入名为"bmwCar"的Bean。

`@Qualifier` 只能和 `@Autowired` 结合使用，是对 `@Autowired` 有益的补充。一般来讲，`@Qualifier` 对方法签名中入参进行注释会降低代码的可读性，而对成员变量注释则相对好一些。

**(3) @Resource**

@Resource注解与@Autowired注解作用非常相似，这个就简单说了，看例子：

```
package com.spring.model;

import javax.annotation.Resource;

public class Zoo1 {
    
    @Resource(name="tiger")
    private Tiger tiger;
    
    @Resource(type=Monkey.class)
    private Monkey monkey;
    
    public String toString(){
        return tiger + "\n" + monkey;
    }
}
```

这是详细一些的用法，说一下@Resource的装配顺序：
(1)、@Resource后面没有任何内容，默认通过name属性去匹配bean，找不到再按type去匹配
(2)、指定了name或者type则根据指定的类型去匹配bean
(3)、指定了name和type则根据指定的name和type去匹配bean，任何一个不匹配都将报错

然后，区分一下@Autowired和@Resource两个注解的区别：
(1)、@Autowired默认按照byType方式进行bean匹配，@Resource默认按照byName方式进行bean匹配
(2)、@Autowired是Spring的注解，@Resource是J2EE的注解，这个看一下导入注解的时候这两个注解的包名就一清二楚了
Spring属于第三方的，J2EE是Java自己的东西，因此，建议使用@Resource注解，以减少代码和Spring之间的耦合。

**(4) @PostConstruct 和 @PreDestro**

Spring 容器中的 Bean 是有生命周期的，Spring 允许在 Bean 在初始化完成后以及 Bean 销毁前执行特定的操作，您既可以通过实现 InitializingBean/DisposableBean 接口来定制初始化之后 / 销毁之前的操作方法，也可以通过 <bean> 元素的 init-method/destroy-method 属性指定初始化之后 / 销毁之前调用的操作方法。

JSR-250 为初始化之后/销毁之前方法的指定定义了两个注释类，分别是 @PostConstruct 和 @PreDestroy，这两个注释只能应用于方法上。标注了 @PostConstruct 注释的方法将在类实例化后调用，而标注了 @PreDestroy 的方法将在类销毁之前调用。

我们知道，不管是通过实现 `InitializingBean`/`DisposableBean` 接口，还是通过 <bean> 元素的`init-method/destroy-method` 属性进行配置，都只能为 Bean 指定一个初始化 / 销毁的方法。但是使用 `@PostConstruct` 和 `@PreDestroy` 注释却可以指定多个初始化 / 销毁方法，那些被标注 `@PostConstruct` 或 `@PreDestroy` 注释的方法都会在初始化 / 销毁时被执行。

**(5) ....**



#### 1.6 Spring 中的事务

Spring事务的本质其实就是数据库对事务的支持，没有数据库的事务支持，spring是无法提供事务功能的。真正的数据库层的事务提交和回滚是通过binlog或者redo log实现的。

**（1）Spring事务的种类：**

spring支持**编程式事务管理**和**声明式事务管理**两种方式：

①编程式事务管理使用TransactionTemplate。

②声明式事务管理建立在AOP之上的。其本质是通过AOP功能，对方法前后进行拦截，将事务处理的功能编织到拦截的方法中，也就是在目标方法开始之前加入一个事务，在执行完目标方法之后根据执行情况提交或者回滚事务。

声明式事务最大的优点就是不需要在业务逻辑代码中掺杂事务管理的代码，只需在配置文件中做相关的事务规则声明或通过@Transactional注解的方式，便可以将事务规则应用到业务逻辑中。

声明式事务管理要优于编程式事务管理，这正是spring倡导的非侵入式的开发方式，使业务代码不受污染，只要加上注解就可以获得完全的事务支持。唯一不足地方是，最细粒度只能作用到方法级别，无法做到像编程式事务那样可以作用到代码块级别。

**（2）spring的事务传播行为：**

spring事务的传播行为说的是，当多个事务同时存在的时候，spring如何处理这些事务的行为。

① PROPAGATION_REQUIRED：如果当前没有事务，就创建一个新事务，如果当前存在事务，就加入该事务，该设置是最常用的设置。

② PROPAGATION_SUPPORTS：支持当前事务，如果当前存在事务，就加入该事务，如果当前不存在事务，就以非事务执行。‘

③ PROPAGATION_MANDATORY：支持当前事务，如果当前存在事务，就加入该事务，如果当前不存在事务，就抛出异常。

④ PROPAGATION_REQUIRES_NEW：创建新事务，无论当前存不存在事务，都创建新事务。

⑤ PROPAGATION_NOT_SUPPORTED：以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。

⑥ PROPAGATION_NEVER：以非事务方式执行，如果当前存在事务，则抛出异常。

⑦ PROPAGATION_NESTED：如果当前存在事务，则在嵌套事务内执行。如果当前没有事务，则按REQUIRED属性执行。

**（3）Spring中的隔离级别：**

① ISOLATION_DEFAULT：这是个 PlatfromTransactionManager 默认的隔离级别，使用数据库默认的事务隔离级别。

② ISOLATION_READ_UNCOMMITTED：读未提交，允许另外一个事务可以看到这个事务未提交的数据。

③ ISOLATION_READ_COMMITTED：读已提交，保证一个事务修改的数据提交后才能被另一事务读取，而且能看到该事务对已有记录的更新。

④ ISOLATION_REPEATABLE_READ：可重复读，保证一个事务修改的数据提交后才能被另一事务读取，但是不能看到该事务对已有记录的更新。

⑤ ISOLATION_SERIALIZABLE：一个事务在执行的过程中完全看不到其他事务对数据库所做的更新。

#### **1.7 Spring中的事件**

Spring 提供了以下5种标准的事件：

（1）上下文更新事件（ContextRefreshedEvent）：在调用ConfigurableApplicationContext 接口中的refresh()方法时被触发。

（2）上下文开始事件（ContextStartedEvent）：当容器调用ConfigurableApplicationContext的Start()方法开始/重新开始容器时触发该事件。

（3）上下文停止事件（ContextStoppedEvent）：当容器调用ConfigurableApplicationContext的Stop()方法停止容器时触发该事件。

（4）上下文关闭事件（ContextClosedEvent）：当ApplicationContext被关闭时触发该事件。容器被关闭时，其管理的所有单例Bean都被销毁。

（5）请求处理事件（RequestHandledEvent）：在Web应用中，当一个http请求（request）结束触发该事件。

如果一个bean实现了ApplicationListener接口，当一个ApplicationEvent 被发布以后，bean会自动被通知。

#### **1.8 Spring中的通知**

**(1) 类型：**

​      1）前置通知（Before advice）：在某连接点（join point）之前执行的通知，但这个通知不能阻止连接点前的执行（除非它抛出一个异常）。

​      2）返回后通知（After returning advice）：在某连接点（join point）正常完成后执行的通知：例如，一个方法没有抛出任何异常，正常返回。 

​     3）抛出异常后通知（After throwing advice）：在方法抛出异常退出时执行的通知。 

​     4）后通知（After (finally) advice）：当某连接点退出的时候执行的通知（不论是正常返回还是异常退出）。 

​     5）环绕通知（Around Advice）：包围一个连接点（join point）的通知，如方法调用。这是最强大的一种通知类型。 环绕通知可以在方法调用前后完成自定义的行为。它也会选择是否继续执行连接点或直接返回它们自己的返回值或抛出异常来结束执行。 环绕通知是最常用的一种通知类型。大部分基于拦截的AOP框架，例如Nanning和JBoss4，都只提供环绕通知。 

**(2) 同一个aspect，不同advice的执行顺序：**

①没有异常情况下的执行顺序：

around before advice
before advice
target method 执行
around after advice
after advice
afterReturning

②有异常情况下的执行顺序：

around before advice
before advice
target method 执行
around after advice
after advice
afterThrowing:异常发生
java.lang.RuntimeException: 异常发生

#### 1.9 Spring 相关问题

**(1) BeanFactory 与ApplicationContext 的区别:**

BeanFactory、ApplicationContext都代表容器，BeanFactory是一个基础接口，实现了容器基础的功能，ApplicationContext是容器的高级形态，增加了许多了特性，顶级父类是BeanFactory。

跟FactoryBean的区别是：

FactoryBean 是一个Bean,用于生产其他的Bean实例

BeanFactory 是一个工厂

**(2) Spring如何解决循环依赖的问题：**

比如A依赖B, B依赖A.

创建A的时候，会把A对应的ObjectFactory放入缓存中，当注入的时候发现需要B, 就会去调用B对象，B对象会先从singletonObjects 查找，没有再从earlySingletonObjects找，还没有就会调用singletonFactory创建对象B,B对象也是先从singletonObjects，earlySingletonObjects，singletonFactories三个缓存中搜索，只要找到就返回，相关方法 AbstractBeanFactory.doGetBean()。

**(3) Spring如何处理线程并发问题？**

在一般情况下，只有无状态的Bean才可以在多线程环境下共享，在Spring中，绝大部分Bean都可以声明为singleton作用域，因为Spring对一些Bean中非线程安全状态采用ThreadLocal进行处理，解决线程安全问题。

ThreadLocal和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。同步机制采用了“时间换空间”的方式，仅提供一份变量，不同的线程在访问前需要获取锁，没获得锁的线程则需要排队。而ThreadLocal采用了“空间换时间”的方式。

ThreadLocal会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。ThreadLocal提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进ThreadLocal。

**(4) Spring基于xml注入bean的几种方式：**

（1）Set方法注入；

（2）构造器注入：①通过index设置参数的位置；②通过type设置参数类型；

（3）静态工厂注入；

（4）实例工厂；

#### **1.10 AOP中的相关名词：**

（1）切面（Aspect）：被抽取的公共模块，可能会横切多个对象。 在Spring AOP中，切面可以使用通用类（基于模式的风格） 或者在普通类中以 @AspectJ 注解来实现。

（2）连接点（Join point）：指方法，在Spring AOP中，一个连接点 总是 代表一个方法的执行。 

（3）通知（Advice）：在切面的某个特定的连接点（Join point）上执行的动作。通知有各种类型，其中包括“around”、“before”和“after”等通知。许多AOP框架，包括Spring，都是以拦截器做通知模型， 并维护一个以连接点为中心的拦截器链。

（4）切入点（Pointcut）：切入点是指 我们要对哪些Join point进行拦截的定义。通过切入点表达式，指定拦截的方法，比如指定拦截add*、search*。

（5）引入（Introduction）：（也被称为内部类型声明（inter-type declaration））。声明额外的方法或者某个类型的字段。Spring允许引入新的接口（以及一个对应的实现）到任何被代理的对象。例如，你可以使用一个引入来使bean实现 IsModified 接口，以便简化缓存机制。

（6）目标对象（Target Object）： 被一个或者多个切面（aspect）所通知（advise）的对象。也有人把它叫做 被通知（adviced） 对象。 既然Spring AOP是通过运行时代理实现的，这个对象永远是一个 被代理（proxied） 对象。

（7）织入（Weaving）：指把增强应用到目标对象来创建新的代理对象的过程。Spring是在运行时完成织入。

切入点（pointcut）和连接点（join point）匹配的概念是AOP的关键，这使得AOP不同于其它仅仅提供拦截功能的旧技术。 切入点使得定位通知（advice）可独立于OO层次。 例如，一个提供声明式事务管理的around通知可以被应用到一组横跨多个对象中的方法上（例如服务层的所有业务操作）。

![img](https://img-blog.csdn.net/20180708154818891?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E3NDUyMzM3MDA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



### 2. SpringMVC 和 Struts2

#### **2.1 Spring MVC **

**(1) Spring MVC 简介：**

Spring MVC，就是spring框架的一个模块,所以它可以和spring框架可以进行无缝整合。它是一个基于Java的实现了MVC设计模式的请求驱动类型的轻量级Web框架，通过把Model，View，Controller分离，将web层进行职责解耦，把复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。

**(2) Spring MVC的流程：**

- spring mvc 先将请求发送给 DispatcherServlet。
- DispatcherServlet 查询一个或多个 HandlerMapping，找到处理请求的 Controller。
- DispatcherServlet 再把请求提交到对应的 Controller。
- Controller 进行业务逻辑处理后，会返回一个ModelAndView。
- Dispathcher 查询一个或多个 ViewResolver 视图解析器，找到 ModelAndView 对象指定的视图对象。
- 视图对象负责渲染返回给客户端。

（1）首先用户发送请求——>DispatcherServlet，前端控制器收到请求后自己不进行处理，而是委托给其他的解析器进行处理，作为统一访问点，进行全局的流程控制；

（2）DispatcherServlet——>HandlerMapping，处理器映射器将会把请求映射为HandlerExecutionChain对象（包含一个Handler处理器对象、多个HandlerInterceptor拦截器）对象；

（3）DispatcherServlet——>HandlerAdapter，处理器适配器将会把处理器包装为适配器，从而支持多种类型的处理器，即适配器设计模式的应用，从而很容易支持很多类型的处理器；

（4）HandlerAdapter——>调用处理器相应功能处理方法，并返回一个ModelAndView对象（包含模型数据、逻辑视图名）；

（5）ModelAndView对象（Model部分是业务对象返回的模型数据，View部分为逻辑视图名）——> ViewResolver， 视图解析器将把逻辑视图名解析为具体的View；

（6）View——>渲染，View会根据传进来的Model模型数据进行渲染，此处的Model实际是一个Map数据结构；

（7）返回控制权给DispatcherServlet，由DispatcherServlet返回响应给用户，到此一个流程结束。

**(3) Spring Mvc的优点:**

（1）可以支持各种视图技术,而不仅仅局限于JSP；

（2）与Spring框架集成（如IoC容器、AOP等）；

（3）清晰的角色分配：前端控制器(dispatcherServlet) , 请求到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。

（4） 支持各种请求资源的映射策略。

**(4) Spring MVC的主要组件：**

（1）前端控制器 DispatcherServlet（不需要程序员开发）

作用：接收请求、响应结果，相当于转发器，有了DispatcherServlet 就减少了其它组件之间的耦合度。

（2）处理器映射器HandlerMapping（不需要程序员开发）

作用：根据请求的URL来查找Handler

（3）处理器适配器HandlerAdapter

注意：在编写Handler的时候要按照HandlerAdapter要求的规则去编写，这样适配器HandlerAdapter才可以正确的去执行Handler。

（4）处理器Handler（需要程序员开发）

（5）视图解析器 ViewResolver（不需要程序员开发）

作用：进行视图的解析，根据视图逻辑名解析成真正的视图（view）

（6）视图View（需要程序员开发jsp）

View是一个接口， 它的实现类支持不同的视图类型（jsp，freemarker，pdf等等）

**(5) SpringMVC怎么样设定重定向和转发的？**

（1）转发：在返回值前面加"forward:"，譬如"forward:user.do?name=method4"

（2）重定向：在返回值前面加"redirect:"，譬如"redirect:http://www.baidu.com"

**(6) SpringMvc怎么和AJAX相互调用的？**

通过Jackson框架就可以把Java里面的对象直接转化成Js可以识别的Json对象。具体步骤如下 ：

（1）加入Jackson.jar

（2）在配置文件中配置json的映射

（3）在接受Ajax方法里面可以直接返回Object,List等,但方法前面要加上@ResponseBody注解。

**(7) 如何解决POST请求中文乱码问题，GET的又如何处理呢？**

（1）解决post请求乱码问题：

在web.xml中配置一个CharacterEncodingFilter过滤器，设置成utf-8；

（2）get请求中文参数出现乱码解决方法有两个：

①修改tomcat配置文件添加编码与工程编码一致，如下：

<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>

 ②另外一种方法对参数进行重新编码：

String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8")

ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码。

**(8) Spring MVC的异常处理 ？**

可以将异常抛给Spring框架，由Spring框架来处理；我们只需要配置简单的异常处理器，在异常处理器中添视图页面即可。

**(9) SpringMvc的控制器是不是单例模式,如果是,有什么问题,怎么解决？**

是单例模式,所以在多线程访问的时候有线程安全问题,不要用同步,会影响性能的,解决方案是在控制器里面不能写字段。

**(10) SpringMVC常用的注解有哪些？**

@RequestMapping：用于处理请求 url 映射的注解，可用于类或方法上。用于类上，则表示类中的所有响应请求的方法都是以该地址作为父路径。

@RequestBody：注解实现接收http请求的json数据，将json转换为java对象。

@ResponseBody：注解实现将conreoller方法返回对象转化为json对象响应给客户。

**(11) SpingMvc中的控制器的注解一般用那个,有没有别的注解可以替代？**

一般用@Controller注解,也可以使用@RestController,@RestController注解相当于@ResponseBody ＋ @Controller,表示是表现层,除此之外，一般不用别的注解代替。

**(12) 如果在拦截请求中，我想拦截get方式提交的方法,怎么配置？**

答：可以在@RequestMapping注解里面加上method=RequestMethod.GET。

**(13) @Autowired 的作用是什么？**

@Autowired 它可以对类成员变量、方法及构造函数进行标注，完成自动装配的工作，通过@Autowired 的使用来消除 set/get 方法。

**(14) 怎样在方法里面得到Request,或者Session？**

答：直接在方法的形参中声明request,SpringMvc就自动把request对象传入。

**(15) 如果想在拦截的方法里面得到从前台传入的参数,怎么得到？**

答：直接在形参里面声明这个参数就可以,但必须名字和传过来的参数一样。

**(16) 如果前台有很多个参数传入,并且这些参数都是一个对象的,那么怎么样快速得到这个对象？**

答：直接在方法中声明这个对象,SpringMvc就自动会把属性赋值到这个对象里面。

**(17) SpringMvc中函数的返回值是什么？**

答：返回值可以有很多类型,有String, ModelAndView。ModelAndView类把视图和数据都合并的一起的，但一般用String比较好。

**(18) SpringMvc用什么对象从后台向前台传递数据的？**

答：通过ModelMap对象,可以在这个对象里面调用put方法,把对象加到里面,前台就可以通过el表达式拿到。

**(19) 怎么样把ModelMap里面的数据放入Session里面？**

答：可以在类上面加上@SessionAttributes注解,里面包含的字符串就是要放入session里面的key。

**(20) SpringMvc里面拦截器是怎么写的：**

有两种写法,一种是实现HandlerInterceptor接口，另外一种是继承适配器类，接着在接口方法当中，实现处理逻辑；然后在SpringMvc的配置文件中配置拦截器即可：

  <!-- 配置SpringMvc的拦截器 -->

<mvc:interceptors>

```
<!-- 配置一个拦截器的Bean就可以了 默认是对所有请求都拦截 -->
 
<bean id="myInterceptor" class="com.zwp.action.MyHandlerInterceptor"></bean>
 
<!-- 只针对部分请求拦截 -->
 
<mvc:interceptor>
 
   <mvc:mapping path="/modelMap.do" />
 
   <bean class="com.zwp.action.MyHandlerInterceptorAdapter" />
 
</mvc:interceptor>
```

</mvc:interceptors>

**注解原理：**

注解本质是一个继承了Annotation的特殊接口，其具体实现类是Java运行时生成的动态代理类。我们通过反射获取注解时，返回的是Java运行时生成的动态代理对象。通过代理对象调用自定义注解的方法，会最终调用AnnotationInvocationHandler的invoke方法。该方法会从memberValues这个Map中索引出对应的值。而memberValues的来源是Java常量池。

#### **2.2 Struts2框架：**

它是一个基于mvc设计思想的前端web层框架,主要作用就是对前端请求进行处理。他的核心是拦截器.但是他的前端控制器是一个过滤器. 它的请求拦截是基于类级别,OGNL也提供了在Struts2里访问各种作用域中的数据的简单方式.大大简化了获取数据的代码.struts2的执行流程是:

A. 页面请求传递到后台, 首先进入Struts2 的核心过滤器 StrutsPrepareAndExecutedFilter .

B.请求进入到struts2 之后, 会根据请求的路径到 struts.xml 文件中根据 package的 namespace 属性 与 action 的 name 属性配置到请求处理的Action 类.

C. 匹配到对应 Action 类的对应方法 , 执行该方法进行业务处理, 处理完毕之后会返回一个结果视图(字符串).

D. 然后根据返回的结果视图 , 到struts.xml 中对应的Action的result结果集配置中 匹配 对应的视图页面(或action).

E. 然后根据 result 的type属性, 转发(或重定向) 对应的页面(或action).

#### **2.3 二者区别**

**(1) 主要区别：**

- 拦截级别：struts2 是类级别的拦截；spring mvc 是方法级别的拦截。

- 数据独立性：spring mvc 的方法之间基本上独立的，独享 request 和 response 数据，请求数据通过参数获取，处理结果通过 ModelMap 交回给框架，方法之间不共享变量；而 struts2 虽然方法之间也是独立的，但其所有 action 变量是共享的，这不会影响程序运行，却给我们编码和读程序时带来了一定的麻烦。

- 拦截机制：struts2 有以自己的 interceptor 机制，spring mvc 用的是独立的 aop 方式，这样导致struts2 的配置文件量比 spring mvc 大。

- 对 ajax 的支持：spring mvc 集成了ajax，所有 ajax 使用很方便，只需要一个注解 @ResponseBody 就可以实现了；而 struts2 一般需要安装插件或者自己写代码才行。

- springmvc的入口是一个servlet即前端控制器（DispatchServlet），而struts2入口是一个filter过虑器（StrutsPrepareAndExecuteFilter）

- Struts采用值栈存储请求和响应的数据，通过OGNL存取数据，springmvc通过参数解析器是将request请求内容解析，并给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过reques域传输到页面。Jsp视图解析器默认使用jstl。

- struts2通过在action类中定义成员变量接收请求参数，struts2只能使用多例模式管理action。

  springmvc通过在controller方法中定义形参接收请求参数，springmvc可以使用单例模式管理controller。

###  3. Mybatis 和 Hibernate

#### 3.1 Mybatis

**(1) 什么是Mybatis？**

（1）Mybatis是一个半ORM（对象关系映射）框架，它内部封装了JDBC，开发时只需要关注SQL语句本身，不需要花费精力去处理加载驱动、创建连接、创建statement等繁杂的过程。程序员直接编写原生态sql，可以严格控制sql执行性能，灵活度高。

（2）MyBatis 可以使用 XML 或注解来配置和映射原生信息，将 POJO映射成数据库中的记录，避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集。

（3）通过xml 文件或注解的方式将要执行的各种 statement 配置起来，并通过java对象和 statement中sql的动态参数进行映射生成最终执行的sql语句，最后由mybatis框架执行sql并将结果映射为java对象并返回。（从执行sql到返回result的过程）。

**(2) Mybaits的优点：**

（1）基于SQL语句编程，相当灵活，不会对应用程序或者数据库的现有设计造成任何影响，SQL写在XML里，解除sql与程序代码的耦合，便于统一管理；提供XML标签，支持编写动态SQL语句，并可重用。

（2）与JDBC相比，减少了50%以上的代码量，消除了JDBC大量冗余的代码，不需要手动开关连接；

（3）很好的与各种数据库兼容（因为MyBatis使用JDBC来连接数据库，所以只要JDBC支持的数据库MyBatis都支持）。

（4）能够与Spring很好的集成；

（5）提供映射标签，支持对象与数据库的ORM字段关系映射；提供对象关系映射标签，支持对象关系组件维护。

**(3) MyBatis框架的缺点：**

（1）SQL语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写SQL语句的功底有一定要求。

（2）SQL语句依赖于数据库，导致数据库移植性差，不能随意更换数据库

**(4) MyBatis框架适用场合：**

（1）MyBatis专注于SQL本身，是一个足够灵活的DAO层解决方案。

（2）对性能的要求很高，或者需求变化较多的项目，如互联网项目，MyBatis将是不错的选择

**(5) Mybatis配置：**

1. 创建普通的JAVA项目
2. 导包：核心包+依赖包+数据库驱动包
3. 建表，建domain
4. 配置核心文件 mybatis-config.xml 和 jdbc.proerties
5. 新建xml来写SQL  
6. 简单功能实现

**(6) MyBatis中的动态SQL**：

对于一些复杂的查询，我们可能会指定多个查询条件，但是这些条件可能存在也可能不存在，需要根据用户指定的条件动态生成SQL语句。如果不使用持久层框架我们可能需要自己拼装SQL语句，还好MyBatis提供了动态SQL的功能来解决这个问题。MyBatis中用于实现动态SQL的元素主要有：

- if
- choose / when / otherwise
- trim
- where
- set
- foreach

**(7) Mybatis动态sql有什么用？执行原理？有哪些动态sql？**

Mybatis动态sql可以在Xml映射文件内，以标签的形式编写动态sql，执行原理是根据表达式的值 完成逻辑判断并动态拼接sql的功能。

Mybatis提供了9种动态sql标签：trim | where | set | foreach | if | choose | when | otherwise | bind。

**(8) MyBatis中命名空间（namespace）的作用**

在大型项目中，可能存在大量的SQL语句，这时候为每个SQL语句起一个唯一的标识（ID）就变得并不容易了。为了解决这个问题，在MyBatis中，可以为每个映射文件起一个唯一的命名空间，这样定义在这个映射文件中的每个SQL语句就成了定义在这个命名空间中的一个ID。只要我们能够保证每个命名空间中这个ID是唯一的，即使在不同映射文件中的语句ID相同，也不会再产生冲突了。

**(9) #{}和${}的区别是什么？**

这里的 #{} 是预编译处理，${} 是字符串替换。

Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用PreparedStatement的set方法来赋值；

Mybatis在处理${} 时，就是把${}替换成变量的值。

使用#{}可以有效的防止SQL注入，提高系统安全性。

**(10) Mybatis的分页方式？如何进行分页的？分页插件的原理？**

分页方式：逻辑分页和物理分页。

逻辑分页： 使用 MyBatis 自带的 RowBounds 进行分页，它是一次性查询很多数据，然后在数据中再进行检索。

物理分页： 自己手写 SQL 分页或使用分页插件 PageHelper，去数据库查询指定条数的分页数据的形式。

- 逻辑分页是一次性查询很多数据，然后再在结果中检索分页的数据。这样做弊端是需要消耗大量的内存、有内存溢出的风险、对数据库压力较大。
- 物理分页是从数据库查询指定条数的数据，弥补了一次性全部查出的所有数据的种种缺点，比如需要大量的内存，对数据库查询压力较大等问题。

Mybatis使用RowBounds对象进行分页，它是针对ResultSet结果集执行的内存分页，而非物理分页。可以在sql内直接书写带有物理分页的参数来完成物理分页功能，也可以使用分页插件来完成物理分页。

分页插件的基本原理是使用Mybatis提供的插件接口，实现自定义插件，在插件的拦截方法内拦截待执行的sql，然后重写sql，根据dialect方言，添加对应的物理分页语句和物理分页参数。

**(11) RowBounds 是一次性查询全部结果吗？为什么？**

RowBounds 表面是在“所有”数据中检索数据，其实并非是一次性查询出所有数据，因为 MyBatis 是对 jdbc 的封装，在 jdbc 驱动中有一个 Fetch Size 的配置，它规定了每次最多从数据库查询多少条数据，假如你要查询更多数据，它会在你执行 next()的时候，去查询更多的数据。就好比你去自动取款机取 10000 元，但取款机每次最多能取 2500 元，所以你要取 4 次才能把钱取完。只是对于 jdbc 来说，当你调用 next()的时候会自动帮你完成查询工作。这样做的好处可以有效的防止内存溢出。

**(12) MyBatis 有哪些执行器（Executor）**

MyBatis 有三种基本的Executor执行器：

- SimpleExecutor：每执行一次 update 或 select 就开启一个 Statement 对象，用完立刻关闭 Statement 对象；
- ReuseExecutor：执行 update 或 select，以 SQL 作为 key 查找 Statement 对象，存在就使用，不存在就创建，用完后不关闭 Statement 对象，而是放置于 Map 内供下一次使用。简言之，就是重复使用 Statement 对象；
- BatchExecutor：执行 update（没有 select，jdbc 批处理不支持 select），将所有 SQL 都添加到批处理中（addBatch()），等待统一执行（executeBatch()），它缓存了多个 Statement 对象，每个 Statement 对象都是 addBatch()完毕后，等待逐一执行 executeBatch()批处理，与 jdbc 批处理相同。

**(13) Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？**

第一种是使用<resultMap>标签，逐一定义数据库列名和对象属性名之间的映射关系。

第二种是使用sql列的别名功能，将列的别名书写为对象属性名。

有了列名与属性名的映射关系后，Mybatis通过反射创建对象，同时使用反射给对象的属性逐一赋值并返回，那些找不到映射关系的属性，是无法完成赋值的。

**(14) 为什么说Mybatis是半自动ORM映射工具？它与全自动的区别在哪里？**

Hibernate属于全自动ORM映射工具，使用Hibernate查询关联对象或者关联集合对象时，可以根据对象关系模型直接获取，所以它是全自动的。而Mybatis在查询关联对象或关联集合对象时，需要手动编写sql来完成，所以，称之为半自动ORM映射工具。

**(15) Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？**

Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。

当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的。

**(16) Mybatis的一级、二级缓存:**

1）一级缓存: 基于 PerpetualCache 的 HashMap 本地缓存，其存储作用域为 Session，当 Session flush 或 close 之后，该 Session 中的所有 Cache 就将清空，默认打开一级缓存。

2）二级缓存与一级缓存其机制相同，默认也是采用 PerpetualCache，HashMap 存储，不同在于其存储作用域为 Mapper(Namespace)，并且可自定义存储源，如 Ehcache。默认不打开二级缓存，要开启二级缓存，使用二级缓存属性类需要实现Serializable序列化接口(可用来保存对象的状态),可在它的映射文件中配置<cache/> ；

3）对于缓存数据更新机制，当某一个作用域(一级缓存 Session/二级缓存Namespaces)的进行了C/U/D 操作后，默认该作用域下所有 select 中的缓存将被 clear 掉并重新更新，如果开启了二级缓存，则只根据配置判断是否刷新。

开启二级缓存数据查询流程：二级缓存 -> 一级缓存 -> 数据库。

缓存更新机制：当某一个作用域(一级缓存 Session/二级缓存 Mapper)进行了C/U/D 操作后，默认该作用域下所有 select 中的缓存将被 clear。

**(17) 什么是MyBatis的接口绑定？有哪些实现方式？**

接口绑定，就是在MyBatis中任意定义接口,然后把接口里面的方法和SQL语句绑定, 我们直接调用接口方法就可以,这样比起原来了SqlSession提供的方法我们可以有更加灵活的选择和设置。

接口绑定有两种实现方式,一种是通过注解绑定，就是在接口的方法上面加上 @Select、@Update等注解，里面包含Sql语句来绑定；另外一种就是通过xml里面写SQL来绑定, 在这种情况下,要指定xml映射文件里面的namespace必须为接口的全路径名。当Sql语句比较简单时候,用注解绑定, 当SQL语句比较复杂时候,用xml绑定,一般用xml绑定的比较多。

**(18) 使用MyBatis的mapper接口调用时有哪些要求？**

①  Mapper接口方法名和mapper.xml中定义的每个sql的id相同；
②  Mapper接口方法的输入参数类型和mapper.xml中定义的每个sql 的parameterType的类型相同；
③  Mapper接口方法的输出参数类型和mapper.xml中定义的每个sql的resultType的类型相同；
④  Mapper.xml文件中的namespace即是mapper接口的类路径。

**(19) Mapper编写有哪几种方式？**

第一种：接口实现类继承SqlSessionDaoSupport：使用此种方法需要编写mapper接口，mapper接口实现类、mapper.xml文件。

第二种：使用org.mybatis.spring.mapper.MapperFactoryBean：

第三种：使用mapper扫描器：

**(20) 简述Mybatis的插件运行原理，以及如何编写一个插件。**

Mybatis仅可以编写针对ParameterHandler、ResultSetHandler、StatementHandler、Executor这4种接口的插件，Mybatis使用JDK的动态代理，为需要拦截的接口生成代理对象以实现接口方法拦截功能，每当执行这4种接口对象的方法时，就会进入拦截方法，具体就是InvocationHandler的invoke()方法，当然，只会拦截那些你指定需要拦截的方法。

编写插件：实现Mybatis的Interceptor接口并复写intercept()方法，然后在给插件编写注解，指定要拦截哪一个接口的哪些方法即可，记住，别忘了在配置文件中配置你编写的插件。

#### 3.2 Hibernate

**(1) 什么是 ORM 框架**

ORM（Object Relation Mapping）对象关系映射，是把数据库中的关系数据映射成为程序中的对象。

使用 ORM 的优点：提高了开发效率降低了开发成本、开发更简单更对象化、可移植更强。

**(2) 为什么要使用 hibernate**

- hibernate 是对 jdbc 的封装，大大简化了数据访问层的繁琐的重复性代码。
- hibernate 是一个优秀的 ORM 实现，很多程度上简化了 DAO 层的编码功能。
- 可以很方便的进行数据库的移植工作。
- 提供了缓存机制，是程序执行更改的高效。

**(3) hibernate 有几种查询方式**

三种：hql、原生 SQL、条件查询 Criteria。

**(4) hibernate 实体类可以被定义为 final 吗**

实体类可以定义为 final 类，但这样的话就不能使用 hibernate 代理模式下的延迟关联提供性能了，所以不建议定义实体类为 final。

**(5) 在 hibernate 中使用 Integer 和 int 做映射有什么区别？**

Integer 类型为对象，它的值允许为 null，而 int 属于基础数据类型，值不能为 null。

**(6) hibernate 是如何工作的**

- 读取并解析配置文件。
- 读取并解析映射文件，创建 SessionFactory。
- 打开 Session。
- 创建事务。
- 进行持久化操作。
- 提交事务。
- 关闭 Session。
- 关闭 SessionFactory。

**(7) Session的load方法和get方法**：

主要有以下三项区别：
① 如果没有找到符合条件的记录，get方法返回null，load方法抛出异常。
② get方法直接返回实体类对象，load方法返回实体类对象的代理。
③ 在Hibernate 3之前，get方法只在一级缓存中进行数据查找，如果没有找到对应的数据则越过二级缓存，直接发出SQL语句完成数据读取；load方法则可以从二级缓存中获取数据；从Hibernate 3开始，get方法不再是对二级缓存只写不读，它也是可以访问二级缓存的。
对于load()方法Hibernate认为该数据在数据库中一定存在可以放心的使用代理来实现延迟加载，如果没有数据就抛出异常，而通过get()方法获取的数据可以不存在。

**(9) hibernate 对象有哪些状态**

- 临时/瞬时状态：直接 new 出来的对象，该对象还没被持久化（没保存在数据库中），不受 Session 管理。
- 持久化状态：当调用 Session 的 save/saveOrupdate/get/load/list 等方法的时候，对象就是持久化状态。
- 游离状态：Session 关闭之后对象就是游离状态。

**(10) 在 hibernate 中 getCurrentSession 和 openSession 的区别是什么**

- getCurrentSession 会绑定当前线程，而 openSession 则不会。
- getCurrentSession 事务是 Spring 控制的，并且不需要手动关闭，而 openSession 需要我们自己手动开启和提交事务。

**(11) hibernate 实体类必须要有无参构造函数吗？为什么？**

hibernate 中每个实体类必须提供一个无参构造函数，因为 hibernate 框架要使用 reflection api，通过调用 ClassnewInstance() 来创建实体类的实例，如果没有无参的构造函数就会抛出异常。

**(12) Hibernate配置：**

1. 创建普通的JAVA项目
2. 导包：核心包+依赖包+数据库驱动包
3. 先创建一个**User**实体
4. 配置**User**实体在数据库表的映射user.hbm.xml
5. 简单配置**hibernate.cfg.xml**配置文件，这个文件名可以随便修改(xxx.cfg.xml)，但是没多大意义，一般不建议修改。
6. 简单功能实现

**(13) jpa 和 hibernate 有什么区别？**

jpa 全称 Java Persistence API，是 Java 持久化接口规范，hibernate 属于 jpa 的具体实现。

**(14) Hibernate常见优化策略：**

①制定合理的缓存策略（二级缓存、查询缓存）。
② 采用合理的Session管理机制。
③ 尽量使用延迟加载特性。
④ 设定合理的批处理参数。
⑤ 如果可以，选用UUID作为主键生成器。
⑥ 如果可以，选用基于版本号的乐观锁替代悲观锁。
⑦ 在开发过程中, 开启hibernate.show_sql选项查看生成的SQL，从而了解底层的状况；开发完成后关闭此选项。
⑧ 考虑数据库本身的优化，合理的索引、恰当的数据分区策略等都会对持久层的性能带来可观的提升，但这些需要专业的DBA（数据库管理员）提供支持。

 **(15) Hibernate的延迟加载机制：**

延迟加载就是并不是在读取的时候就把数据加载进来，而是等到使用时再加载。Hibernate使用了虚拟代理机制实现延迟加载，我们使用Session的load()方法加载数据或者一对多关联映射在使用延迟加载的情况下从一的一方加载多的一方，得到的都是虚拟代理，简单的说返回给用户的并不是实体本身，而是实体对象的代理。代理对象在用户调用getter方法时才会去数据库加载数据。但加载数据就需要数据库连接。而当我们把会话关闭时，数据库连接就同时关闭了。

延迟加载与session关闭的矛盾一般可以这样处理：
① 关闭延迟加载特性。这种方式操作起来比较简单，因为Hibernate的延迟加载特性是可以通过映射文件或者注解进行配置的，但这种解决方案存在明显的缺陷。首先，出现"no session or session was closed"通常说明系统中已经存在主外键关联，如果去掉延迟加载的话，每次查询的开销都会变得很大。
② 在session关闭之前先获取需要查询的数据，可以使用工具方法Hibernate.isInitialized()判断对象是否被加载，如果没有被加载则可以使用Hibernate.initialize()方法加载对象。
③ 使用拦截器或过滤器延长Session的生命周期直到视图获得数据。Spring整合Hibernate提供的OpenSessionInViewFilter和OpenSessionInViewInterceptor就是这种做法。

**(16) Hibernate中SessionFactory和Session是线程安全的吗？这两个线程是否能够共享同一个Session？**

SessionFactory对应Hibernate的一个数据存储的概念，它是线程安全的，可以被多个线程并发访问。SessionFactory一般只会在启动的时候构建。对于应用程序，最好将SessionFactory通过单例模式进行封装以便于访问。Session是一个轻量级非线程安全的对象（线程间不能共享session），它表示与数据库进行交互的一个工作单元。Session是由SessionFactory创建的，在任务完成之后它会被关闭。Session是持久层服务对外提供的主要接口。Session会延迟获取数据库连接（也就是在需要的时候才会获取）。为了避免创建太多的session，可以使用ThreadLocal将session和当前线程绑定在一起，这样可以让同一个线程获得的总是同一个session。Hibernate 3中SessionFactory的getCurrentSession()方法就可以做到。

**(17) Hibernate如何实现分页查询？**

通过Hibernate实现分页查询，开发人员只需要提供HQL语句（调用Session的createQuery()方法）或查询条件（调用Session的createCriteria()方法）、设置查询起始行数（调用Query或Criteria接口的setFirstResult()方法）和最大查询行数（调用Query或Criteria接口的setMaxResults()方法），并调用Query或Criteria接口的list()方法，Hibernate会自动生成分页查询的SQL语句。

**(18) Hibernate的一级缓存、二级缓存以及查询缓存**

Hibernate的Session提供了一级缓存的功能，默认总是有效的，当应用程序保存持久化实体、修改持久化实体时，Session并不会立即把这种改变提交到数据库，而是缓存在当前的Session中，除非显示调用了Session的flush()方法或通过close()方法关闭Session。通过一级缓存，可以减少程序与数据库的交互，从而提高数据库访问性能。
SessionFactory级别的二级缓存是全局性的，所有的Session可以共享这个二级缓存。不过二级缓存默认是关闭的，需要显示开启并指定需要使用哪种二级缓存实现类（可以使用第三方提供的实现）。一旦开启了二级缓存并设置了需要使用二级缓存的实体类，SessionFactory就会缓存访问过的该实体类的每个对象，除非缓存的数据超出了指定的缓存空间。
一级缓存和二级缓存都是对整个实体进行缓存，不会缓存普通属性，如果希望对普通属性进行缓存，可以使用查询缓存。查询缓存是将HQL或SQL语句以及它们的查询结果作为键值对进行缓存，对于同样的查询可以直接从缓存中获取数据。查询缓存默认也是关闭的，需要显示开启。

#### 3.3 二者区别

- 灵活性：MyBatis 更加灵活，自己可以写 SQL 语句，使用起来比较方便。
- 可移植性：MyBatis 有很多自己写的 SQL，因为每个数据库的 SQL 可以不相同，所以可移植性比较差。
- 学习和使用门槛：MyBatis 入门比较简单，使用门槛也更低。
- 二级缓存：hibernate 拥有更好的二级缓存，它的二级缓存可以自行更换为第三方的二级缓存。
- Mybatis和hibernate不同，它不完全是一个ORM框架，因为MyBatis需要程序员自己编写Sql语句。
- Hibernate对象/关系映射能力强，数据库无关性好，对于关系模型要求高的软件，如果用hibernate开发可以节省很多代码，提高效率。
- Mybatis直接编写原生态sql，可以严格控制sql执行性能，灵活度高，非常适合对关系数据模型要求不高的软件开发，因为这类软件需求变化频繁，一但需求变化要求迅速输出成果。但是灵活的前提是mybatis无法做到数据库无关性，如果需要实现支持多种数据库的软件，则需要自定义多套sql映射文件，工作量大。 

### 4. Spring Boot/Spring Cloud

#### **4.1 Spring Boot**

**(1) 什么是 Spring Boot**

spring boot 是为 spring 服务的，是用来简化新 spring 应用的初始搭建以及开发过程的。

Spring Boot是 Spring 的子项目，正如其名字，提供 Spring 的引导( **Boot** )的功能。

通过 Spring Boot ，我们开发者可以快速配置 Spring 项目，引入各种 Spring MVC、Spring Transaction、Spring AOP、MyBatis 等等框架，而无需不断重复编写繁重的 Spring 配置，降低了 Spring 的使用成本。

**(2) 为什么要用 spring boot**

- 配置简单
- 独立运行
- 自动装配
- 无代码生成和 xml 配置
- 提供应用监控
- 易上手
- 提升开发效率

**(3) Spring Boot启动流程**

1. 启动类里面调用SpringApplication.run方法
2. 在run方法中，首先构造SpringApplication对象，然后再调用run方法
3. 在构造SpringApplication对象中，做了如下工作
   - 将sources放入primarySources变量中
   - 判断webApplication是什么类型的
   - 设置ApplicationContextInitializer，ApplicationListener，通过加载META-INF/spring.factories中配置的类
   - 找到main方法找到启动主类
4. run方法中，做的工作
   - StopWatch主要是监控启动过程，统计启动时间，检测应用是否已经启动或者停止。
   - 加载SpringApplicationRunListener(也是通过META-INF/spring.factories),默认加载的是EventPublishingRunListener
   - 调用RunListener.starting()方法。
   - 根据args创建应用参数解析器ApplicationArguments;
   - 准备环境变量：获取环境变量environment，将应用参数放入到环境变量持有对象中，监听器监听环境变量对象的变化(listener.environmentPrepared)
   - 打印Banner信息(SpringBootBanner)
   - 创建SpringBoot的应用上下文(AnnotationConfigEmbeddedWebApplicationContext)
   - prepareContext上下文之前的准备
   - refreshContext刷新上下文
   - afterRefresh(ApplicationRunner,CommandLineRunner接口实现类的启动)
   - 返回上下文对象

**(4) spring boot 核心配置文件是什么？**

spring boot 核心的两个配置文件：

- bootstrap (. yml 或者 . properties)：boostrap 由父 ApplicationContext 加载的，比 applicaton 优先加载，且 boostrap 里面的属性不能被覆盖；
- application (. yml 或者 . properties)：用于 spring boot 项目的自动化配置。

**(5) spring boot 配置文件有哪几种类型？它们有什么区别？**

配置文件有 . properties 格式和 . yml 格式，它们主要的区别是书法风格不同。

. properties 配置如下：

```
spring. RabbitMQ. port=5672
```

. yml 配置如下：

```
spring:
    RabbitMQ:
        port: 5672
```

. yml 格式不支持 @PropertySource 注解导入。

**(6)Spring Boot启动的时候会加载哪些包？**

在web项目中，会在Maven中配置 spring-boot-starter-web 包，该包中包含了spring-core、spring-content、servlet、tomcat、jackson、HikariCP、junit、jdbc、slf4j 等

**(7) 如何重新加载 Spring Boot 上的更改，而无需重新启动服务器？**

一共有三种方式，可以实现效果：

- 【推荐】`spring-boot-devtools` 插件。注意，这个工具需要配置 IDEA 的自动编译。

- Spring Loaded 插件。

  `Spring Boot 2.X 后，官方宣布不再支持 Spring Loaded 插件 的更新，所以基本可以无视它了。`

- JRebel 插件，需要付费。

**(8) 什么是 Spring Boot 自动配置？**

1. Spring Boot 在启动时扫描项目所依赖的 jar 包，寻找包含`spring.factories` 文件的 jar 包。
2. 根据 `spring.factories` 配置加载 AutoConfigure 类。
3. 根据 `@Conditional` 等条件注解的条件，进行自动配置并将 Bean 注入 Spring IoC 中。

**(9) spring boot 有哪些方式可以实现热部署？**

- 使用 devtools 启动热部署，添加 devtools 库，在配置文件中把 spring. devtools. restart. enabled 设置为 true；
- 使用 Intellij Idea 编辑器，勾上自动编译或手动重新编译。

#### 4.2 Spring Cloud

**(1) 什么是 spring cloud**

spring cloud 是一系列框架的有序集合。它利用 spring boot 的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用 spring boot 的开发风格做到一键启动和部署。

![img](https://img-blog.csdnimg.cn/20181103225238934.png)

**(2) Spring Cloud框架特点**

![img](https://img-blog.csdnimg.cn/20181103223930610.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pwY2FuZHpoag==,size_16,color_FFFFFF,t_70)

**(3) spring cloud 断路器的作用是什么**

在分布式架构中，断路器模式的作用也是类似的，当某个服务单元发生故障（类似用电器发生短路）之后，通过断路器的故障监控（类似熔断保险丝），向调用方返回一个错误响应，而不是长时间的等待。这样就不会使得线程因调用故障服务被长时间占用不释放，避免了故障在分布式系统中的蔓延。

**(4) spring cloud 的核心组件有哪些**

- Eureka：服务注册于发现。
- Feign：基于动态代理机制，根据注解和选择的机器，拼接请求 url 地址，发起请求。
- Ribbon：实现负载均衡，从一个服务的多台机器中选择一台。
- Hystrix：提供线程池，不同的服务走不同的线程池，实现了不同服务调用的隔离，避免了服务雪崩的问题。
- Zuul：网关管理，由 Zuul 网关转发请求给对应的服务。

### 5. 中间件

#### 5.1 消息队列

**消息队列**：MQ(Message Queue)，可以简单理解为：把要传输的数据放在队列中。是分布式系统中重要的组件，其通用的使用场景可以简单地描述为：当不需要立即获得结果，但是并发量又需要进行控制的时候，差不多就是需要使用消息队列的时候。

消息队列主要解决了应用耦合、异步处理、流量削锋等问题。

当前使用较多的消息队列有RabbitMQ、RocketMQ、ActiveMQ、Kafka、ZeroMQ、MetaMq等，而部分数据库如Redis、Mysql以及phxsql也可实现消息队列的功能。

常见的MQ性能对比表：

| 特性       | ActiveMQ                                                     | RabbitMQ                                                     | RocketMQ                 | kafka                                                        |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------ | ------------------------------------------------------------ |
| 开发语言   | java                                                         | erlang                                                       | java                     | scala                                                        |
| 单机吞吐量 | 万级                                                         | 万级                                                         | 10万级                   | 10万级                                                       |
| 时效性     | ms级                                                         | us级                                                         | ms级                     | ms级以内                                                     |
| 可用性     | 高(主从架构)                                                 | 高(主从架构)                                                 | 非常高(分布式架构)       | 非常高(分布式架构)                                           |
| 功能特性   | 成熟的产品，在很多公司得到应用；有较多的文档；各种协议支持较好 | 基于erlang开发，所以并发能力很强，性能极其好，延时很低;管理界面较丰富 | MQ功能比较完备，扩展性佳 | 只支持主要的MQ功能，像一些消息查询，消息回溯等功能没有提供，毕竟是为大数据准备的，在大数据领域应用广。 |

#### 5.2 RabbitMQ

**(1) RabbitMQ 的使用场景有哪些？**

- 抢购活动，削峰填谷，防止系统崩塌。
- 延迟信息处理，比如 10 分钟之后给下单未付款的用户发送邮件提醒。
- 解耦系统，对于新增的功能可以单独写模块扩展，比如用户确认评价之后，新增了给用户返积分的功能，这个时候不用在业务代码里添加新增积分的功能，只需要把新增积分的接口订阅确认评价的消息队列即可，后面再添加任何功能只需要订阅对应的消息队列即可。

**(2) RabbitMQ 有哪些重要的角色？**

RabbitMQ 中重要的角色有：生产者、消费者和代理：

- 生产者：消息的创建者，负责创建和推送数据到消息服务器；
- 消费者：消息的接收方，用于处理数据和确认消息；
- 代理：就是 RabbitMQ 本身，用于扮演“快递”的角色，本身不生产消息，只是扮演“快递”的角色。

**(3) RabbitMQ 有哪些重要的组件？**

- ConnectionFactory（连接管理器）：应用程序与Rabbit之间建立连接的管理器，程序代码中使用。
- Channel（信道）：消息推送使用的通道。
- Exchange（交换器）：用于接受、分配消息。
- Queue（队列）：用于存储生产者的消息。
- RoutingKey（路由键）：用于把生成者的数据分配到交换器上。
- BindingKey（绑定键）：用于把交换器的消息绑定到队列上。

**(4) RabbitMQ 中 vhost 的作用是什么？**

vhost：每个 RabbitMQ 都能创建很多 vhost，我们称之为虚拟主机，每个虚拟主机其实都是 mini 版的RabbitMQ，它拥有自己的队列，交换器和绑定，拥有自己的权限机制。

**(5) RabbitMQ 的消息是怎么发送的？**

首先客户端必须连接到 RabbitMQ 服务器才能发布和消费消息，客户端和 rabbit server 之间会创建一个 tcp 连接，一旦 tcp 打开并通过了认证（认证就是你发送给 rabbit 服务器的用户名和密码），你的客户端和 RabbitMQ 就创建了一条 amqp 信道（channel），信道是创建在“真实” tcp 上的虚拟连接，amqp 命令都是通过信道发送出去的，每个信道都会有一个唯一的 id，不论是发布消息，订阅队列都是通过这个信道完成的。

**(6) RabbitMQ 怎么保证消息的稳定性？**

- 提供了事务的功能。
- 通过将 channel 设置为 confirm（确认）模式。

**(7) RabbitMQ 怎么避免消息丢失？**

- 把消息持久化磁盘，保证服务器重启消息不丢失。
- 每个集群中至少有一个物理磁盘，保证消息落入磁盘。

**(8) 要保证消息持久化成功的条件有哪些？**

- 声明队列必须设置持久化 durable 设置为 true.
- 消息推送投递模式必须设置持久化，deliveryMode 设置为 2（持久）。
- 消息已经到达持久化交换器。
- 消息已经到达持久化队列。

以上四个条件都满足才能保证消息持久化成功。

**(9) RabbitMQ 持久化有什么缺点？**

持久化的缺地就是降低了服务器的吞吐量，因为使用的是磁盘而非内存存储，从而降低了吞吐量。可尽量使用 ssd 硬盘来缓解吞吐量的问题。

**(10) RabbitMQ 有几种广播类型？**

- direct（默认方式）：最基础最简单的模式，发送方把消息发送给订阅方，如果有多个订阅者，默认采取轮询的方式进行消息发送。
- headers：与 direct 类似，只是性能很差，此类型几乎用不到。
- fanout：分发模式，把消费分发给所有订阅者。
- topic：匹配订阅模式，使用正则匹配到消息队列，能匹配到的都能接收到。

**(11) RabbitMQ 怎么实现延迟消息队列？**

延迟队列的实现有两种方式：

- 通过消息过期后进入死信交换器，再由交换器转发到延迟消费队列，实现延迟功能；
- 使用 RabbitMQ-delayed-message-exchange 插件实现延迟功能。

**(12) RabbitMQ 集群有什么用？**

集群主要有以下两个用途：

- 高可用：某个服务器出现问题，整个 RabbitMQ 还可以继续使用；
- 高容量：集群可以承载更多的消息量。

**(13) RabbitMQ 节点的类型有哪些？**

- 磁盘节点：消息会存储到磁盘。
- 内存节点：消息都存储在内存中，重启服务器消息丢失，性能高于磁盘类型。

**(14) RabbitMQ 集群搭建需要注意哪些问题？**

- 各节点之间使用“--link”连接，此属性不能忽略。
- 各节点使用的 erlang cookie 值必须相同，此值相当于“秘钥”的功能，用于各节点的认证。
- 整个集群中必须包含一个磁盘节点。

**(15) RabbitMQ 每个节点是其他节点的完整拷贝吗？为什么？**

不是，原因有以下两个：

- 存储空间的考虑：如果每个节点都拥有所有队列的完全拷贝，这样新增节点不但没有新增存储空间，反而增加了更多的冗余数据；
- 性能的考虑：如果每条消息都需要完整拷贝到每一个集群节点，那新增节点并没有提升处理消息的能力，最多是保持和单节点相同的性能甚至是更糟。

**(16) RabbitMQ 集群中唯一一个磁盘节点崩溃了会发生什么情况？**

如果唯一磁盘的磁盘节点崩溃了，不能进行以下操作：

- 不能创建队列
- 不能创建交换器
- 不能创建绑定
- 不能添加用户
- 不能更改权限
- 不能添加和删除集群节点

唯一磁盘节点崩溃了，集群是可以保持运行的，但你不能更改任何东西。

**(17) RabbitMQ 对集群节点停止顺序有要求吗？**

RabbitMQ 对集群的停止的顺序是有要求的，应该先关闭内存节点，最后再关闭磁盘节点。如果顺序恰好相反的话，可能会造成消息的丢失。

#### 5.3 Kafka

**(1) kafka 可以脱离 zookeeper 单独使用吗？为什么？**

kafka 不能脱离 zookeeper 单独使用，因为 kafka 使用 zookeeper 管理和协调 kafka 的节点服务器。

**(2) kafka 有几种数据保留的策略？**

kafka 有两种数据保存策略：按照过期时间保留和按照存储的消息大小保留。

**(3) kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 kafka 将如何处理？**

这个时候 kafka 会执行数据清除工作，时间和大小不论那个满足条件，都会清空数据。

**(4) 什么情况会导致 kafka 运行变慢？**

- cpu 性能瓶颈
- 磁盘读写瓶颈
- 网络瓶颈

**(5) 使用 kafka 集群需要注意什么？**

- 集群的数量不是越多越好，最好不要超过 7 个，因为节点越多，消息复制需要的时间就越长，整个群组的吞吐量就越低。
- 集群数量最好是单数，因为超过一半故障集群就不能用了，设置为单数容错率更高。

#### 5.4 Zookeeper

**(1) zookeeper 是什么？**

zookeeper 是一个分布式的，开放源码的分布式应用程序协调服务，是 google chubby 的开源实现，是 hadoop 和 hbase 的重要组件。它是一个为分布式应用提供一致性服务的软件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。

**(2) zookeeper 都有哪些功能？**

- 集群管理：监控节点存活状态、运行请求等。
- 主节点选举：主节点挂掉了之后可以从备用的节点开始新一轮选主，主节点选举说的就是这个选举的过程，使用 zookeeper 可以协助完成这个过程。
- 分布式锁：zookeeper 提供两种锁：独占锁、共享锁。独占锁即一次只能有一个线程使用资源，共享锁是读锁共享，读写互斥，即可以有多线线程同时读同一个资源，如果要使用写锁也只能有一个线程使用。zookeeper可以对分布式锁进行控制。
- 命名服务：在分布式系统中，通过使用命名服务，客户端应用能够根据指定名字来获取资源或服务的地址，提供者等信息。

**(3) zookeeper 有几种部署模式？**

zookeeper 有三种部署模式：

- 单机部署：一台集群上运行；
- 集群部署：多台集群运行；
- 伪集群部署：一台集群启动多个 zookeeper 实例运行。

**(4) zookeeper 怎么保证主从节点的状态同步？**

zookeeper 的核心是原子广播，这个机制保证了各个 server 之间的同步。实现这个机制的协议叫做 zab 协议。 zab 协议有两种模式，分别是恢复模式（选主）和广播模式（同步）。当服务启动或者在领导者崩溃后，zab 就进入了恢复模式，当领导者被选举出来，且大多数 server 完成了和 leader 的状态同步以后，恢复模式就结束了。状态同步保证了 leader 和 server 具有相同的系统状态。

**(5) 集群中为什么要有主节点？**

在分布式环境中，有些业务逻辑只需要集群中的某一台机器进行执行，其他的机器可以共享这个结果，这样可以大大减少重复计算，提高性能，所以就需要主节点。

**(6) 集群中有 3 台服务器，其中一个节点宕机，这个时候 zookeeper 还可以使用吗？**

可以继续使用，单数服务器只要没超过一半的服务器宕机就可以继续使用。

**(7) 说一下 zookeeper 的通知机制？**

客户端端会对某个 znode 建立一个 watcher 事件，当该 znode 发生变化时，这些客户端会收到 zookeeper 的通知，然后客户端可以根据 znode 变化来做出业务上的改变。

## 三、 JVM 

#### 1. 主要组成部分和作用

- 类加载器（ClassLoader）
- 运行时数据区（Runtime Data Area）
- 执行引擎（Execution Engine）
- 本地库接口（Native Interface）

组件的作用： 首先通过类加载器（ClassLoader）会把 Java 代码转换成字节码，运行时数据区（Runtime Data Area）再把字节码加载到内存中，而字节码文件只是 JVM 的一套指令集规范，并不能直接交给底层操作系统去执行，因此需要特定的命令解析器执行引擎（Execution Engine），将字节码翻译成底层系统指令，再交由 CPU 去执行，而这个过程中需要调用其他语言的本地库接口（Native Interface）来实现整个程序的功能。

#### 2. JVM 运行时数据区

不同虚拟机的运行时数据区可能略微有所不同，但都会遵从 Java 虚拟机规范， Java 虚拟机规范规定的区域分为以下 5 个部分：

- 程序计数器（Program Counter Register）：当前线程所执行的字节码的行号指示器，字节码解析器的工作是通过改变这个计数器的值，来选取下一条需要执行的字节码指令，分支、循环、跳转、异常处理、线程恢复等基础功能，都需要依赖这个计数器来完成；
- Java 虚拟机栈（Java Virtual Machine Stacks）：用于存储局部变量表、操作数栈、动态链接、方法出口等信息；
- 本地方法栈（Native Method Stack）：与虚拟机栈的作用是一样的，只不过虚拟机栈是服务 Java 方法的，而本地方法栈是为虚拟机调用 Native 方法服务的；
- Java 堆（Java Heap）：Java 虚拟机中内存最大的一块，是被所有线程共享的，几乎所有的对象实例都在这里分配内存；
- 方法区（Methed Area）：用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译后的代码等数据。

#### 2. 垃圾回收

**(1) 垃圾回收：Generational Collection 分代收集。**

目前JVM主要采取的一种方法，思想就是把JVM分成不同的区域。每种区域使用不同的垃圾回收方法。

- 新生代(Young Generation)：用于存放新创建的对象，采用复制回收方法，如果在s0和s1之间复制一定次数后，转移到年老代中。这里的垃圾回收叫做minor GC;
- 年老代(Old Generation)：这些对象垃圾回收的频率较低，采用的标记整理方法，这里的垃圾回收叫做 major GC。
- 永久代(Permanent Generation)：存放Java本身的一些数据，当类不再使用时，也会被回收。

在新生代中，分为三个区：Eden, from survivor, to survior。

- 当触发minor GC时，会先把Eden中存活的对象复制到to Survivor中；
- 然后再看from survivor，如果次数达到年老代的标准，就复制到年老代中；如果没有达到则复制到to survivor中，如果to survivor满了，则复制到年老代中。
- 然后调换from survivor 和 to survivor的名字，保证每次to survivor都是空的等待对象复制到那里的。

**(2) 判断是否可以回收，或者存活主要是看：**

1. 堆中是否存在该实例
2. 加载该类的classloader是否已经被回收
3. 该类的java.lang.Class对象在任何地方没有被引用，也就是不能够通过反射方法获取该类信息

**(3) 怎么判断对象是否可以被回收？**

一般有两种方法来判断：

- 引用计数器：为每个对象创建一个引用计数，有对象引用时计数器 +1，引用被释放时计数 -1，当计数器为 0 时就可以被回收。它有一个缺点不能解决循环引用的问题；
- 可达性分析：从 GC Roots 开始向下搜索，搜索所走过的路径称为引用链。当一个对象到 GC Roots 没有任何引用链相连时，则证明此对象是可以被回收的。

**(4) 哪些对象可以作为GC ROOT对象**

1. 虚拟机栈(栈帧中的本地变量表)中引用的对象
2. 本地方法中JNI引用的对象
3. 方法区中的静态变量和常量引用的对象

**(5) 常见的GC算法：**

1. 标记-清除算法：先标记出需要回收的对象，再清除这些被标记了的对象，缺点是：标记清除过程效率不高；会产生内存碎片
2. 复制算法：将内存划分成同等大小两块，只使用其中一块内存，当这一块的内存快用完后，将已存活的对象复制到另外一块内存，再对已使用的内存空间进行一次清理
3. 标记-整理算法：标记出已存活的对象，将对象移动到内存一端，再对端以外的内存进行清理回收
4. 分代收集算法：年轻代使用复制算法,永久代使用 标记-清除或者标记-整理算法

**(6) 说一下 JVM 有哪些垃圾回收器？**

- Serial：最早的单线程串行垃圾回收器。
- Serial Old：Serial 垃圾回收器的老年版本，同样也是单线程的，可以作为 CMS 垃圾回收器的备选预案。
- ParNew：是 Serial 的多线程版本。
- Parallel 和 ParNew 收集器类似是多线程的，但 Parallel 是吞吐量优先的收集器，可以牺牲等待时间换取系统的吞吐量。
- Parallel Old 是 Parallel 老生代版本，Parallel 使用的是复制的内存回收算法，Parallel Old 使用的是标记-整理的内存回收算法。
- CMS：一种以获得最短停顿时间为目标的收集器，非常适用 B/S 系统。
- G1：一种兼顾吞吐量和停顿时间的 GC 实现，是 JDK 9 以后的默认 GC 选项。

**(7) 详细介绍一下 CMS 垃圾回收器？**

CMS 是英文 Concurrent Mark-Sweep 的简称，是以牺牲吞吐量为代价来获得最短回收停顿时间的垃圾回收器。对于要求服务器响应速度的应用上，这种垃圾回收器非常适合。在启动 JVM 的参数加上“-XX:+UseConcMarkSweepGC”来指定使用 CMS 垃圾回收器。

CMS 使用的是标记-清除的算法实现的，所以在 gc 的时候回产生大量的内存碎片，当剩余内存不能满足程序运行要求时，系统将会出现 Concurrent Mode Failure，临时 CMS 会采用 Serial Old 回收器进行垃圾清除，此时的性能将会被降低。

**(8) CMS在进行可达性分析时需要做什么？发生几次？**

会发生“Stop the world”，将JVM暂停，来进行判断对象是否被引用，发生两次，一次在标记的时候，一个在清除的时候（面试官说只会发生一次，在清除的时候）

**(9) 一个对象怎么被清除？**

如果可达性分析算法没有被标记，就会被放入清除队列，当进行第二次标记时，就会被执行Finalizer（终结方法），但是JVM并不知道对象时否执行了finalize

**(8) 新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？**

- 新生代回收器：Serial、ParNew、Parallel Scavenge
- 老年代回收器：Serial Old、Parallel Old、CMS
- 整堆回收器：G1

新生代垃圾回收器一般采用的是复制算法，复制算法的优点是效率高，缺点是内存利用率低；老年代回收器一般采用的是标记-整理的算法进行垃圾回收。

**(9) 简述分代垃圾回收器是怎么工作的？**

分代回收器有两个分区：老生代和新生代，新生代默认的空间占比总空间的 1/3，老生代的默认占比是 2/3。

新生代使用的是复制算法，新生代里有 3 个分区：Eden、To Survivor、From Survivor，它们的默认占比是 8:1:1，它的执行流程如下：

- 把 Eden + From Survivor 存活的对象放入 To Survivor 区；
- 清空 Eden 和 From Survivor 分区；
- From Survivor 和 To Survivor 分区交换，From Survivor 变 To Survivor，To Survivor 变 From Survivor。

每次在 From Survivor 到 To Survivor 移动时都存活的对象，年龄就 +1，当年龄到达 15（默认配置是 15）时，升级为老生代。大对象也会直接进入老生代。

老生代当空间占用到达某个值之后就会触发全局垃圾收回，一般使用标记整理的执行算法。以上这些循环往复就构成了整个分代垃圾回收的整体执行流程。

#### 3. jvm优化

1. 响应时间优先：年轻代设的大些，直到接近系统的最低响应时间限制。年轻代设大，可以减少到达年老代的对象。对于永久代的设置需要参考：永久代并发收集的次数、年轻代和永久代回收时间比例，调整达到一个合适的值
2. 吞吐量优先：年轻代设的大些，永久代较小

**(1) 说一下 JVM 调优的工具？**

JDK 自带了很多监控工具，都位于 JDK 的 bin 目录下，其中最常用的是 jconsole 和 jvisualvm 这两款视图监控工具。

- jconsole：用于对 JVM 中的内存、线程和类等进行监控；
- jvisualvm：JDK 自带的全能分析工具，可以分析：内存快照、线程快照、程序死锁、监控内存的变化、gc 变化等。

**(2) 常用的 JVM 调优的参数都有哪些？**

- -Xms2g：初始化推大小为 2g；
- -Xmx2g：堆最大内存为 2g；
- -XX:NewRatio=4：设置年轻的和老年代的内存比例为 1:4；
- -XX:SurvivorRatio=8：设置新生代 Eden 和 Survivor 比例为 8:2；
- –XX:+UseParNewGC：指定使用 ParNew + Serial Old 垃圾回收器组合；
- -XX:+UseParallelOldGC：指定使用 ParNew + ParNew Old 垃圾回收器组合；
- -XX:+UseConcMarkSweepGC：指定使用 CMS + Serial Old 垃圾回收器组合；
- -XX:+PrintGC：开启打印 gc 信息；
- -XX:+PrintGCDetails：打印 gc 详细信息。

#### 4. 类的生命周期

类的生命周期一个有7个阶段：加载、验证、准备、解析、初始化、使用、卸载

- 加载:
  加载阶段，虚拟机需要完成以下3件事

1. 通过类的全限定名来获取此类的二进制字节流
2. 将字节流所代表的静态存储结构转化为方法区的运行时数据结构
3. 在内存中生成代表这个类的java.lang.Class对象，作为方法区这个类的各种数据访问入口

- 验证：分4个验证

1. 文件格式验证，验证是否符合Class文件格式的规范，并且能被当前版本的虚拟机处理
2. 元数据验证，对字节码描述的信息进行语义分析，以保证其描述的信息符合Java语言规范的要求
3. 字节码验证,通过数据流和控制流分析，确定程序语义是否合法、符合逻辑
4. 符合引用验证，是对类自身以外的信息进行匹配性校验(常量池中各种符合引用)

- 准备：正式为类变量分配内存并设置初始值的阶段，这里设置初始值是数据类型的默认值
- 解析：虚拟机将常量池中的符号引用替换为直接引用的过程
- 初始化：执行类构造器的过程

#### 5. OOM

​        OOM，全称“Out Of Memory”，翻译成中文就是“内存用完了”，来源于java.lang.OutOfMemoryError。看下关于的官方说明： Thrown when the Java Virtual Machine cannot allocate an object because it is out of memory, and no more memory could be made available by the garbage collector. 意思就是说，当JVM因为没有足够的内存来为对象分配空间并且垃圾回收器也已经没有空间可回收时，就会抛出这个error（注：非exception，因为这个问题已经严重到不足以被应用处理）。

**为什么会OOM？**

为什么会没有内存了呢？原因不外乎有两点：

1）分配的少了：比如虚拟机本身可使用的内存（一般通过启动时的VM参数指定）太少。

2）应用用的太多，并且用完没释放，浪费了。此时就会造成内存泄露或者内存溢出。

**内存泄露**：申请使用完的内存没有释放，导致虚拟机不能再次使用该内存，此时这段内存就泄露了，因为申请者不用了，而又不能被虚拟机分配给别人用。

**内存溢出**：申请的内存超出了JVM能提供的内存大小，此时称之为溢出。

在之前没有垃圾自动回收的日子里，比如C语言和C++语言，我们必须亲自负责内存的申请与释放操作，如果申请了内存，用完后又忘记了释放，比如C++中的new了但是没有delete，那么就可能造成内存泄露。偶尔的内存泄露可能不会造成问题，而大量的内存泄露可能会导致内存溢出。

而在Java语言中，由于存在了垃圾自动回收机制，所以，我们一般不用去主动释放不用的对象所占的内存，也就是理论上来说，是不会存在“内存泄露”的。但是，如果编码不当，比如，将某个对象的引用放到了全局的Map中，虽然方法结束了，但是由于垃圾回收器会根据对象的引用情况来回收内存，导致该对象不能被及时的回收。如果该种情况出现次数多了，就会导致内存溢出，比如系统中经常使用的缓存机制。Java中的内存泄露，不同于C++中的忘了delete，往往是逻辑上的原因泄露。

JVM的内存区域大致可以分为Java堆、方法区、虚拟机栈、本地方法栈、程序计数器。除了程序计数器不可能发生OOM之外，其他区域都可能发生OOM。

Java堆：Java堆发生内存溢出，主要是活着的对象占用的空间超过堆空间的大小。避免的方法可以罗列如下：

1.分析是否创建的很多不必要创建的对象；

2.或者是已经应该死掉的对象，没有在正常的声明周期中死掉；

3.或者在前面都正常的情况下，考虑是否可以在成本可以接收的范围内对实现进行重构和优化，避免这种情况；

4.在前面都正常的情况下，查看堆、方法区等等占用内存的比例，看看是否可以调大堆的大小；

5.在前面都正常的情况下，查看物理内存和虚拟机内存的比例，考虑不影响机器上其他应用的前提下，适当加大虚拟机内存；

6.在前面都正常的情况下，考虑适当加大物理机内存。

方法区：方法区是存放Java类文件和运行时常量池的地方，导致OOM也应该主要是这两方面的原因。避免的方法罗列如下：

1.查看是否其他区域的信息是否放到方法区，如果是，考虑是否可以把他们迁出去；

2.分析运行时常量池是否占用内存过多，是否有无必要，就算有必要，是否可以用其他的方式代替，比如在堆中分配；

3.分析不需要的类文件是否过多，是否可以卸载不必要的类文件；

其他的优化方式，类似于Java堆的3.4.5.6，将Java对改成方法区即可。

虚拟机栈：虚拟机栈是Java执行方法的在内存中分配的空间，出现OOM可能有两种情况，栈深度溢出或者因为栈太多导致内存不够（这种情况主要出现在多线征程）。避免的方法罗列如下：

1.栈深度溢出的话，可以考虑加大Java虚拟机栈的大小，如果Java虚拟机栈的空间允许的话；

2.如果由于栈太多，导致OOM，可以考虑适当减小栈的深度（如果可以满足业务需求）来避免；

其他的解决方式可以考虑类似于Java堆的3.4.5.6，将Java对改成虚拟机栈即可。

本地方法栈：本地方法栈是Java虚拟机调用本地方法，所使用的栈空间。解决方法可以罗列如下：

1.考虑优化程序，减少调用本地方法调用的次数，或者加大调用次数减少内存即可；

2.加大物理内存；

3.在某些情况下，也可以考虑调小虚拟机内存，本地方法栈所占的大小。

**APP发生OOM的情况：**

![img](https://uploadfiles.nowcoder.com/images/20171122/5226191_1511340441871_847DE7D22E12A66CA9FAB3F4B3B5E2F1)

#### 6. Java的引用类型

- 强引用：发生 gc 的时候不会被回收。
- 软引用：有用但不是必须的对象，在发生内存溢出之前会被回收。
- 弱引用：有用但不是必须的对象，在下一次GC时会被回收。
- 虚引用（幽灵引用/幻影引用）：无法通过虚引用获得对象，用 PhantomReference 实现虚引用，虚引用的用途是在 gc 时返回一个通知。



## 四、数据

### 1. MySQL

如何获取当前数据库版本？

使用 select version() 获取当前 MySQL 数据库版本。

#### 1.1 数据库的三范式

- 第一范式：强调的是列的原子性，即数据库表的每一列都是不可分割的原子数据项。
- 第二范式：要求实体的属性完全依赖于主关键字。所谓完全依赖是指不能存在仅依赖主关键字一部分的属性。
- 第三范式：任何非主属性不依赖于其它非主属性。

#### 1.2  ACID 特性

- Atomicity（原子性）：一个事务（transaction）中的所有操作，或者全部完成，或者全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被恢复（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。即，事务不可分割、不可约简。
- Consistency（一致性）：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设约束、触发器、级联回滚等。
- Isolation（隔离性）：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
- Durability（持久性）：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。

#### 1.3 Mysql架构

1. 连接层：通信协议、线程处理、用户密码认证
2. SQL层：权限判断、查询缓存、解析器、预处理、查询优化器、缓存、执行计划
3. 存储引擎层：MylSAM、InnoDB、Memory、....

#### 1.4 InnoDB存储结构

逻辑存储单元分为表空间(TableSpace) -> 段(segment) -> 区(extent) -> 页(page)

1. 表空间：所有数据都存在表空间中，表空间分系统表空间和独立表空间。
2. 段：表空间由段组成，一个表通常有数据段、回滚段、索引段等，每个段由N个区和32个零散的页组成。
3. 区：由连续的页组成，每个区大小固定1MB
4. 页：一个区由64个连续页组成，页默认大小16KB        

#### 1.5 InnoDB与MyISAM区别

- InnoDB 引擎：mysql 5.1 后默认的数据库引擎，提供了对数据库 acid 事务的支持，并且还提供了行级锁和外键的约束，它的设计的目标就是处理大数据容量的数据库系统。MySQL 运行的时候，InnoDB 会在内存中建立缓冲池，用于缓冲数据和索引。但是该引擎是不支持全文搜索，同时启动也比较的慢，它是不会保存表的行数的，所以当进行 select count(*) from table 指令的时候，需要进行扫描全表。由于锁的粒度小，写操作是不会锁定全表的,所以在并发度较高的场景下使用会提升效率的。
- MyIASM 引擎：不提供事务的支持，也不支持行级锁和外键。因此当执行插入和更新语句时，即执行写操作的时候需要锁定这个表，所以会导致效率会降低。不过和 InnoDB 不同的是，MyIASM 引擎是保存了表的行数，于是当进行 select count(*) from table 语句时，可以直接的读取已经保存的值而不需要进行扫描全表。所以，如果表的读操作远远多于写操作时，并且不需要事务的支持的，可以将 MyIASM 作为数据库引擎的首选。

| 存储引擎 | InnoDB                      | MyISAM                                  |
| -------- | --------------------------- | --------------------------------------- |
| 存储文件 | .frm表定义文件 .ibd数据文件 | .frm表定义文件.myd数据文件.myi 索引文件 |
| 锁       | 表锁，行锁                  | 表锁                                    |
| 事务     | ACID                        | 不支持                                  |
| CRUD     | 读写                        | 读多                                    |
| count    | 扫表                        | 专门存储的地方                          |
| 索引结构 | B+Tree                      | B+Tree                                  |

**eg:**

一张自增表里面总共有 7 条数据，删除了最后 2 条数据，重启 MySQL 数据库，又插入了一条数据，此时 id 是几？

- 表类型如果是 MyISAM ，那 id 就是 8。
- 表类型如果是 InnoDB，那 id 就是 6。

InnoDB 表只会把自增主键的最大 id 记录在内存中，所以重启之后会导致最大 id 丢失。

#### 1.6 索引

**索引的建立原则：**

1. 最左匹配原则，直到遇到范围查询(>, <, between, like)就停止，比如a = 1 and b = 2 and c >3 and d = 4 如果建立(a,b,c,d)顺序的索引，d是用不到索引的，如果建立(a,b,d,c)的索引则都可以用到，abd的顺序可以任意调整
2. = 和 in可以乱序，比如a = 1 and b =2 and c = 3建立(a, b, c) 索引可以任意顺序，mysql查询优化器会帮你优化
3. 尽量选择区分度高的索引，区分度公式count(distinct col)/count(*) ，表示字段不重复的比例，比例越大我们的扫描记录越少,比例一般是需要join的字段要求是0.1以上，即平均1条扫描10条记录
4. 索引不能参与计算，比如from_unixtime(create_time) = '2014-05-29' 就不能使用到索引，因为b+tree中存的都是数据表中的字段值，但进行检索时，需要把素有元素都应用到函数才能比较，成本大，应该改成create_time = unix_timestamp('2014-05-29')
5. 尽量扩展索引，不要新建索引，比如表中已经有a索引，现在要加(a,b)索引，只需要修改原来的索引即可

**B+ Tree索引 和 哈希索引 限制：**

B+Tree索引：分两类，聚集索引和 普通索引。

聚集索引，在创建表的时候，会创建一个主键，这个主键就是聚集索引，在索引叶子节点中存放了数据信息。InnoDB会给没有创建主键的表选择第一个不包含null值的唯一索引作为主键，如果唯一索引也没有，就会为该表创建一个6字节的rowid作为主键

普通索引，索引叶子节点并不包含所有行的数据，只保留键值，通过键来查找行数据

- 全值匹配，和索引中的所有列进行匹配
- 匹配最左前缀
- 匹配列前缀，可以只匹配某一列的值开头部分
- 匹配范围值，如果匹配的列不是主键，只能使用第一个索引来匹配范围，否则不走索引，如果匹配列是主键，可以不按照索引顺序来，走的是主键索引
- 精确匹配某一个列并范围匹配另外一列

哈希索引：

- 哈希索引只包含哈希值和行指针，而不存储字段值，所以不能使用索引中的值来避免读取行。不过，访问内存中行的速度很快
- 哈希索引数据并不是按照索引值顺序存储的，所以也无法用于排序
- 哈希索引不支持部分索引列匹配查找，因为哈希索引始终使用索引列的全部内容来计算哈希值
- 只支持等值比较查询，包括 =、 in()、<=>，不支持范围查询
- 数据访问速度快，当哈希冲突时，必须遍历链表中的所有行指针，直到查询到符合条件的行
- 哈希冲突多的话，一些索引维护操作的代代价很高

索引用于快速找出在某个列中有一特定值的行。不使用索引，MySQL必须从第1条记录开始然后读完整个表直到找出相关的行。表越大，花费的时间越多。如果表中查询的列有一个索引，MySQL能快速到达一个位置去搜寻到数据文件的中间，没有必要看所有数据。

index abc(b,a,c)指的是建立一个索引名称为abc的多元素索引，这个多元素索引包含a、b、c三个字段

![img](https://static.oschina.net/uploads/space/2016/1117/143233_dyRU_1039336.png)



**在MySQL的user表中对a,b,c三个字段建立联合索引，查询时使用其中的2个作为查询条件，是否还会走索引？**

根据查询字段的位置不同来决定，如查询a,     a,b    a,b,c    a,c   都可以走索引的，其他条件的查询不能走索引。

组合索引 有“最左前缀”原则。就是只从最左面的开始组合，并不是所有只要含有这三列存在的字段的查询都会用到该组合索引。

验证过程如下所示：

首先，在SQLyog中建立一个user表，如下图所示；

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306121502152-871320998.png)

对中间3个字段（user_name,user_age,user_password）进行联合索引 index_user_join

查询情况如下所示：

1.同时查询这3个字段作为条件的SQL，索引情况及SQL语句如下所示：

SELECT *FROM t_user WHERE  user_name='zs' AND user_age=20 AND user_password='123456';

其使用索引情况如下所示：

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306121952690-169769576.png)

从执行结果上可以看到是从走索引进行查询的

2.使用user_age和user_password作为查询条件进行查询，索引及SQL语句如下所示:

 ![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306122821811-334838883.png)

3.使用user_name和user_password作为查询条件进行查询，索引及SQL语句如下所示:

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306123208794-1479608943.png)

4.使用user_name作为查询条件进行查询，索引及SQL语句如下所示:

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306123121508-1181697833.png)

5.使用user_age作为查询条件进行查询，索引及SQL语句如下所示:

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306123040312-2051717284.png)

6.使用user_password作为查询条件进行查询，索引及SQL语句如下所示:

![img](https://img2018.cnblogs.com/blog/1447588/201903/1447588-20190306123003875-1856087516.png)

#### 1.7 事务隔离级别

1. read uncommitted(未提交读) ： 可以看到未提交的数据,脏读
2. read committed (提交读)：只能读取已提交的数据，但多次读取的数据结果可能不一致，导致幻读
3. repeatable read(可重复读)：默认级别，可以重复读，解决了脏读问题，但会有幻读
4. serializable(可串行化)：最高隔离级别，强制事务串行执行，避免幻读问题

查询当前会话级别：select @@tx_isolation;

查看系统当前隔离级别：select @@global.tx_isolation;

设置当前会话隔离级别：set session transaction isolatin level repeatable read;

设置系统当前隔离级别：set global transaction isolation level repeatable read;

#### 1.8 什么是MVCC

MVCC即多版本并发控制，它能在很多情况下避免加锁操作，降低开销，不同的存储引擎实现方式不同，有乐观并发控制和悲观并发控制

MySQL的InnoDB引擎，通过在每行记录后面保存两个隐藏的列来实现，一个列保存了行的创建时间，一个保存了行的过期时间（或删除时间）。实际存储的是系统版本号，每开始一个新的事务，系统版本号都会自动递增，事务开始时刻的系统版本号会作为事务的版本号，用来和查询到的每行记录的版本号进行比较。该MVCC只使用在repeatable read 和 read committed下

保存这两个额外的系统版本号，使大多数读操作都不用加锁，并且也能保证只会读到符合标准的行。缺点是需要额外的存储空间和维护工作。

#### 1.9 锁

**(1) 死锁**

死锁是两个或者多个事务在同一资源上互相占用，并请求锁定对方资源，从而导致互相等待的现象。

两个事务分别执行两个更新语句，都执行第一个语句，锁定了该行数据，但该行数据将做为对方事务执行下条语句的条件，所以当事务继续执行第二条语句的时候，因为需要的条件所在行已被另外一个事务锁定，这是死锁现象

避免死锁的方法：

- 约定以相同的顺序访问表
- 大事务分小事务
- 一个事务中，一次锁定资源
- 锁升级，采用表锁

**(2) 活锁**

活锁也是一种死锁，死锁的话，所有线程都处于阻塞状态，活锁是由于某些条件没有满足，导致一直重复尝试，但有可能自行解开，比如设置了重试次数限制，或者超时时间

**(3) MySQL 的行锁和表锁**

MyISAM 只支持表锁，InnoDB 支持表锁和行锁，默认为行锁。

- 表级锁：开销小，加锁快，不会出现死锁。锁定粒度大，发生锁冲突的概率最高，并发量最低。
- 行级锁：开销大，加锁慢，会出现死锁。锁力度小，发生锁冲突的概率小，并发度最高。

**(4) 乐观锁和悲观锁**

- 乐观锁：每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在提交更新的时候会判断一下在此期间别人有没有去更新这个数据。
- 悲观锁：每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会阻止，直到这个锁被释放。

数据库的乐观锁需要自己实现，在表里面添加一个 version 字段，每次修改成功值加 1，这样每次修改的时候先对比一下，自己拥有的 version 和数据库现在的 version 是否一致，如果不一致就不修改，这样就实现了乐观锁。

**(5) sleep 和 wait 的区别：**

sleep：

- 让当前线程休眠指定时间
- 不释放锁资源
- 可通过调用interrupt()方法来唤醒休眠线程

wait：

- 让当前线程进入等待状态，当其他线程调用notify或者notifyAll方法时，当前线程进入就绪状态
- 当前线程会释放已获取的锁资源，并进入等待队列

#### 1.11 Msyql 执行SQL 过程

1. 客户端发送一条查询给服务器
2. 服务器先检查查询缓存，如果命中了缓存，则立刻返回存储在缓存中的结果。否则进入下一阶段
3. 服务器端进行SQL解析，预处理，再由优化器生成对应的执行计划
4. MySQL根据优化器生成的执行计划，调用存储引擎的API来执行查询
5. 将结果返回给客户端

#### 1.12 如何优化sql翻页

1. 只让用户一页页翻，不能跳页
2. 确定每页的边界值，通过where条件查询来优化
3. 使用延迟关联，通过使用覆盖索引查询返回需要的主键，再根据这些主键关联原有表获得需要的行

#### 1.13 如何优化sql语句

1. 先看表的数据类型是否设计的合理，遵守选取数据类型越简单越小的原则
2. 表中的碎片是否整理
3. 表的统计信息是否收集，只有统计信息准确，执行计划才可以帮助我们优化SQL
4. 查看执行计划，检查索引的使用情况，没有用到索引，创建索引
5. 创建索引需要判断这个字段是否适合创建索引，遵守建立索引的原则
6. 创建索引后，通过explain分析，前后性能变化

#### 1.14 如何分析explain计划

先查看type列，如果出现all关键词，就代表sql执行全表扫描

再看key列，如果null代表没有使用索引

再看rows列，如果越大，代表需要扫描的行数越多，相应耗时就长

最后看 extra列，是否有影响性能的 Using filesort 或者 Using temporary

explain 各个字段含义：<https://blog.csdn.net/weixin_34062469/article/details/94498678>

### 2. Redis

#### 2.1 Redis 简介

Redis 是一个使用 C 语言开发的高速缓存数据库。

Redis **使用场景**：

- 记录帖子点赞数、点击数、评论数；
- 缓存近期热帖；
- 缓存文章详情信息；
- 记录用户会话信息。

Redis 有哪些**功能**：

- 数据缓存功能
- 分布式锁的功能
- 支持数据持久化
- 支持事务
- 支持消息队列

#### 2.2. Redis、MongoDB 、Memcache 的区别

**(1) Redis**

**Redis**（内存数据库）是一个key-value存储系统（布式内缓存，高性能的key-value数据库）。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave（主从）同步。

**特点：**

- 支持多种数据结构，如 string（字符串）、 list(双向链表)、dict(hash表)、set(集合）、zset(排序set)、hyperloglog（基数估算）；
- 支持持久化操作，可以进行aof及rdb数据持久化到磁盘，从而进行数据备份或数据恢复等操作，较好的防止数据丢失的手段；
- 支持通过Replication进行数据复制，通过master-slave机制，可以实时进行数据的同步复制，支持多级复制和增量复制，master-slave机制是Redis进行HA的重要手段；
- 单线程请求，所有命令串行执行，并发情况下不需要考虑数据一致性问题；
- 支持pub/sub消息订阅机制，可以用来进行消息订阅与通知；
- 支持简单的事务需求，但业界使用场景很少，并不成熟。
- Redis只能使用单线程，性能受限于CPU性能，故单实例CPU最高才可能达到5-6wQPS每秒（取决于数据结构，数据大小以及服务器硬件性能，日常环境中QPS高峰大约在1-2w左右）；
- 支持简单的事务需求，但业界使用场景很少，并不成熟，既是优点也是缺点；
- 支持（快照、AOF）：依赖快照进行持久化，AOF增强了可靠性的同时，对性能有所影响；
- Redis在string类型上会消耗较多内存，可以使用dict（hash表）压缩存储以降低内存耗用；
- MC和Redis都是Key-Value类型，不适合在不同数据集之间建立关系，也不适合进行查询搜索。比如redis的keys pattern这种匹配操作，对redis的性能是灾难；
- Redis在2.0版本后增加了自己的VM特性，突破物理内存的限制；可以对key value设置过期时间（类似memcache）；
- Redis事务支持比较弱，只能保证事务中的每个操作连续执行，

**和 Memcache 区别：**

- 存储方式不同：memcache 把数据全部存在内存之中，断电后会挂掉，数据不能超过内存大小；Redis 有部份存在硬盘上，这样能保证数据的持久性。
- 数据支持类型：memcache 对数据类型支持相对简单；Redis 有复杂的数据类型。
- 使用底层模型不同：它们之间底层实现方式，以及与客户端之间通信的应用协议不一样，Redis 自己构建了 vm 机制，因为一般的系统调用系统函数的话，会浪费一定的时间去移动和请求。
- value 值大小不同：Redis 最大可以达到 512mb；memcache 只有 1mb。

**(2) MongoDB** 

**MongoDB**（NoSQL数据库）是一个介于关系数据库和非关系数据库之间的产品（基于分布式文件存储的数据库），是非关系数据库当中功能最丰富，最像关系数据库的。他支持的数据结构非常松散，是类似json的bson格式，因此可以存储比较复杂的数据类型。Mongo最大的特点是他支持的查询语言非常强大，其语法有点类似于面向对象的查询语言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。

**特点：**

- 适合大数据量的存储，依赖操作系统VM做内存管理，吃内存也比较厉害，服务不要和别的服务在一起；
- 支持丰富的数据表达，索引，最类似关系型数据库，支持的查询语言非常丰富；
- 支持master-slave,replicaset（内部采用paxos选举算法，自动故障恢复）,auto sharding机制，对客户端屏蔽了故障转移和切分机制；
- 从1.8版本开始采用binlog方式支持持久化的可靠性；
- MongoDB不支持事务；
- MongoDB内置了数据分析的功能(mapreduce),其他不支持

**和 Redis 区别：**

就Redis和MongoDB来说，大家一般称之为**Redis缓存、MongoDB数据库**。

| 比较指标   | MongoDB(v2.4.9)                                              | Redis(v2.4.17)                                               | 比较说明                                                     |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 实现语言   | c++                                                          | c/c++                                                        | -                                                            |
| 协议       | BSON,自定义二进制                                            | 类telnet                                                     | -                                                            |
| 性能       | 依赖内存,TPS较高                                             | 依赖内存,TPS非常高                                           | Redis优于MongoDB                                             |
| 可操作性   | 丰富的数据表达,索引;最类似于关系型数据库,支持丰富的查询语句  | 数据丰富,较少的IO                                            | MongoDB优于Redis                                             |
| 内存及存储 | 适合大数据量存储,依赖系统虚拟内存,采用镜像文件存储;内存占用率比较高,官方建议独立部署在64位系统 | Redis2.0后支持虚拟内存特性(VM) 突破物理内存限制;数据可以设置时效性,类似于memcache | 不同的应用场景,各有千秋                                      |
| 可用性     | 支持master-slave,replicatset(内部采用paxos选举算法,自动故障恢复),auto sharding机制,对客户端屏蔽了故障转移和切片机制 | 依赖客户端来实现分布式读写;主从复制时,每次从节点重新连接主节点都要依赖整个快照,无增量复制;不支持auto sharding,需要依赖程序设定一致性hash机制 | MongoDB优于Redis；单点问题上,MongoDB应用简单,相对用户透明,Redis比较复杂,需要客户端主动解决.(MongoDB一般使用replicasets和sharding相结合,replicasets侧重高可用性以及高可靠,sharding侧重性能,水平扩展) |
| 可靠性     | 从1.8版本后,采用binlog方式(类似Mysql) 支持持久化             | 依赖快照进行持久化;AOF增强可靠性;增强性的同时,影响访问性能   |                                                              |
| 一致性     | 不支持事务,靠客户端保证                                      | 支持事务,比较脆,仅能保证事务中的操作按顺序执行               | Redis优于MongoDB                                             |
| 数据分析   | 内置数据分析功能(mapreduce)                                  | 不支持                                                       | MongoDB优于Redis                                             |
| 应用场景   | 海量数据的访问效率提升                                       | 较小数据量的性能和运算                                       | MongoDB优于Redis                                             |

**TPS 和 QPS：**

**TPS**：Transactions Per Second（每秒传输的事物处理个数），即服务器每秒处理的事务数。TPS包括一条消息入和一条消息出，加上一次用户数据库访问。（业务TPS = CAPS × 每个呼叫平均TPS）

TPS是软件测试结果的测量单位。一个事务是指一个客户机向服务器发送请求然后服务器做出反应的过程。客户机在发送请求时开始计时，收到服务器响应后结束计时，以此来计算使用的时间和完成的事务个数。

一般的，评价系统性能均以每秒钟完成的技术交易的数量来衡量。系统整体处理能力取决于处理能力最低模块的TPS值。

**QPS**：每秒查询率QPS是对一个特定的查询服务器在规定时间内所处理流量多少的衡量标准，在因特网上，作为域名系统服务器的机器的性能经常用每秒查询率来衡量。

对应fetches/sec，即每秒的响应请求数，也即是最大吞吐能力。

**(3) Memcached**

**Memcached**（内存Cache）是一个高性能的分布式内存对象缓存系统，用于动态Web应用以减轻数据库负载。它通过在内存中缓存数据和对象来减少读取数据库的次数，从而提高动态、数据库驱动网站的速度。Memcached基于一个存储键/值对的hashmap。其守护进程（daemon ）是用[C](http://baike.baidu.com/item/C/7252092)写的，但是客户端可以用任何语言来编写，并通过memcached协议与守护进程通信。

**特点：**

- 可以利用多核优势，单实例吞吐量极高，可以达到几十万QPS（取决于key、value的字节大小以及服务器硬件性能，日常环境中QPS高峰大约在4-6w左右）。适用于最大程度扛量；
- 支持直接配置为session handle。
- 只支持简单的key/value数据结构，不像Redis可以支持丰富的数据类型；
- 无法进行持久化，数据不能备份，只能用于缓存使用，且重启后数据全部丢失；
- 无法进行数据同步，不能将MC中的数据迁移到其他MC实例中；
- 内存分配采用Slab Allocation机制管理内存，value大小分布差异较大时会造成内存利用率降低，并引发低利用率时依然出现踢出等问题。需要用户注重value设计。
- Memcached可以修改最大可用内存,采用LRU算法。

**(4) 应用场景**

- Redis 适用于对读写效率要求都很高，数据处理业务复杂和对安全性要求较高的系统（如新浪微博的计数和微博发布部分系统，对数据安全性、读写要求都很高）。
- MongoDB 主要解决海量数据的访问效率问题。
- Memcached 动态系统中减轻数据库负载，提升性能；做缓存，适合多读少写，大数据量的情况（如人人网大量查询用户信息、好友信息、文章信息等）；用于在动态系统中减少数据库负载，提升性能;做缓存，提高性能（适合读多写少，对于数据量比较大，可以采用sharding）。

#### 2.3 缓存问题

**(1) 缓存穿透**

缓存穿透是指，缓存中不存在该key的数据，于是就是去数据库中查询，如果流量一大，就会打趴数据库

优化:

1. 缓存空对象

   对于不存在的数据，依旧将空值缓存起来。但这会造成内存空间的浪费，可以针对这类数据加一个过期时间。对于缓存和存储层数据的一致性，可以在过期的时候，请求存储层，或者通过消息系统更新缓存

2. 布隆过滤器

   将所有存在的数据做成布隆过滤器，可以使用Bitmaps实现，其在大数据量下空间占用小

   Redis4.0以上采用插件集成

   原理：

   在redis中是一个大型的位数组，通过计算key的hash然后对数组长度取模得到一个位置，进行写入；在判断是否存在时，判断位数组中几个位置是否都为1，只要一个位为0，就说明这个key不存在。布隆过滤器也会存在一定的误判，如果位数组比较稀疏，概率就会很大，否则就会降低。

**(2) 缓存雪崩**

指缓存由于大量请求，造成缓存挂掉，大量请求直接打到存储层，造成存储层挂机

优化：

1. 使用主从，哨兵，集群模式保证缓存高可用
2. 依赖隔离组件为后端限流并降级
3. 提前演练，做好后备方案

**(3) 缓存更新方式**

同步更新，先写入数据库，写入成功后，再更新缓存。

异步更新，通过消息中间件进行触发更新。

失效更新，在取不到缓存的时候，从数据库取数据，再更新缓存。

定时更新，通过定时任务来更新缓存

**(4) 缓存不一致**

通过增加重试机制，补偿任务，达到最终一致

**(5) 热点key重建**

优化

1. 使用互斥锁，只允许一个线程重建缓存
2. 使用逻辑缓存过期，在value中存一个key过期时间，在获取key的时候通过逻辑时间进行判断

#### 2.4 如何和数据库保证一致性

- 合理设置缓存的过期时间。
- 新增、更改、删除数据库操作时同步更新 Redis，可以使用事物机制来保证数据的一致性。

1. 更新操作，先删除缓存，再修改数据库，如果数据库失败，数据库中的还是旧数据，缓存是空的，在查询的时候，发现缓存是空的，就会从数据库取数据，然后更新到缓存中

2. 方案一在高并发下，先删除了缓存，但数据库还没修改成功，此时读请求过来，发现没有缓存，就会去查询数据库，放入缓存，随后更新数据库操作完成了，此时缓存中的数据是旧数据，与数据库中的数据不一致。

   方案如下：

   在请求的时候，发现没有缓存，就发一个更新操作，到JVM队列，主线程循环判断缓存是否更新，并设置超时时间，如果超时，就直接取数据库数据，返回旧数据。JVM队列中，如果之前已经有更新操作，自动丢弃后面的更新操作，防止频繁更新。具体如下图所示：

   ![img](https://img-blog.csdnimg.cn/20190322174249523.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2dseTEyNTYyODgzMDc=,size_16,color_FFFFFF,t_70)

   如果实例服务是分布式部署，需要将同一请求路由到同一个实例，可以通过某个请求参数的hash路由，也可以通过Nginx的hash路由功能

   细想该方案，其实还有几个优化点：

   1、读请求过多的时候，队列里面会有多个“更新缓存”操作串在一起，其实是没有意义的，往队列里面塞数据的时候可以先判断一下，有的话就不用再塞进去了

   2、遇到更新DB比较频繁的业务场景时，可能会导致读请求长时间阻塞，这个时候可以通过扩机器增加吞吐量，或者可以先返回一个旧的值

#### 2.4 其他

**(1) Redis 为什么是单线程的？为什么单线程还能这么快？**

因为 cpu 不是 Redis 的瓶颈，Redis 的瓶颈最有可能是机器内存或者网络带宽。既然单线程容易实现，而且 cpu 又不会成为瓶颈，那就顺理成章地采用单线程的方案了。

关于 Redis 的性能，官方网站也有，普通笔记本轻松处理每秒几十万的请求。

而且单线程并不代表就慢 nginx 和 nodejs 也都是高性能单线程的代表。

单线程能够避免线程切换和竞态产生的消耗，而且单线程可以简化数据结构和算法的实现。

至于单线程还快，是因为Redis是基于内存的数据库，内存响应速度是很快的，并且采用epoll作为I/O多路复用技术，再加上Redis自身的事件处理模型将epoll中的连接、读写、关闭都转换为事件，不在网络I/O上浪费过多时间

**(2) Redis 支持的数据类型有哪些？**

Redis 支持的数据类型：string（字符串）、list（列表）、hash（字典）、set（集合）、zset（有序集合）。

Redis 支持的 Java 客户端都有哪些？

支持的 Java 客户端有 Redisson、jedis、lettuce 等。

**(3) jedis 和 Redisson 有哪些区别？**

- jedis：提供了比较全面的 Redis 命令的支持。
- Redisson：实现了分布式和可扩展的 Java 数据结构，与 jedis 相比 Redisson 的功能相对简单，不支持排序、事务、管道、分区等 Redis 特性。

**(4) Redis 持久化有几种方式？**

Redis 的持久化有两种方式，或者说有两种策略：

- RDB（Redis Database）：指定的时间间隔能对你的数据进行快照存储。
- AOF（Append Only File）：每一个收到的写命令都通过write函数追加到文件中。

**(5) Redis 怎么实现分布式锁？**

Redis 分布式锁其实就是在系统里面占一个“坑”，其他程序也要占“坑”的时候，占用成功了就可以继续执行，失败了就只能放弃或稍后重试。

占坑一般使用 setnx(set if not exists)指令，只允许被一个程序占有，使用完调用 del 释放锁。

**(6) Redis 分布式锁有什么缺陷？**

Redis 分布式锁不能解决超时的问题，分布式锁有一个超时时间，程序的执行如果超出了锁的超时时间就会出现问题。

**(7) Redis 如何做内存优化？**

尽量使用 Redis 的散列表，把相关的信息放到散列表里面存储，而不是把每个字段单独存储，这样可以有效的减少内存使用。比如将 Web 系统的用户对象，应该放到散列表里面再整体存储到 Redis，而不是把用户的姓名、年龄、密码、邮箱等字段分别设置 key 进行存储。

**(8) Redis 淘汰策略有哪些？**

- volatile-lru：从已设置过期时间的数据集（server. db[i]. expires）中挑选最近最少使用的数据淘汰。
- volatile-ttl：从已设置过期时间的数据集（server. db[i]. expires）中挑选将要过期的数据淘汰。
- volatile-random：从已设置过期时间的数据集（server. db[i]. expires）中任意选择数据淘汰。
- allkeys-lru：从数据集（server. db[i]. dict）中挑选最近最少使用的数据淘汰。
- allkeys-random：从数据集（server. db[i]. dict）中任意选择数据淘汰。
- no-enviction（驱逐）：禁止驱逐数据。

**(9) Redis 常见的性能问题有哪些？该如何解决？**

- 主服务器写内存快照，会阻塞主线程的工作，当快照比较大时对性能影响是非常大的，会间断性暂停服务，所以主服务器最好不要写内存快照。
- Redis 主从复制的性能问题，为了主从复制的速度和连接的稳定性，主从库最好在同一个局域网内。

**(10)数据库集群和redis集群**

数据库集群：顾名思义，就是利用至少两台或者多台数据库服务器，构成一个虚拟单一数据库逻辑映像，像单数据库系统那样，向客户端提供透明的数据服务。

redis集群：主从模式、Sentinel模式、Cluster模式

### 3. 亿级数据处理

**背景**：

随着公司业务增长，如果每天1000多万笔订单的话，3个月将有约10亿的订单量，之前数据库采用单库单表的形式已经不满足于业务需求，数据库改造迫在眉睫。

**订单数据如何划分**：

我们可以将订单数据划分成两大类型：分别是热数据和冷数据。

- 热数据：3个月内的订单数据，查询实时性较高;
- 冷数据A：3个月 ~ 12个月前的订单数据，查询频率不高;
- 冷数据B：1年前的订单数据，几乎不会查询，只有偶尔的查询需求;

可能这里有个疑惑为什么要将冷数据分成两类，因为根据实际场景需求，用户基本不会去查看1年前的数据，如果将这部分数据还存储在db中，那么成本会非常高，而且也不便于维护。另外如果真遇到有个别用户需要查看1年前的订单信息，可以让用户走离线数据查看。

对于这三类数据的存储，目前规划如下：

- 热数据： 使用mysql进行存储，当然需要分库分表；
- 冷数据A: 对于这类数据可以存储在ES中，利用搜索引擎的特性基本上也可以做到比较快的查询；
- 冷数据B: 对于这类不经常查询的数据，可以存放到Hive中；

**Mysql如何分库分表**：

**按业务划分**：在业务初始阶段，为了加快应用上线和快速迭代，很多应用都采用集中式的架构。但是随着业务系统的扩大，系统匾额越来越复杂，越来越难以维护，开发效率变得越来越低，并且对资源的消耗也变得越来越大，通过硬件提高系统性能的成本会变得更高。

通常一般的电商平台，包含了用户、商品、订单等几大模块，简单的做法是在同一个库中分别建这几张表，如：用户表、商品表、订单表 等等

但是随着业务的提升，将所有业务都放在一个库中已经变得越来越难以维护，因此我们建议，将不同业务放在不同的库中，如：用户库、商品库、订单库 等等

由图中我们可以看出，我们将不同的业务放到不同的库中，将原来所有压力由同一个库中分散到不同的库中，提升了系统的吞吐量。

**分库与分表**：我们知道每台机器无论配置多么好它都有自身的物理上限，所以当我们应用已经能触及或远远超出单台机器的某个上限的时候，我们惟有寻找别的机器的帮助或者继续升级的我们的硬件，但常见的方案还是通过添加更多的机器来共同承担压力。

我们还得考虑当我们的业务逻辑不断增长，我们的机器能不能通过线性增长就能满足需求？因此，使用数据库的分库分表，能够立竿见影的提升系统的性能，关于为什么要使用数据库的分库分表的其他原因这里不再赘述，主要讲具体的实现策略。

(1)分表策略：

(2)分库策略：

(3)分库分表结合使用策略：

**整体架构设计：**

从图中我们将请求分成read和write请求，write请求比较简单，就是根据分库分表规则写入db即可。

对于read请求，我们需要计算出查询的是热数据还是冷数据，一般order_id生成规则如下，“商户所在地区号+时间戳+随机数”，我们可以根据时间戳计算出查询的是热数据还是冷数据，（当然具体业务需要具体对待，这里不再详细阐述）

另外架构图中的冷数据指的是3个月~12个月前的数据，如果是查询一年前的数据，建议直接离线查hive即可。

图中有一个定时Job，主要用来定时迁移订单数据，需要将冷数据分别迁移到ES和hive中。

**如何把系统不停机迁移到分库分表中？**

简单来说，就是在线上系统里面，之前所有写库的地方，增删改操作，都除了对老库增删改，都加上对新库的增删改，这就是所谓双写，同时写俩库，老库和新库。

然后系统部署之后，新库数据差太远，用之前说的导数工具，跑起来读老库数据写新库，写的时候要根据gmt_modified这类字段判断这条数据最后修改的时间，除非是读出来的数据在新库里没有，或者是比新库的数据新才会写。

接着导万一轮之后，有可能数据还是存在不一致，那么就程序自动做一轮校验，比对新老库每个表的每条数据，接着如果有不一样的，就针对那些不一样的，从老库读数据再次写。反复循环，直到两个库每个表的数据都完全一致为止。

接着当数据完全一致了，就ok了，基于仅仅使用分库分表的最新代码，重新部署一次，不就仅仅基于分库分表在操作了么，还没有几个小时的停机时间，很稳。所以现在基本玩儿数据迁移之类的，都是这么干了。

## 五、数据结构

#### 1. B树 和 B+树 的区别

B+树 的中间节点不保存数据，所以磁盘页能容纳更多节点元素；

B+树查询必须查找到叶子节点，B树只要匹配到即可不用管元素位置，因此B+树查找更稳定

对于范围查找来说，B+树只需遍历叶子节点链表即可，B树却要重复地中序遍历

**(1) B树：**

  每个节点都存储key和data，所有节点组成这棵树，并且叶子节点指针为null。

  ![img](https://img-blog.csdn.net/20170920132504569?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemh1YW56aGUxMTc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

 **(2) B+树：**

  只有叶子节点存储data，叶子节点包含了这棵树的所有键值，叶子节点不存储指针。

  ![img](https://img-blog.csdn.net/20170920132523536?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemh1YW56aGUxMTc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

​        后来，在B+树上增加了顺序访问指针，也就是每个叶子节点增加一个指向相邻叶子节点的指针，这样一棵树成了 数据库系统实现索引的首选数据结构。 

        原因有很多，最主要的是这棵树矮胖，呵呵。一般来说，索引很大，往往以索引文件的形式存储的磁盘上，索引查找时产生磁盘I/O消耗，相对于内存存取，I/O存取的消耗要高几个数量级，所以评价一个数据结构作为索引的优劣最重要的指标就是在查找过程中磁盘I/O操作次数的时间复杂度。树高度越小，I/O次数越少。 

        那为什么是B+树而不是B树呢，因为它内节点不存储data，这样一个节点就可以存储更多的key。

       在MySQL中，最常用的两个存储引擎是MyISAM和InnoDB，它们对索引的实现方式是不同的。

**(3) MyISAM：**

  data存的是数据地址。索引是索引，数据是数据。索引放在XX.MYI文件中，数据放在XX.MYD文件中，所以也叫非聚集索引。

  ![img](https://img-blog.csdn.net/20170920132633099?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemh1YW56aGUxMTc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

 

**(4) InnoDB：**

  data存的是数据本身。索引也是数据。数据和索引存在一个XX.IDB文件中，所以也叫聚集索引。

  ![img](https://img-blog.csdn.net/20170920132729406?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemh1YW56aGUxMTc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

  了解了数据结构再看索引，一切都不费解了，只是顺着逻辑推而已。另加两种存储引擎的区别：

1、MyISAM是非事务安全的，而InnoDB是事务安全的

2、MyISAM锁的粒度是表级的，而InnoDB支持行级锁

3、MyISAM支持全文类型索引，而InnoDB不支持全文索引

4、MyISAM相对简单，效率上要优于InnoDB，小型应用可以考虑使用MyISAM

5、MyISAM表保存成文件形式，跨平台使用更加方便

6、MyISAM管理非事务表，提供高速存储和检索以及全文搜索能力，如果在应用中执行大量select操作可选择

7、InnoDB用于事务处理，具有ACID事务支持等特性，如果在应用中执行大量insert和update操作，可选择。

#### 2. 二叉树结构

二叉树每个节点至多有两个节点，左节点永远比右节点小，并且小于根节点。

查找最好时间复杂度O(longN), 最坏O(N)

插入删除操作时间复杂度跟查找差不多

**(1) 相关练习题：**

一个高度为h的满二叉树共有n个结点，其中有m个叶子结点，则：

满二叉树的高度和节点总数满足下列关系 n = 2^h - 1;而且叶子节点全都位于第 H 层，所以又有 m = 2^(h-1);

易知 n = 2*m-1;

#### 3. 平衡二叉树 (AVL)

左右子树的高度差不超过1，并且左右子树都是平衡二叉树，超过1就旋转。

比二叉树稳定，查找时间复杂度O(logN)

插入操作最多需要旋转1次，时间复杂度O(logN)左右

删除时间复杂度O(2logN)

#### 4. 红黑树

每个节点上都有节点颜色，可以是红色或者黑色；根节点必须是黑色；每个红色节点的子节点，父节点是黑色；从任一节点到每个叶子节点的所有路径都包含相同数目的黑色节点。

查找效率最好情况下是O(logN)，最坏情况下比平衡二叉树要差一些，但也比二叉树要好

插入和删除操作改变树的平衡性概率小于平衡二叉树

#### 5. 栈和队列

**(1) 栈**：是一种特殊的线性表。其特殊性在于限定插入和删除数据元素的操作只能在线性表的一端进行。

结论：后进先出（Last In First Out），简称为LIFO线性表。

栈的基本运算有六种：

构造空栈：InitStack(S)、

判栈空: StackEmpty(S)、

判栈满： StackFull(S)、

进栈： Push(S,x)、可形象地理解为压入，这时栈中会多一个元素

退栈： Pop(S) 、 可形象地理解为弹出，弹出后栈中就无此元素了。

取栈顶元素：StackTop(S),不同与弹出，只是使用栈顶元素的值，该元素仍在栈顶不会改变。

**(2) 队列：**也是一种运算受限的线性表，它的运算限制与栈不同，是两头都有限制，插入只能在表的一端进行(只进不出)，而删除只能在表的另一端进行(只出不进)，允许删除的一端称为队尾(rear)，允许插入的一端称为队头 (Front)

队列的操作原则是先进先出的，所以队列又称作FIFO表(First In First Out)

队列的基本运算也有六种：

置空队 ：InitQueue(Q)

判队空： QueueEmpty(Q)

判队满： QueueFull(Q)

入队 ： EnQueue(Q,x)

出队 ： DeQueue(Q)

取队头元素： QueueFront(Q),不同与出队，队头元素仍然保留。

#### 6 查找

**查找定义：**根据给定的某个值，在查找表中确定一个其关键字等于给定值的数据元素（或记录）。

主要算法有：顺序查找、二分查找、插入查找、斐波那契查找、数表查找、分块查找、哈希查找。

**查找算法分类：**

　　1）静态查找和动态查找；

　　　　注：静态或者动态都是针对查找表而言的。动态表指查找表中有删除和插入操作的表。

　　2）无序查找和有序查找。

　　　　无序查找：被查找数列有序无序均可；

　　　　有序查找：被查找数列必须为有序数列。

**平均查找长度（Average Search Length，ASL）：**需和指定key进行比较的关键字的个数的期望值，称为查找算法在查找成功时的平均查找长度。

　　对于含有n个数据元素的查找表，查找成功的平均查找长度为：ASL = Pi*Ci的和。
　　Pi：查找表中第i个数据元素的概率。
　　Ci：找到第i个数据元素时已经比较过的次数。

**(1) 顺序查找**

**说明：顺序查找适合于存储结构为顺序存储或链接存储的线性表。**

　　**基本思想：**顺序查找也称为线形查找，属于无序查找算法。从数据结构线形表的一端开始，顺序扫描，依次将扫描到的结点关键字与给定值k相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于k的结点，表示查找失败。

　　**复杂度分析：**　

　　查找成功时的平均查找长度为：（假设每个数据元素的概率相等） ASL = 1/n(1+2+3+…+n) = (n+1)/2 ;
　　当查找不成功时，需要n+1次比较，时间复杂度为O(n);

　　所以，**顺序查找的时间复杂度为O(n)。**

**(2) 二分查找**

**说明：元素必须是有序的，如果是无序的则要先进行排序操作。**

　　**基本思想：**也称为是折半查找，属于有序查找算法。用给定值k先与中间结点的关键字比较，中间结点把线形表分成两个子表，若相等则查找成功；若不相等，再根据k与该中间结点关键字的比较结果确定下一步查找哪个子表，这样递归进行，直到查找到或查找结束发现表中没有这样的结点。

　　**复杂度分析：**最坏情况下，关键词比较次数为log2(n+1)，且**期望时间复杂度为O(log2n)**；

　　注：折半查找的前提条件是需要有序表顺序存储，对于静态查找表，一次排序后不再变化，折半查找能得到不错的效率。但对于需要频繁执行插入或删除操作的数据集来说，维护有序的排序会带来不小的工作量，那就不建议使用。——《大话数据结构》

**(3) 插入查找**

在介绍插值查找之前，首先考虑一个新问题，为什么上述算法一定要是折半，而不是折四分之一或者折更多呢？

　　打个比方，在英文字典里面查“apple”，你下意识翻开字典是翻前面的书页还是后面的书页呢？如果再让你查“zoo”，你又怎么查？很显然，这里你绝对不会是从中间开始查起，而是有一定目的的往前或往后翻。

　　同样的，比如要在取值范围1 ~ 10000 之间 100 个元素从小到大均匀分布的数组中查找5， 我们自然会考虑从数组下标较小的开始查找。

　　经过以上分析，折半查找这种查找方式，不是自适应的（也就是说是傻瓜式的）。二分查找中查找点计算如下：

　　mid=(low+high)/2, 即mid=low+1/2*(high-low);

　　通过类比，我们可以将查找的点改进为如下：

　　mid=low+(key-a[low])/(a[high]-a[low])*(high-low)，

　　也就是将上述的比例参数1/2改进为自适应的，根据关键字在整个有序表中所处的位置，让mid值的变化更靠近关键字key，这样也就间接地减少了比较次数。

　　**基本思想：**基于二分查找算法，将查找点的选择改进为自适应选择，可以提高查找效率。当然，差值查找也属于有序查找。

　　注：**对于表长较大，而关键字分布又比较均匀的查找表来说，插值查找算法的平均性能比折半查找要好的多。反之，数组中如果分布非常不均匀，那么插值查找未必是很合适的选择。**

　　**复杂度分析：查找成功或者失败的时间复杂度均为O(log2(log2n))。**

**(4) 斐波那契查找**

在介绍斐波那契查找算法之前，我们先介绍一下很它紧密相连并且大家都熟知的一个概念——黄金分割。

　　黄金比例又称黄金分割，是指事物各部分间一定的数学比例关系，即将整体一分为二，较大部分与较小部分之比等于整体与较大部分之比，其比值约为1:0.618或1.618:1。

　　0.618被公认为最具有审美意义的比例数字，这个数值的作用不仅仅体现在诸如绘画、雕塑、音乐、建筑等艺术领域，而且在管理、工程设计等方面也有着不可忽视的作用。因此被称为黄金分割。

　　大家记不记得斐波那契数列：1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89…….（从第三个数开始，后边每一个数都是前两个数的和）。然后我们会发现，随着斐波那契数列的递增，前后两个数的比值会越来越接近0.618，利用这个特性，我们就可以将黄金比例运用到查找技术中。

![img](https://img-blog.csdn.net/20150323100632467?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc2hlbmJvMjAzMA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

**基本思想：**也是二分查找的一种提升算法，通过运用黄金比例的概念在数列中选择查找点进行查找，提高查找效率。同样地，斐波那契查找也属于一种有序查找算法。

　　相对于折半查找，一般将待比较的key值与第mid=（low+high）/2位置的元素比较，比较结果分三种情况：

　　1）相等，mid位置的元素即为所求

　　2）>，low=mid+1;

​     3）<，high=mid-1。

　　斐波那契查找与折半查找很相似，他是根据斐波那契序列的特点对有序表进行分割的。他要求开始表中记录的个数为某个斐波那契数小1，及n=F(k)-1;

 开始将k值与第F(k-1)位置的记录进行比较(及mid=low+F(k-1)-1),比较结果也分为三种

　　1）相等，mid位置的元素即为所求

　　2）>，low=mid+1,k-=2;

　　说明：low=mid+1说明待查找的元素在[mid+1,high]范围内，k-=2 说明范围[mid+1,high]内的元素个数为n-(F(k-1))= Fk-1-F(k-1)=Fk-F(k-1)-1=F(k-2)-1个，所以可以递归的应用斐波那契查找。

　　3）<，high=mid-1,k-=1。

　　说明：low=mid+1说明待查找的元素在[low,mid-1]范围内，k-=1 说明范围[low,mid-1]内的元素个数为F(k-1)-1个，所以可以递归 的应用斐波那契查找。

　　**复杂度分析：最坏情况下，时间复杂度为O(log2n)，且其期望复杂度也为O(log2n)。**

**(5) 数表查找**

* **最简单的树表查找算法——二叉树查找算法。**

　　**基本思想：**二叉查找树是先对待查找的数据进行生成树，确保树的左分支的值小于右分支的值，然后在就行和每个节点的父节点比较大小，查找最适合的范围。 这个算法的查找效率很高，但是如果使用这种查找方法要首先创建树。 

**二叉查找树**（BinarySearch Tree，也叫二叉搜索树，或称二叉排序树Binary Sort Tree）或者是一棵空树，或者是具有下列性质的二叉树：

　　1）若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；

　　2）若任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；

　　3）任意节点的左、右子树也分别为二叉查找树。

　　**二叉查找树性质**：**对二叉查找树进行中序遍历，即可得到有序的数列。**

**复杂度分析：它和二分查找一样，插入和查找的时间复杂度均为O(logn)，但是在最坏的情况下仍然会有O(n)的时间复杂度。原因在于插入和删除元素的时候，树没有保持平衡（比如，我们查找上图（b）中的“93”，我们需要进行n次查找操作）。我们追求的是在最坏的情况下仍然有较好的时间复杂度，这就是平衡查找树设计的初衷。**

- **平衡查找树之2-3查找树（2-3 Tree）**

**2-3查找树定义**：和二叉树不一样，2-3树运行每个节点保存1个或者两个的值。对于普通的2节点(2-node)，他保存1个key和左右两个自己点。对应3节点(3-node)，保存两个Key，2-3查找树的定义如下：

　　1）要么为空，要么：

　　2）对于2节点，该节点保存一个key及对应value，以及两个指向左右节点的节点，左节点也是一个2-3节点，所有的值都比key要小，右节点也是一个2-3节点，所有的值比key要大。

　　3）对于3节点，该节点保存两个key及对应value，以及三个指向左中右的节点。左节点也是一个2-3节点，所有的值均比两个key中的最小的key还要小；中间节点也是一个2-3节点，中间节点的key值在两个跟节点key值之间；右节点也是一个2-3节点，节点的所有key值比两个key中的最大的key还要大。

**2-3查找树的性质：**

　　**1）如果中序遍历2-3查找树，就可以得到排好序的序列；**

　　**2）在一个完全平衡的2-3查找树中，根节点到每一个为空节点的距离都相同。（这也是平衡树中“平衡”一词的概念，根节点到叶节点的最长距离对应于查找算法的最坏情况，而平衡树中根节点到叶节点的距离都一样，最坏情况也具有对数复杂度。）**

**复杂度分析：**2-3树的查找效率与树的高度是息息相关的。

在最坏的情况下，也就是所有的节点都是2-node节点，查找效率为lgN

在最好的情况下，所有的节点都是3-node节点，查找效率为log3N约等于0.631lgN

- **平衡查找树之红黑树（Red-Black Tree）**

2-3查找树能保证在插入元素之后能保持树的平衡状态，最坏情况下即所有的子节点都是2-node，树的高度为lgn，从而保证了最坏情况下的时间复杂度。但是2-3树实现起来比较复杂，于是就有了一种简单实现2-3树的数据结构，即红黑树（Red-Black Tree）。

　　**基本思想：**红黑树的思想就是对2-3查找树进行编码，尤其是对2-3查找树中的3-nodes节点添加额外的信息。红黑树中将节点之间的链接分为两种不同类型，红色链接，他用来链接两个2-nodes节点来表示一个3-nodes节点。黑色链接用来链接普通的2-3节点。特别的，使用红色链接的两个2-nodes来表示一个3-nodes节点，并且向左倾斜，即一个2-node是另一个2-node的左子节点。这种做法的好处是查找的时候不用做任何修改，和普通的二叉查找树相同。

**复杂度分析：最坏的情况就是，红黑树中除了最左侧路径全部是由3-node节点组成，即红黑相间的路径长度是全黑路径长度的2倍。**

- **B树和B+树（B Tree/B+ Tree）**

**B和B+树的区别在于，B+树的非叶子结点只包含导航信息，不包含实际的值，所有的叶子结点和相连的节点使用链表相连，便于区间查找和遍历。**

　　B+ 树的优点在于：

- 由于B+树在内部节点上不包含数据信息，因此在内存页中能够存放更多的key。 数据存放的更加紧密，具有更好的空间局部性。因此访问叶子几点上关联的数据也具有更好的缓存命中率。
- B+树的叶子结点都是相链的，因此对整棵树的遍历只需要一次线性遍历叶子结点即可。而且由于数据顺序排列并且相连，所以便于区间查找和搜索。而B树则需要进行每一层的递归遍历。相邻的元素可能在内存中不相邻，所以缓存命中性没有B+树好。

　　**但是B树也有优点，其优点在于，由于B树的每一个节点都包含key和value，因此经常访问的元素可能离根节点更近，因此访问也更迅速。**

B/B+树常用于文件系统和数据库系统中，它通过对每个节点存储个数的扩展，使得对连续的数据能够进行较快的定位和访问，能够有效减少查找时间，提高存储的空间局部性从而减少IO操作。它广泛用于文件系统及数据库中，如：

Windows：HPFS文件系统；

Mac：HFS，HFS+文件系统；

Linux：ResiserFS，XFS，Ext3FS，JFS文件系统；

数据库：ORACLE，MYSQL，SQLSERVER等中。

- **树表查找总结：**

  二叉查找树平均查找性能不错，为O(logn)，但是最坏情况会退化为O(n)。在二叉查找树的基础上进行优化，我们可以使用平衡查找树。平衡查找树中的2-3查找树，这种数据结构在插入之后能够进行自平衡操作，从而保证了树的高度在一定的范围内进而能够保证最坏情况下的时间复杂度。但是2-3查找树实现起来比较困难，红黑树是2-3树的一种简单高效的实现，他巧妙地使用颜色标记来替代2-3树中比较难处理的3-node节点问题。红黑树是一种比较高效的平衡查找树，应用非常广泛，很多编程语言的内部实现都或多或少的采用了红黑树。除此之外，2-3查找树的另一个扩展——B/B+平衡树，在文件系统和数据库系统中有着广泛的应用。

**(6) 分块查找**

分块查找又称索引顺序查找，它是顺序查找的一种改进方法。
　　**算法思想：**将n个数据元素"按块有序"划分为m块（m ≤ n）。每一块中的结点不必有序，但块与块之间必须"按块有序"；即第1块中任一元素的关键字都必须小于第2块中任一元素的关键字；而第2块中任一元素又都必须小于第3块中的任一元素，……
　　**算法流程：**
　　step1 先选取各块中的最大关键字构成一个索引表；
　　step2 查找分两个部分：先对索引表进行二分查找或顺序查找，以确定待查记录在哪一块中；然后，在已确定的块中用顺序法进行查找。

**(7) 哈希查找。**

**什么是哈希表（Hash）？**

　　我们使用一个下标范围比较大的数组来存储元素。可以设计一个函数（哈希函数， 也叫做散列函数），使得每个元素的关键字都与一个函数值（即数组下标）相对应，于是用这个数组单元来存储这个元素；也可以简单的理解为，按照关键字为每一个元素"分类"，然后将这个元素存储在相应"类"所对应的地方。但是，不能够保证每个元素的关键字与函数值是一一对应的，因此极有可能出现对于不同的元素，却计算出了相同的函数值，这样就产生了"冲突"，换句话说，就是把不同的元素分在了相同的"类"之中。后面我们将看到一种解决"冲突"的简便做法。

　　**总的来说，"直接定址"与"解决冲突"是哈希表的两大特点。**

　　**什么是哈希函数？**

　　哈希函数的规则是：通过某种转换关系，使关键字适度的分散到指定大小的的顺序结构中，越分散，则以后查找的时间复杂度越小，空间复杂度越高。

　　**算法思想：**哈希的思路很简单，如果所有的键都是整数，那么就可以使用一个简单的无序数组来实现：将键作为索引，值即为其对应的值，这样就可以快速访问任意键的值。这是对于简单的键的情况，我们将其扩展到可以处理更加复杂的类型的键。

　　**算法流程：**

　　1）用给定的哈希函数构造哈希表；

　　2）根据选择的冲突处理方法解决地址冲突；

　　　  常见的解决冲突的方法：拉链法和线性探测法。

　　3）在哈希表的基础上执行哈希查找。

　　**哈希表是一个在时间和空间上做出权衡的经典例子。如果没有内存限制，那么可以直接将键作为数组的索引。那么所有的查找时间复杂度为O(1)；如果没有时间限制，那么我们可以使用无序数组并进行顺序查找，这样只需要很少的内存。哈希表使用了适度的时间和空间来在这两个极端之间找到了平衡。只需要调整哈希函数算法即可在时间和空间上做出取舍。**

　　**复杂度分析**：

　　单纯论查找复杂度：对于无冲突的Hash表而言，查找复杂度为O(1)（注意，在查找之前我们需要构建相应的Hash表）。

**使用Hash，我们付出了什么？**
　　我们在实际编程中存储一个大规模的数据，最先想到的存储结构可能就是map，也就是我们常说的KV pair，经常使用Python的博友可能更有这种体会。使用map的好处就是，我们在后续处理数据处理时，可以根据数据的key快速的查找到对应的value值。map的本质就是Hash表，那我们在获取了超高查找效率的基础上，我们付出了什么？

　　Hash是一种典型**以空间换时间**的算法，比如原来一个长度为100的数组，对其查找，只需要遍历且匹配相应记录即可，从空间复杂度上来看，假如数组存储的是byte类型数据，那么该数组占用100byte空间。现在我们采用Hash算法，我们前面说的Hash必须有一个规则，约束键与存储位置的关系，那么就需要一个固定长度的hash表，此时，仍然是100byte的数组，假设我们需要的100byte用来记录键与位置的关系，那么总的空间为200byte,而且用于记录规则的表大小会根据规则，大小可能是不定的。

#### 7 排序

常见排序算法：

![img](https://upload-images.jianshu.io/upload_images/1156494-ab4cecff133d87b3.png)

常用排序算法时空复杂度及稳定性：

| 排序算法 | 时间复杂度平均情况 | 时间复杂度最好情况 | 时间复杂度最坏情况 | 辅助空间       | 稳定性 |
| -------- | ------------------ | ------------------ | ------------------ | -------------- | ------ |
| 冒泡排序 | O(n^2)             | O(n)               | O(n^2)             | O(1)           | 稳定   |
| 选择排序 | O(n^2)             | O(n^2)             | O(n^2)             | O(1)           | 不稳定 |
| 插入排序 | O(n^2)             | O(n)               | O(n^2)             | O(1)           | 稳定   |
| 希尔排序 | O(n^2)~O(n*log(n)) | O(n)               | O(n^2)             | O(1)           | 不稳定 |
| 堆排序   | O(n*log(n))        | O(n*log(n))        | O(n*log(n))        | O(1)           | 不稳定 |
| 归并排序 | O(n*log(n))        | O(n*log(n))        | O(n*log(n))        | O(n)           | 稳定   |
| 快速排序 | O(n*log(n))        | O(n*log(n))        | O(n^2)             | O(log(n))~O(n) | 不稳定 |
| 基数排序 | O(d(r+n))          | O(d(rd+n))         | O(d(r+n))          | O(d(rd+n))     | 稳定   |

**比较次数**：除了堆排序算法的比较次数是O(nlog2 n)，其他的都是n(n-1)/2

**(1) 冒泡排序：**

     ![img](https://upload-images.jianshu.io/upload_images/1156494-fef2b2e3edc03289.gif)

 线性表的冒泡排序采用双层循环迭代的方式，排序方式由大到小，内循环每次冒出一个最大数到待排序数的表头，外循环控制当前待排序数表的长度。这个过程像是水中的气泡冒出的过程，小的气泡在下向上冒出的过程中慢慢变大最后大的气泡冒出水面。

算法过程：（由大到小排序，从前往后遍历）

1. 每次遍历前后两个数，遇到前一个数小于后一个数交换两个数的位置。
2. 循环一次结束，下次循环的长度减1。
3. 直到遍历完整个数组。

**改进的冒泡排序：**

       对冒泡的过程进行排序（由大到小排序），在进行表的遍历的过程，采用来回遍历的方式，从左往右遍历的过程中冒出最小值到表尾部，右端标记向左滑动一位，再从右往左遍历的过程中冒出最大值到表头，左端的标记向右滑动一位。直到最后左端的标记等于右端的标记结束。

算法过程：

1. 从左端往右端遍历线性表，对比前后数据，当左边数据比右边小时调换两个数据，直到右端标记遍历结束，右端标记向左移动一位。
2. 再从右端标记向左端标记遍历，对比前后数据，当左边数据比右边小时调换两个数据，直到左端标记遍历结束，左端标记向右移动一位。
3. 当左端标记等于右端标记时，排序结束。

**(2) 选择排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-25821a7cb5aec881.gif)       

数据排列从大到小的选择排序，线性表选择排序的基本思想是：从一堆数据中选择出一个最大的数和表头的数据进行调换，然后再在剩下的数中选择次大的数和从表头开始的第二个数进行调换，依此向下，直到遍历完整个表。

算法过程：

1. 循环遍历数据从中找到最大的数据和当前表头位置的数进行调换。
2. 调换完成后，表头标记为已排序完数的下一个数。
3. 直到表中所有的数据有序。

**(3) 插入排序：**

       ![img](https://upload-images.jianshu.io/upload_images/1156494-936d9f02b6aac880.gif)

直接插入排序的核心思想就是：将数组中的所有元素依次跟前面已经排好的元素相比较，如果选择的元素比已排序的元素小，则交换，直到全部元素都比较过。
因此，从上面的描述中我们可以发现，直接插入排序可以用两个循环完成：

1. 第一层循环：遍历待比较的所有数组元素
2. 第二层循环：将本轮选择的元素(selected)与已经排好序的元素(ordered)相比较。
   如果：selected > ordered，那么将二者交换  

线性表的插入排序，（从大到小）插入排序的基本思路是：从一个数开始，将其看作是有序，取下一个数，如果次数比第一个数小则将次数插在第一个数的后面，反之，将第一个数往后挪一位，将次数插在第一个数前面，这样构成一个包含两个数的有序列。接下来取出第三个数，并遍历有序列，找到合适的插入位置，将插入位置之后的数整体往后挪一位。这样取数插入，直到整个表中的数据被全部取完。

算法过程：

1. 取数的过程从第二个数开始。
2. 找到合适的位置，将位置后排好序的数依此向后移动一个位置。
3. 直到，表中的数据全部取出。

**(4) 希尔排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-80700e24aed3d83e.png)       

希尔排序的算法思想：将待排序数组按照步长gap进行分组，然后将每组的元素利用直接插入排序的方法进行排序；每次将gap折半减小，循环上述操作；当gap=1时，利用直接插入，完成排序。
同样的：从上面的描述中我们可以发现：希尔排序的总体实现应该由三个循环完成：

1. 第一层循环：将gap依次折半，对序列进行分组，直到gap=1
2. 第二、三层循环：也即直接插入排序所需要的两次循环。具体描述见上。

线性表做希尔排序，（由大到小）希尔排序是渐变步长的插入排序，一开始步长较大可以在初排序的过程中保证序列相对有序，再依此缩短步长，下次排序只需要做出局部调整，当步长变成1时再略微调整，排序就结束了。

算法过程：

1. 选择步长，进行插入排序。
2. 缩短步长进行插入排序。

**(5) 堆排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-596eee6397817ca2.png)       

堆排序是利用二叉树的概率构造大顶堆和小顶堆，大顶堆中每一个子树其根节点的值总是大于或等于左右子节点，小顶堆，则相反，根节点的值都小于等于左右子节点。但在对线性表做堆排序时，并不需要构建堆，也就是不需要构建二叉树。秩序要应用一下规则：

//下标为i的节点其做左叶子节点的下标为2i + 1,其右叶子节点下标为2i + 2
//大顶堆：a[i] >= a[2 * i + 1] && a[i] >= a[2 * i + 2];

//小顶堆：a[i] <= a[2 * i + 1] && a[i] <= a[2 * i + 2];

因此每次对序列进行一次大顶堆或小顶堆的调整，就可以得到一个最大数或者是最小数，并将次数从堆中分隔出放置线性表结尾，再对余下数进行调整，直到所有数都被调整为有序。

**(6) 归并排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-0597aa6877e219f0.gif)      

 归并排序的思想，类似于刚学数据结构时总会做到的一道数据结构题：将两个有序序列合并为一个有序序列。因此对于一个无序的序列做归并排序，其过程很容易结合递归操作进行。在递归深入的过程中将一串无需的序列划分为一个个单独的数，单独的数当作是有序的，在递归回溯的过程中将这些单独的数一对一对合并成序列，最终合并成一个大的有序的序列。

**(7) 快速排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-2d150e5550b700fa.gif)       

快速排序的思想是，每次从无序的序列中找出一个基数，对序列做划分，大于基数的数放一边，小于基数的数放另一边。下一次，再分别对基数两边无序的数，从中再寻找基数做划分，这样一直划分下去，直到选取基数后其两边都没有数，快速排序结束。

       由于其空间复杂度是O(1)，需要一个单位的辅助空间用来保存基数的值，所以开始遍历对比的方向是序列中相对于基数的另一头，例如：如果从左边开始取基数，那么开始比较的时候取的数一定是从序列的右边开始，这样进行交换。

       一次选取基数排序的过程结束的标志是左边的位置标记等于右边位置标记的值。如果是从小往大排序，比基数小的放在左边，比基数大的放在右边。

**(8) 基数排序：**

![img](https://upload-images.jianshu.io/upload_images/1156494-70872a75238d1269.gif)



基数排序：通过序列中各个元素的值，对排序的N个元素进行若干趟的“分配”与“收集”来实现排序。
      分配：我们将L[i]中的元素取出，首先确定其个位上的数字，根据该数字分配到与之序号相同的桶中；
      收集：当序列中所有的元素都分配到对应的桶中，再按照顺序依次将桶中的元素收集形成新的一个待排序列L[ ]
对新形成的序列L[]重复执行分配和收集元素中的十位、百位...直到分配完该序列中的最高位，则排序结束；



## 六、分布式与微服务

#### 1. CAP理论、BASE理论

CAP:

C(一致性 Consistency)，所有节点上的数据时刻保持一致

A(可用性 Avaliability)，每个请求都能够收到一个响应，无论响应成功或者失败

P(分区容错 Partition-tolerance)，系统出现脑裂以后，可能导致某些server 与集群中的机器失去联系

BASE：

XA事务虽然可以保证数据库在分布式系统下的ACID特性，但会带来性能方面的影响

eBay提出了BASE理论

Basically available：数据库采用分片模式，把100w的用户数据分布在5个实例上，如果破坏了其中一个实例，仍然可以保证80%的用户可用

Soft-state：在基于client-server模式的系统中，server端是否有状态，决定了系统是否具备良好的水平扩展、负载均衡、故障恢复等特性。Server端承诺会维护client端状态数据，这个状态仅维持一小段时间，这段时间以后，server端会丢弃这个状态，恢复正常状态

Eventually consistent：数据最终一致性

#### 2. 微服务与SOA的区别

SOA即面向服务架构，关注点是服务，现有的分布式服务化技术有Dubbo等

1. 微服务是一种经过改良架构设计的SOA解决方案，是面向服务的交互方案
2. 微服务更趋向于以自治的方式产生价值
3. 微服务与敏捷开发的思想高度结合在一起，服务的定义更加清晰，同时减少了企业ESB开发的复杂性
4. 微服务是SOA思想的一种提炼
5. SOA是重ESB,微服务是轻网关

#### 3. 分布式一致性方案

1. 两阶段提交

   分准备阶段、提交阶段，由事务管理协调器发起

   准备阶段：事务管理器向参与者发起指令，参与者评估自己的状态，如果参与者评估指令可以完成，则会写redo或者undo日志，然后锁定资源，执行操作，但并不提交。如果其中一个参与者返回准备准备失败，则协调者向参与者发起中止指令，参与者取消已经变更的事务，执行undo日志，释放锁定的资源

   提交阶段：如果每个参与者明确返回准备成功，也就是预留资源和执行操作成功，则协调者向参与者发起提交指令，参与者提交资源变更的事务，释放锁定的资源；

   缺点：

   阻塞，对于任何一次指令都必须收到明确的响应，才会继续下一步，否则处于阻塞状态，占用的资源被一直锁定，不会释放

   单点故障，协调者宕机，参与者没有协调者指挥，会一直阻塞，需要自己实现协调者选举

   脑裂，协调者发送指令，有的参与者可能会没有接收到指令，导致多个参与者事务状态不一致

2. 三阶段提交

   是二阶段提交的改进版本，通过超时机制解决了阻塞问题

   询问阶段：协调者询问参与者是否可以完成指令，协调者回复是或者不是，不做真正的操作，如果超时会导致中止

   准备阶段、提交阶段：与二阶段相同

3. TCC补偿事务

   将一个任务拆分成Try、Confirm、Cancle三个步骤，主业务先发起请求执行Try，如果没有问题，则提交任务到TCC事务管理器，由事务管理器执行Confirm，如果出现问题，再执行逆操作Cancel

   优点：解决了阻塞问题，通过TCC自动化Cancel降低了不一致的情况

   缺点：实现还是臃肿，在极端情况下会出现不一致和脑裂问题

4. RocketMQ事务

   系统A发送一个事务消息到MQ，MQ会反馈消息接收成功，系统A会收到消息接收成功回调，此时系统A执行本地事务，执行成功后向MQ发送确认消息，否则向MQ取消消息，MQ收到确认消息后，消费系统B就能够接收到该事务消息，执行操作


## 七、操作系统

### 1. windows

**(1) 64位和32位的区别？**

操作系统只是硬件和应用软件中间的一个平台。32位操作系统针对的32位的CPU设计。64位操作系统针对的64位的CPU设计。

* 运行能力不同。64位可以一次性可以处理8个字节的数据量，而32位一次性只可以处理4个字节的数据量，因此64位比32位的运行能力提高了一倍。
* 内存寻址不同。64位最大寻址空间为2的64次方，理论值直接达到了16TB，而32位的最大寻址空间为2的32次方，为4GB，换而言之，就是说32位系统的处理器最大只支持到4G内存，而64位系统最大支持的内存高达亿位数。  
* 运行软件不同。由于32位和64位CPU的指令集是不同的。所以需要区分32位和64位版本的软件。
  为了保证兼容性，64位CPU上也能运行老的32位指令。于是实际上我们可以在64位CPU上运行32位程序，但是反过来不行。简而言之就是64位的操作系统可以兼容运行32位的软件，反过来32位系统不可以运行64位的软件。

**(2) 你怎么理解操作系统里的内存碎片，有什么解决办法？**

内存碎片分为：内部碎片和外部碎片。

内部碎片就是已经被分配出去（能明确指出属于哪个进程）却不能被利用的内存空间；

内部碎片是处于区域内部或页面内部的存储块。占有这些区域或页面的进程并不使用这个存储块。而在进程占有这块存储块时，系统无法利用它。直到进程释放它，或进程结束时，系统才有可能利用这个存储块。

单道连续分配只有内部碎片。多道固定连续分配既有内部碎片，又有外部碎片。

外部碎片指的是还没有被分配出去（不属于任何进程），但由于太小了无法分配给申请内存空间的新进程的内存空闲区域。

外部碎片是出于任何已分配区域或页面外部的空闲存储块。这些存储块的总和可以满足当前申请的长度要求，但是由于它们的地址不连续或其他原因，使得系统无法满足当前申请。

使用伙伴系统算法。

**(3) 介绍一下，什么是页式存储？**

主存被等分成大小相等的片，称为主存块，又称为实页。

当一个用户程序装入内存时，以页面为单位进行分配。页面的大小是为2n ,通常为1KB、2KB、2n KB等

（2n是2的n次方）

### 2. Linux

**(1) CentOS 和 Linux的关系？**

CentOS是Linux众多得发行版本之一，linux有三大发行版本（：Slackware、debian、redhat）,而Redhat有收费的商业版和免费的开源版,商业版的业内称之为RHEL系列，CentOS是来自于依照开放源代码规定而公布的源代码重新编译而成。可以用CentOS替代商业版的RHEL使用。两者的不同，CentOS不包含封闭源代码软件，是免费的。

**(2) 请解释一下，LINUX下的线程，GDI类**

LINUX实现的就是基于核心轻量级进程的”一对一”线程模型，一个线程实体对应一个核心轻量级进程，而线程之间的管理在核外函数库中实现。

GDI类为图像设备编程接口类库。

**(3) 谈一谈，系统线程数量上限是多少？**

Linux 系统中单个进程的最大线程数有其最大的限制 PTHREAD_THREADS_MAX。

这个限制可以在/usr/include/bits/local_lim.h中查看 ，对 linuxthreads 这个值一般是 1024，对于 nptl 则没有硬性的限制，仅仅受限于系统的资源。

这个系统的资源主要就是线程的 stack 所占用的内存，用 ulimit -s 可以查看默认的线程栈大小，一般情况下，这个值是8M=8192KB。

**(4) 讲一讲，线程与进程的区别**

进程和线程的主要差别在于它们是不同的操作系统资源管理方式。进程有独立的地址空间，一个进程崩溃后，在保护模式下不会对其它进程产生影响，而线程只是一个进程中的不同执行路径。线程有自己的堆栈和局部变量，但线程之间没有单独的地址空间，一个线程死掉就等于整个进程死掉，所以多进程的程序要比多线程的程序健壮，但在进程切换时，耗费资源较大，效率要差一些。但对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。

1) 简而言之,一个程序至少有一个进程,一个进程至少有一个线程.

2) 线程的划分尺度小于进程，使得多线程程序的并发性高。

3) 另外，进程在执行过程中拥有独立的内存单元，而多个线程共享内存，从而极大地提高了程序的运行效率。

4) 线程在执行过程中与进程还是有区别的。每个独立的线程有一个程序运行的入口、顺序执行序列和程序的出口。但是线程不能够独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。

5) 从逻辑角度来看，多线程的意义在于一个应用程序中，有多个执行部分可以同时执行。但操作系统并没有将多个线程看做多个独立的应用，来实现进程的调度和管理以及资源分配。这就是进程和线程的重要区别。

**(5) 请问，如何杀死一个进程？**

* kill pid；系统发送一个signal,程序收到信号后，会先释放资源，再关闭程序。
* kill -9 pid；-9表示强制执行。

### 3. 处理调度与死锁

**(1) 系统如何提高并发性**

* 提高CPU并发计算能力

​      1）多进程&多线程

​      2）减少进程切换，使用线程，考虑进程绑定CPU

​      3）减少使用不必要的锁，考虑无锁编程

​      4）考虑进程优先级

​      5）关注系统负载

* 改进I/O模型

​      1) DMA技术

​      2) 异步I/O

​      3) 改进多路I/O就绪通知策略，epoll

​     4) Sendfile

​     5) 内存映射

​     6) 直接I/O

**(2) 系统CPU比较高的原因**

* 首先查看是哪些进程的CPU占用率最高（如下可以看到详细的路径）

​     ps -aux --sort -pcpu | more

​    定位有问题的线程可以用如下命令

​    ps -mp pid -o THREAD,tid,time | more

* 查看JAVA进程的每个线程的CPU占用率

​    ps -Lp 5798 cu | more        # 5798是查出来进程PID

* 追踪线程，查看负载过高的原因，使用JDK下的一个工具

​    jstack 5798                        # 5798是PID

​    jstack -J-d64 -m 5798       # -j-d64指定64为系统

​    jstack 查出来的线程ID是16进制，可以把输出追加到文件，导出用记事本打开，再根据系统中的线程ID去搜索 查看该ID的线程运行内容，可以和开发一起排查。

**(3) 请谈一谈，什么情况下会发生死锁？解决死锁的策略有哪些？**

* 互斥条件：一个资源一次只能被一个进程访问。即某个资源在一段时间内只能由一个进程占有，不能同时被两个或两个以上的进程占 有。这种独占资源如CD-ROM驱动器，打印机等等，必须在占有该资源的进程主动释放它之后，其它进程才能占有该资源。这是由资源本身的属性所决定的。
* 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放。进程至少已经占有一个资源，但又申请新的资源；由于该资源已被另外进程占有，此时该进程阻塞；但是，它在等待新资源之时，仍继续占用已占有的资源。
* 不剥夺条件：进程已经获得的资源，在未使用完之前不能强行剥夺，而只能由该资源的占有者进程自行释放
* 循环等待条件：若干资源形成一种头尾相接的循环等待资源关系。

   解决方法：银行家算法

## 八、XML基础

### 1. XML

**问题 1： XML是什么**

XML 即可扩展标记语言（Extensible Markup language），你可以根据自己的需要扩展 XML。XML 中可以轻松定义<books>, <orders>等自定义标签，而在 HTML 等其他标记语言中必须使用预定义的标签，比如<p>，而不能使用用户定义的标签。使用 DTD 和 XML Schema 标准化XML 结构。XML 主要用于从一个系统到另一系统的数据传输，比如企级应用的客户端与服务端。

**问题 2 ：DTD 与 与 XML Schema  有什么区别？**
答：DTD 与 XML Schema 有以下区别：DTD 不使用 XML 编写而 XML Schema 本身就是 xml 文件，这意味着XML解析器等已有的XML工具可以用来处理XML Schema。而且XML Schema 是设计于 DTD 之后的，它提供了更多的类型来映射 xml 文件不同的数据类型。DTD 即文档类型描述(Document Type definition)是定义 XML 文件结构的传统方式。

**问题 3 ：XPath  是什么？**
答：XPath 是用于从 XML 文档检索元素的 XML 技术。XML 文档是结构化的，因此 XPath 可以从 XML 文件定位和检索元素、属性或值。从数据检索方面来说，XPath与 SQL 很相似，但是它有自己的语法和规则。了解更多查看怎样使用 XPath 从 XML 文档中检索数据

**问题 4 ：XSLT  是什么?**
答：XSLT 也是常用的 XML 技术，用于将一个 XML 文件转换为另一种 XML，HTML 或者其他
的格式。XSLT 为转换 XML 文件详细定义了自己的语法，函数和操作符。通常由 XSLT 引擎完成转换，XSLT 引擎读取 XSLT 语法编写的 XML 样式表或者 XSL 文件的指令。XSLT 大量使用递归来执行转换。一个常见 XSLT 使用就是将 XML 文件中的数据作为 HTML 页面显示。XSLT 也可以很方便地把一种 XML 文件转换为另一种 XML 文档

**问题 5 ：什么是 XML  元素和属性**
答：最好举个例子来解释。下面是简单的 XML 片断。
<Orders>
<Order id="123">
<Symbol>6758.T</Symbol>
<Price>2300</Price>
<Order>
<Orders>
例子中 id 是元素的一个属性，其他元素都没有属性。

**问题 6 ：什么是格式良好的 XML**
答：这个问题经常在电话面试中出现。一个格式良好的 XML 意味着该 XML 文档语法上是正确的，比如它有一个根元素，所有的开放标签合适地闭合，属性值必须加引号等等。如果一个 XML 不是格式良好的，那么它可能不能被各种 XML 解析器正确地处理和解析。

**问题 7 ：XML  命名空间是什么？它为什么很重要？**
答：XML 命名空间与 Java 的 package 类似，用来避免不同来源名称相同的标签发生冲突。XML 命名空间在 XML 文档顶部使用 xmlns 属性定义，语法为 xmlns:prefix=’URI’。prefix 与XML 文档中实际标签一起使用。下面例子为 XML 命名空间的使用。
<root xmlns:inst="http://instruments.com/inst"
<inst:phone>
<inst:number>837363223</inst:number>
</inst:phone>
</root>

**问题 8 ：DOM 和 和 SAX  解析器有什么区别**
答：这又是一道常见面试题，不仅出现在 XML 面试题中，在 Java 面试中也会问到。DOM 和SAX 解析器的主要区别在于它们解析 XML 文档的方式。使用 DOM 解析时，XML 文档以树形结构的形式加载到内存中，而 SAX 是事件驱动的解析器。这个问题更详细的回答查看 DOM和 SAX 解析器之间的区别。

**问题 9 ：XML CDATA  是什么**
答：这道题很简单也很重要，但很多编程人员对它的了解并不深。CDATA 是指字符数据，它有特殊的指令被 XML 解析器解析。XML 解析器解析 XML 文档中所有的文本，比如<name>Thisis name of person</name>，标签的值也会被解析，因为标签值也可能包含 XML 标签，比如<name><firstname>First Name</firstname></name>。CDATA 部分不会被 XML 解析器解析。CDATA 部分以<![CDATA[开始，以]]>结束。

**问题 10 ：Java 的 的 XML  数据绑定是什么**
答：Java 的 XML 绑定指从 XML 文件中创建类和对象，使用 Java 编程语言修改 XML 文档。XML绑定的 Java API，JAXB 提供了绑定 XML 文档和 Java 对象的便利方式。另一个可选的 XML 绑定方法是使用开源库，比如 XML Beans。Java 中 XML 绑定的一个最大的优势就是利用 Java编程能力创建和修改 XML 文档。以上的 XML 面试问答题收集自很多编程人员，但它们对于使用 XML 技术的每个人都是有用的。由于 XML 具有平台独立的特性，XPath，XSLT，XQuery 等 XML 技术越来越重要，XML广泛用于跨平台数据传输。尽管 XML 有冗余和文档体积大等缺点，但它在 web 服务以及带宽、速率作为次要考虑因素的系统间数据传输起很大作用。

**(1) XML 和 HTML 的区别**

XML 和 HTML 为不同的目的而设计：

- XML 被设计用来传输和存储数据，其焦点是数据的内容。
- HTML 被设计用来显示数据，其焦点是数据的外观。

HTML 旨在显示信息，而 XML 旨在传输信息。

**(2) 请介绍一下，XML文档定义的几种形式，它们之间有何本质区别？再说说，解析XML文档又有哪几种方式？**

a: 两种形式 dtd schema
b: 本质区别:schema本身是xml的，可以被XML解析器解析(这也是从DTD上发展schema的根本目的)
c:有DOM,SAX,STAX等
DOM:处理大型文件时其性能下降的非常厉害。这个问题是由DOM的树结构所造成的，这种结构占用的内存较多，而且DOM必须在解析文件之前把整个文档装入内存,适合对XML的随机访问
SAX:不现于DOM,SAX是事件驱动型的XML解析方式。它顺序读取XML文件，不需要一次全部装载整个文件。当遇到像文件开头，文档结束，或者标签开头与标签结束时，它会触发一个事件，用户通过在其回调事件中写入处理代码来处理XML文件，适合对XML的顺序访问
STAX:Streaming API for XML (StAX)
xml文档有两种定义方法：
dtd：数据类型定义（data type definition），用以描述XML文档的文档结构，是早期的XML文档定义形式。
schema：其本身是基于XML语言编写的，在类型和语法上的限定能力比dtd强，处理也比较方便，因为此正逐渐代替dtd成为新的模式定义语言。

### 2. Web Service

**(1) Java规范中和 与Web Service相关的 规范有哪些？**

Java规范中和Web Service相关的有三个：

- JAX-WS(JSR 224)：这个规范是早期的基于SOAP的Web Service规范JAX-RPC的替代版本，它并不提供向下兼容性，因为RPC样式的WSDL以及相关的API已经在Java EE5中被移除了。WS-MetaData是JAX-WS的依赖规范，提供了基于注解配置Web Service和SOAP消息的相关API。
- JAXM(JSR 67)：定义了发送和接收消息所需的API,相当于Web Service的服务器端。
- JAX-RS(JSR 311 & JSR 339 & JSR 370)：是Java针对REST（Representation State Transfer）架构风格制定的一套Web Service规范。REST是一种软件架构模式，是一种风格，它不像SOAP那样本身承载着一种消息协议， (两种风格的Web Service均采用了HTTP做传输协议，因为HTTP协议能穿越防火墙，Java的远程方法调用（RMI）等是重量级协议，通常不能穿越防火墙），因此可以将REST视为基于HTTP协议的软件架构。REST中最重要的两个概念是资源定位和资源操作，而HTTP协议恰好完整的提供了这两个点。HTTP协议中的URI可以完成资源定位，而GET、POST、OPTION、DELETE方法可以完成资源操作。因此REST完全依赖HTTP协议就可以完成Web Service，而不像SOAP协议那样只利用了HTTP的传输特性，定位和操作都是由SOAP协议自身完成的，也正是由于SOAP消息的存在使得基于SOAP的Web Service显得笨重而逐渐被淘汰。

**(2) 请你谈谈对SOAP、WSDL、UDDI的了解。**

- SOAP：简单对象访问协议（Simple Object Access Protocol），是Web Service中交换数据的一种协议规范。
- WSDL：Web服务描述语言（Web Service Description Language），它描述了Web服务的公共接口。这是一个基于XML的关于如何与Web服务通讯和使用的服务描述；也就是描述与目录中列出的Web服务进行交互时需要绑定的协议和信息格式。通常采用抽象语言描述该服务支持的操作和信息，使用的时候再将实际的网络协议和信息格式绑定给该服务。
- UDDI：统一描述、发现和集成（Universal Description, Discovery and Integration），它是一个基于XML的跨平台的描述规范，可以使世界范围内的企业在互联网上发布自己所提供的服务。简单的说，UDDI是访问各种WSDL的一个门面（可以参考设计模式中的门面模式）

**(3) WEB SERVICE名词解释，JSWDL开发包的介绍，JAXP、JAXM的解释。SOAP、UDDI,WSDL解释。**

Web ServiceWeb Service是基于网络的、分布式的模块化组件，它执行特定的任务，遵守具体的技术规范，这些规范使得WebService能与其他兼容的组件进行互操作。

JAXP(Java API for XML Parsing) 定义了在Java中使用DOM, SAX, XSLT的通用的接口。这样在你的程序中你只要使用这些通用的接口，当你需要改变具体的实现时候也不需要修改代码。

JAXM(Java API for XML Messaging) 是为SOAP通信提供访问方法和传输机制的API。

WSDL是一种 XML 格式，用于将网络服务描述为一组端点，这些端点对包含面向文档信息或面向过程信息的消息进行操作。这种格式首先对操作和消息进行抽象描述，然后将其绑定到具体的网络协议和消息格式上以定义端点。相关的具体端点即组合成为抽象端点（服务）。

SOAP即简单对象访问协议(Simple Object Access Protocol)，它是用于交换XML编码信息的轻量级协议。

UDDI 的目的是为电子商务建立标准；UDDI是一套基于Web的、分布式的、为Web Service提供的、信息注册中心的实现标准规范，同时也包含一组使企业能将自身提供的Web Service注册，以使别的企业能够发现的访问协议的实现标准。

soap是web service最关键的技术，是web service中数据和方法调传输的介质。WSDL（web service definition language）描述了web service的接口和功能。



## 九、Others

Access的数据库对象：
1、表：主要用于存储数据。

2、查询： 主要用于提取数据。

3、窗体： 用户与程序的交互。

4、报表： 主要用于展示数据。

5、页： 主要用于数据共享。

6、宏： 用于自动化完成。
