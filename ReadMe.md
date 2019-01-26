# c#学习简记

### 数据类型
> 目标:该项目主要是为了进一步的探索c#以及桌面应用程序的制作,如果有可能,为我的那个自由度很高的游戏开发做准备(因为不需要多好的界面,主要是复杂的逻辑控制和程序设计,为什么?有什么意义?没有,我知道c#,WPF已经基本上是凉透的状态,但这是我)
>
> 注意:主要针对我不会的内容进行简记
>
> 学习内容:主要刘铁锰视频,以及WPF学习视频,创建此存储库时,已经学习到了刘铁锰c#学习视频,操作符的第2个视频.之前笔记已记,将复制到此.之前的实践代码不再补.
>
> 学习要求:尽可能的跑一下实例,并且在此记一下笔记.

[数据类型]### 数据类型

- 运行时，堆存储类，栈存储方法。堆很大，栈几M.
- c#数据类型
  - 引用类型
    - 类
    - 接口
    - 委托
  - 值类型
    - 结构体
      - int
      - long
      - byte 1个字节,无符号
    - 枚举
  - 值类型在栈分配空间,引用类型在堆分配空间.
  - 在堆里声明数据效率低(垃圾收集机制),因此值类型在栈中声明.
  - 值类型变量和引用类型变量都存储在栈.值类型变量直接存储值的初始指针,而引用类型变量空间总是4个字节(32,内存的地址应该是32位的),这个空间存储了实际引用类型实例存储空间的初始指针.
  - 方法内的局部变量声明在栈,类内的变量(全局变量)声明在堆.
  - 类内的变量会自动初始化,而方法内的变量不会自动初始化.C语言会在方法内自动初始化,出现垃圾值,也就是会直接调用原有内存中没有清零的值,出现烫烫烫.
  - 装箱和拆箱
    - **将值类型隐式转换为引用类型是装箱**
    - **将引用类型显式转换为值类型是拆箱.**

### 方法

- 方法由函数发展而来。函数在类中定义为方法。方法永远只能在类内。
- 字段是成员变量，方法是成员函数。
- 静态方法
- 构造器 ctor tab tab
- 重载方法 参数三个种类

- 操作符
  - 操作符本质是函数的简记法
  - 操作符不能脱离它相关的数据类型
  - 操作符重载
  - Type类型和typeof操作符
  - default操作符
  - 枚举类型显式赋值，可以赋值字符串等

### 操作符

- new
  - 匿名类型
    - var person = new { Name = "Tom" };
    - Console.WriteLine(person.GetType().Name);
  - 初始化器
  - new功能强大,但不能滥用,在一个类中声明其他类的实例会造成**紧耦合**,**依赖注入**解决这个问题
- checked
  - 数值越界的时候默认不会报错
  - 加了checked后可以报错
  - check{}或者()  语句序列或者语句
- delegate 
  - 作为操作符已经弃用,使用lambda代替
- sizeof
  - 数据类型的字节数,只能用于结构体类型或者自定义的结构体类型(此时为不安全代码)
  - 不安全代码要使用unsafe括起来
- ->
  - 指针访问操作符,不安全代码
- ~
  - 二进制按位取反
- (T)x  类型转换
  - 隐式类型转换
    - 不丢失精度的转换
    - 子类向父类转换
    - 装箱
  - 显式类型转换
    - 有可能丢失精度 cast
    - 拆箱
    - Convert类
    - Parse ,比如double.Parse("4534"),用于将字符串解析为数值,**要求格式正确** tryParse
    - 显式类型转换背后的秘密,非继承类之间的转换
- await
  - 异步操作,太深入,视频暂时不讲
- 算术运算符
  - 略
  - 类型提升
- 位移操作符
  - 数据在内存中的二进制的数据左移动或者右移动
- 关系操作符
  - 比较数值或者字符或者字符串
  - is as 类型检验操作符
    - 比较时,**只要是派生而来的就可以**,比如儿子的类型也是父亲的类型
    - is检测是否是相同类型后返回真假(是不是)
    - as直接返回转换后的值,不能转换返回null(作为)
- 位操作符
- 条件操作符
  - 短路效应
- ?,Nullable<T>,??
- ?:
- 赋值操作符
  - +=./=,%=,-=,<<=,>>=,*=
  - 从右往左结合
