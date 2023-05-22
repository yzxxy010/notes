# 构成

---

[toc]

___

## 0.结构及规范

### 0.命名规范

1. 只能使用字母，数字，下划线进行命名，并且不能用数字开头

2. 变量命名规范

  1. 驼峰命名法  

  	> 首个单词的首字母小写其余单词首字母大写  
  	>
  	> 例如：`maxValue` `value threeEgg`

3. 常量命名规范

	1. 常量名全字母大写 

		> 例如: `PI` `PRICE` `EGG` 
	


4. 函数命名规范  

	1. 每个单词首字母大写  

		> 例如: `Main` `Max` `MaxValue`  


### 1.相关词汇

1. 循环体  

  > 循环语句中大括号内的代码称之为循环体

2. 函数体

  > 在代码中，函数后花括号包括其内代码，称之为函数体

3. 多态

	> 多态是同一个行为具有多个不同表现形式或形态的能力。
	>
	> **多态性**意味着有多重形式。在面向对象编程范式中，多态性往往表现为"一个接口，多个功能"。
	>
	> 多态性可以是静态的或动态的。在**静态多态性**中，函数的响应是在编译时发生的。在**动态多态性**中，函数的响应是在运行时发生的。

### 2.命名空间

命名空间就像一个文件夹，这个文件夹包含类，类中包含方法

1. 定义命名空间

	> 命名空间的定义是以关键字`namespace`开始，后跟命名空间的名称
	>
	> ```c#
	> namespace namespace_name
	> {
	>    // 代码声明
	> }
	> ```

2. 嵌套命名空间

	> 命名空间可以被嵌套，可以在一个命名空间内定义另一个命名空间
	>
	> ```c#
	> namespace namespace_name1 
	> {
	>    // 代码声明
	>    namespace namespace_name2 
	>    {
	>      // 代码声明
	>    }
	> }
	> ```

3. 引用其他命名空间  

	1. 当前类引用

		> ```c#
		> //Console这个类就是属于System的，所以当我们需要使用Console的时候需要引入System
		> 
		> using System;
		> //引入方式 using namespace_name
		> namespace namespace_name
		> {
		>    // 代码声明
		> }
		> 
		> //如果需要引用命名空间内的另一个命名空间
		> //应该先引用主命名空间然后用.连接子命名空间
		> using namespace_name1.namespace_name2;
		> ```

	2. 直接引用

		> ```c#
		> //当我们不需要频繁调用某个类时，可以在使用类时引用命名空间
		> namespace mynamespace1
		> {
		>     class Program
		>     {
		>         static void Main(string[] args)
		>         {
		>             System.Console.WriteLine("ABC");
		>             //在Console类前加上对应命名空间可以直接引用一次
		>         }
		>     }
		> }
		> //如果需要引用命名空间内的另一个命名空间
		> //应该先引用主命名空间然后用.连接子命名空间
		> using e1.namespace_name2.class_name;
		> ```



## 1.数据类型

### 1.数据

变量的作用域

> ```c#
> if（true）{
> 	int a = 3;
>     Console.Write(a);
> 	if（false）{
> 		int c = 4;
>         Console.Write(a+c);
> 	}
> }
> ```
>
> 子作用域可以使用父作用域内的变量，而父作用域无法使用子作用域的变量。
>
> 所以上述代码中,`if(true)`中只能`Console.Write(a);`而无法访问`int c`

### 2.数据类型

1. 值类型

	- 整型

		> - `sbyte` 代表有符号8位整数 范围-128 ～ 127
		> - `byte`  无符号8位整数 范围0～ 255 short 有符号的16位整数 范围-32768 ～ 32767
		> - `ushort` 有符号的16位整数 范围0 ～ 65,535
		> - `int` 有符号32位整数 范围-2147483648~2147483647
		> - `uint` 无符号32位整数 范围0~4294967295
		> - `long` 有符号的64位整数 范围-9223372036854775808 ～9223372036854775808
		> - `ulong` 无符号的64位整数 范围0 ～18446744073709551615
		> - `char` 无符号的16位整数，数值范围从0～65535。 Char类型的可能值对应于统一字符编码标准(Unicode)的字符集；任意单个字符，用＇＇号框选

	- 浮点型

		> - `float` 32位 范围-3.402823E+38 ～3.402823E+38 小数位数精度为6位
		> - `double` 64位 范围-1.79769313486232E+308 ～1.79769313486232E+308 小数位数精度为15位

	- 特殊类型

		> - `decimal` 128位 范围-79228162514264337593543950335～79228162514264337593543950335

	- 布尔值

		> **布尔值**
		>
		> - `bool` 判断结果，值为`true(1)`和`false(0)`

2. 引用类型

	> 引用类型不包含存储在变量中的实际数据，但它们包含对变量的引用。 换句话说，它们指的是一个内存位置。使用多个变量时，引用类型可以指向一个内存位置。如果内存位置的数据是由一个变量改变的，其他变量会自动反映这种值的变化。**内置的引用类型有：`object`、`dynamic` 和 `string`**

3. 字符串类型

	> - `string` 字符串 字符串类型也是引用类型  
	> - 任意字符，用""号框选

4. 匿名类型

	> `var`类型是一个未定义类型
	>
	> 将什么类型的值赋值给`var`类型变量，那么此变量将转换成什么类型

5. 动态类型

	> `Dynamic` 您可以存储任何类型的值在动态数据类型变量中。这些变量的类型检查是在运行时发生的。
	>
	> 动态类型与对象类型相似，但是对象类型变量的类型检查是在编译时发生的，而动态类型变量的类型检查是在运行时发生的。

6. 对象类型

	> **对象（Object）类型** 是 C# 通用类型系统（Common Type System - CTS）中所有数据类型的终极基类。  
	>
	> `Object` 是 `System.Object` 类的别名。所以对象（Object）类型可以被分配任何其他类型（值类型、引用类型、预定义类型或用户自定义类型）的值。  
	>
	> 但是，在分配值之前，需要先进行类型转换。
	>
	> 当一个值类型转换为对象类型时，则被称为**装箱**,另一方面，当一个对象类型转换为值类型时，则被称为**拆箱**。
	>
	> ```c#
	> object obj;
	> obj = 100; // 这是装箱
	> ```

### 3.数据处理

#### 1.运算符

1. **计算运算符**

  > \+ 加
  >
  > \- 减
  >
  > \* 乘
  >
  > / 除
  >
  > % 除余

2. **自增自减运算符**

  > a++  先赋值在自增1
  > ++a 先自增1再赋值
  > a-- 先赋值再自减1
  > --a 先自减1再赋值

3. **赋值运算符**

  > = 赋值
  >+= 加且赋值（举例：a+=b相当于
  > a=a+b，以下同理）
  > -= 减且赋值
  > *= 乘且赋值
  > /= 除且赋值
  > %= 除余且赋值

4. **逻辑运算符(判断运算符)**

  >&& 与
  >1>0 && 2<8；//两边结果都是true则输出true
  >|| 或
  >1>0 || 9<8；两边结果其中一个是true，则输出结果是true
  >！非
  >!(1>0 && 2<8);括号内结果为true，经过非则变为false

5. **转义字符**

  > - \\   \符号
  > - \'    '符号
  > - \"  "符号
  > - \?  ?符号
  > - \a  Alert 或 bell
  > - \b  退格
  > - \f   换页
  > - \n 换行
  > - \r  回车
  > - \t  水平制表符tab
  > - \v  垂直制表符tab

#### 2.运算符重载

> 可以重定义或重载 C# 中内置的运算符。因此，程序员也可以使用用户自定义类型的运算符。重载运算符是具有特殊名称的函数，通过**operator** 后跟运算符的符号来定义的。
>
> ~~~c#
> public static 返回值类型 operator 要重载的运算符 (形参1,形参2)
> {
> 
> }
> //重载只在当前类，对当前类的实例化成员有效
> 
> //例子
> //以下代码为main方法
> ABC a=new ABC();
> ABC b=new ABC();
> a.qwq=3;
> b.qwq=5;
> Console.WriteLine(a+b);
> //最后结果为13
> //以下代码为ABC类
> public int qwq;
> public static int operator+(ABC a,ABC b)
> {
>     return a.qwq + b.qwq + b.qwq;
> }
> ~~~

#### 3.字符串处理

1. **字符串前加@**

  > [^字符串前加@]:字符串前加@表示强制不转译。
  >
  > 字符串前加@表示强制不转译。
  >
  > 如果你的字符串中有大量的\字符，而不是想用转义，那就写@来取消\转义字符。

2. **字符串本质**

  > 字符串本质上就是一个char数组（但是无法改变字符串的内容），所以也可以通过索引进行访问
  >
  > ```c#
  > string str = "abcd";
  > Console.WriteLine(str[2]);
  > //最后打印结果为c
  > ```

3. **字符串组拼**

  > 字符串加上一个值，那个值会归为字符串类型，而不会当成数值
  >
  > ```c#
  > string s = "字符串";
  > int a =3;
  > int b =4;
  > Console.Write(s+a+b);
  > //输出结果为 字符串34
  > //因为a,b是与字符串相加，会自动归类为字符串
  > ```
  >
  > 如果想用字符串加上两个值并让他们相加，应该用括号括起来两个值的运算，这样就会优先运算
  >
  > ```c#
  > string s = "字符串";
  > int a =3;
  > int b =4;
  > Console.Write(s+(a+b));
  > //输出结果为 字符串7
  > //因为ab相加用括号括起来了，所以会优先运算
  > ```

4. **字符串长度**

  > ```c#
  > string name="abc";
  > Console.WriteLine(name.length);
  > //name.length中name为字符串名字，length为属性
  > //name[2]中，[]中的2为索引，因为字符串可以看作为char的数值，所以可以采用数组索引进行单个字符读取
  > //但是只能读取不能对其改变
  > ```

5. **StringBuilder类**

  此类位于system.Text命名空间下

  1. **创建StringBuilder对象**

  	> ```c#
  	> StringBuilder sb = new StringBuilder ("www.taikr. com");//实例化一个对象，并追加内容
  	> StringBuilder sb = new StringBuilder (20);//实例化一个对象，容量为20
  	> StringBuilder sb = new StringBuilder ("www.devsiki.com",100);//创建一个对象，容量为100，并追加内容
  	> //容量不是最大容量，如果超出容量会自动扩容
  	> ```

  2. **StringBuilder类的方法**

  	> Append()方法，给当前字符串追加一个字符
  	>
  	> Insert()追加特定格式的字符串
  	>
  	> Remove()从当前字符串中删除字符
  	>
  	> Replace()在当前字符串中，用某个字符或者字符串全部替换另一个字符或者字符串
  	>
  	> ToString()把当前stringBuilder中存储的字符串，提取成一个不可变的字符串

6. **字符串属性及方法**

  | Length：获得当前字符串中字符的个数                           |
  | ------------------------------------------------------------ |
  | ToUpper():将字符转换成大写形式                               |
  | ToLower():将字符串转换成小写形式                             |
  | Equals(lessonTwo,StringComparison.OrdinalIgnoreCase):比较两个字符串，可以忽略大小写 |
  | Split()：分割字符串，返回字符串类型的数组。使用正则表达式表示拆分位置[正则表达式](note://WEB9d51db7285ee37fd1590e26a84ee61df) |
  | Substring()：截取字符串。在截取的时候包含要截取的那个位置。  |
  | IndexOf():判断某个字符串在字符串中第一次出现的位置，如果没有返回-1、值类型和引用类型在内存上存储的地方不一样。 |
  | LastIndexOf()：判断某个字符串在字符串中最后一次出现的位置，如果没有同样返回-1 |
  | StartsWith():判断以....开始                                  |
  | EndsWith():判断以...结束                                     |
  | Replace():将字符串中某个字符串替换成一个新的字符串           |
  | Contains():判断某个字符串是否包含指定的字符串                |
  | Trim():去掉字符串中前后的空格                                |
  | TrimEnd()：去掉字符串中结尾的空格                            |
  | TrimStart()：去掉字符串中前面的空格                          |
  | string.IsNullOrEmpty():判断一个字符串是否为空或者为null      |
  | string.Join()：将数组按照指定的字符串连接，返回一个字符串。  |

7. 字符串格式化

  > ```c#
  > //格式化
  > int a=10;
  > int b=55;
  > Console.WriteLine(string.Format("{0}{1}{0}",a,b));
  > //输出结果为105510
  > //格式化输出的同时，可以在{}内的索引后加上标识，来表示别的意思
  > //例如
  > int a=10;
  > Console.WriteLine(string.Format("{0:c}",a));
  > //输出结果为 ￥1.00
  > //:c就表示为货币
  > ```
  >
  > [字符串格式化更多表达](http://cnblogs.com/net-sky/p/10250880.html)



### 4.数据类型转换

1. 隐式转换

	> 两个类型，如果一个类型的范围小于另一个类型范围，则小的类型可以直接隐式转换为大的类型。
	>
	> ```c#
	> int a = 2;
	> long b = a;
	> //这种情况可直接转换，不会报错
	> ```

	

2. 显示转换

	> 如果一个范围大的类型，直接转化为小的类型，则会报错，这时候则可以在转换代码的范围小的类型前加上 (范围大的类型) 来进行强制转换。但是可能会因为类型的转换而舍弃一些值。
	>
	> ```c#
	> double a =1.26;
	> int b = a;
	> //这种情况会报错
	> double a =1.26;
	> 
	> int b = (int)a;
	> //这种情况不会报错，不过因为int值不存在小数，所以最后输出b的结果为1，小数点后的数将被舍弃
	> ```

	

3. Convert转换

	> `Convert`转换方式也可以将范围大的类型转换成小的类型，且字符串也可以通过Convert转换为数值
	>
	> ```c#
	> string a = "1976";
	> int b = Convert.Toint32(a);
	> //输出b的结果为1976
	> //Toint32可替换为别的类型，假设b不是int是char，则可以替换为Tochar
	> ```

	

4. 字符串类型转换

	- parse()

	  > `Parse()`可以将字符串转成任意类型
	  >
	  > ```c#
	  > string str="123";
	  > int num=int.Parse(str);
	  > ```
	
	- TryParse()
	
	  > `TryParse()`可以将字符串转成任意类型,并返回转成是否成功
	  >
	  > ```c#
	  > string str="123";
	  > int num=int.TryParse(str);//此时字符串内123可以转换为int类型则进行转换并返回true
	  > string str="abc";
	  > int num=int.TryParse(str);//此时字符串内abc无法转换为int类型则返回false
	  > ```
	
	  


5. as和is
	- as
	
		> as是将Object类转换为其他类
		>
		> 并且，转换失败（两类型无法转换）会返回null
		>
		> ```c#
		> Object o = "aaa";
		> string str = o as string;
		> //切记as不可用于值类型转换，例如
		> Object o = 123;
		> int value = o as int;
		> //这种为错误用法，应使用is加强制转换的方式
		> ```
	
	- is
	
		> is并不做真正的类型转换，只会在运行时进行一次转换，如果可以转换则返回true，否则返回folse
		>
		> ```c#
		> int a =999;
		> double b;
		> if(a is double){
		>    b=Convert.ToDouble(a); 
		> } 
		> ```
	
	Object => 已知引用类型——使用as操作符完成；
	
	Object => 已知值类型——先使用is操作符来进行判断，再用类型强转换方式进行转换；

### 5.自定义类型

#### 1.结构体

**注意：声明结构体类型不可以在方法或函数内，否则无法声明**

**结构体的实例化对象为值类型**

1. 结构体内定义变量

	> 定义方式
	>
	> ```c#
	> struct structname{
	>     public int num;
	>     private string str;
	> }
	> ```
	>
	> 调用方式
	>
	> ```c#
	> struct value{
	>     public int adc;
	>     public string qwer;
	> }//定义结构体
	> static void Main(string[] args){//Main主函数
	>     value xxx;//创建value类型变量xxx,value类型是通过定义结构体得到的
	>     xxx.adc=10086;//将value类型xxx变量内的adc进行赋值
	>     xxx.qwer="这是一个字符串";//将value类型xxx变量内的qwer进行赋值
	> }
	> ```

2. 结构体内定义函数

	> 定义方式
	>
	> ```c#
	> struct structname{
	>     public void temp{
	>         //函数体
	>     }
	> }
	> ```
	>
	> 使用方式
	>
	> ```c#
	> struct cwl{
	>     public void cw{
	>         Console.WriteLine("1");    
	>     }
	> }
	> static void Main(string[] args){
	>     cwl.cw();//调用函数
	> }
	> ```

	

#### 2.枚举类型

**注意：声明枚举类型不可以在方法或函数内，否则无法声明**

1. 枚举类型的声明

	> ```c#
	> enum ValueEnum{
	>     one,two,three,four
	> }
	> //枚举值可用中文命名
	> ```

2. 枚举类型的调用

	> ```c#
	> enum ValueEnum{
	>   one,two,three,four
	> }
	> static void Main(string[] args){
	>     ValueEnum a=ValueEnum.one;//调用枚举值
	> }
	> ```

3. 枚举值的对应值

	> 每个枚举类型都对应一个值，类似索引
	>
	> 并且后一个枚举值总比前一个默认大1
	>
	> ```c#
	> enum a{
	>     a,b,c,d,e,f,g
	> }
	> //a对应的就是0，b对应1…
	> ```
	>
	> 不过可以进行干涉进行改变
	>
	> ```c#
	> enum a{
	>     a,b=99,c,d,e,f=10086,g
	> }
	> //此时a对应0，b对应99，c对应100…e对应102，对应10086，g对应10087
	> ```

	

#### 2.委托类型

**注意：声明委托类型不可以在方法或函数内，否则无法声明**

1. 概念

  > 委托是一种存储函数引用的类型

2. **delegate委托**

  > **定义方式**
  >
  > 委托就像一个没有函数体的函数
  >
  > ```c#
  > delegate type name(param1,param2…paramn)
  > //type是返回值类型 name是委托名字 param是参数
  > ```
  >
  > **实际案例**
  >
  > ```c#
  > delegate int value(int a;int b)
  > ```
  >
  > **使用方式**
  >
  > 委托可以指向类型相同，参数列表相同的函数
  >
  > 类型相同：返回值类型相同
  >
  > 参数列表相同：所携带参数数量，类型都相同(参数的名字可以不同)
  >
  > ```c#
  > static int value(int a,int b){//声明一个函数
  >     num1=a;
  >     num2=b;
  >    Console.WriteLine(num1+num2);
  > }
  > delegate int abc(int qwe,int zxc);//定义一个委托
  > static void Main(string[] args){//main函数
  >     abc deve;//声明一个委托类型的变量
  >     deve=value;//声明变量指向的函数
  >     deve(2,3);//调用变量携带参数等同于调用函数
  > }
  > ```
  >
  > **委托类型数组**
  >
  > ```c#
  > //委托类型也可以作为一个数组的类型
  > //以下代码为QWQ类
  > public static int zxc(int temp)
  > {
  >    return temp; 
  > }
  > public staticin int cxz(int temp)
  > {
  >     return temp+temp;
  > }
  > //以下代码为program类
  > delegate int abc(int x);
  > abc[] abcArr ={QWQ.zxc,QWQ.cxz};
  > //此时调用数组中的元素相当于使用委托调用
  > ```
  >
  > **委托作为参数**
  >
  > ~~~c#
  > delegate void mydelegate();//定义委托
  > //以下为program类
  > public static void a(){
  >     Console.Write("a");
  > }
  > public static void b(){
  >     Console.Write("b");
  > }
  > public static void test(mydelegate temp){
  >     if(d!=null){
  >         d();
  >     }
  > }
  > public static void Main(args[]){
  >     mydelegate de=a;
  >     test(de);//将de作为参数传递给test，然后通过test进行判断，调用
  > }
  > ~~~

3. 泛型委托

  - **泛型Action委托**

> Action委托至少0个参数，至多16个参数，无返回值。
> Action委托封装的函数必须是无返回值（返回值类型为void）
> 示例:
>
> ```c#
> //无参函数封装
> Action action = abc;
> public void abc()
> {
>     Consoule.Write("123");
> }
> action();//调用abc函数
> //有一个参数的函数封装
> Action<int> action = abc;
> public void abc(int x)
> {
>     Console.Write("123"+x);
> }
> action(222);
> //多个参数的函数封装
> Action<int,double,int> action = abc;
> public void abc(int a,double b,int c)
> {
>     Console.wrWrite("000"+a+b+c);
> }
> action(3,2.7,5);
> //Action<T1,T2...T16> names = NULL;
> //最多支持16个参数，每个参数的类型都需要在泛类的对应位置写好
> ```

  - **泛型Fanc委托**

> Fanc委托至少0个参数，至多16个参数，必须有返回值。 Action委托封装的函
> 示例：
>
> ```c#
> //无参函数封装
> Fanc<string> fanc=abc;
> public string abc()
> {
>     string str="000";
>     return str;
> }
> fanc();
> //有一个参数的函数封装
> Fanc<int,string> fanc=abc;
> public string abc(int x)
> {
>     string str="000";
>     return str+x;
> }
> fanc(3);
> //有多个参数的函数封装
> Fanc<int,double,int,string> fanc=abc;
> public string abc(int a,double b,int c)
> {
>     string str="000";
>     string str1=str+a+b+c;
>     return str1;
> }
> fanc(5,2.4,5);
> //Fanc<T1,T2...T16,TResult> names = NULL;
> //前16个T为16个参数对应的类型，TResult为返回值类型
> ```

4. **多播委托**

  > 委托对象可使用 "+=" 运算符进行合并。一个合并委托调用它所合并的两个委托。只有相同类型的委托可被合并。"-=" 运算符可用于从合并的委托中移除组件委托。
  >
  > ```c#
  > //ABC类
  > delegate void abcdelegate();//定义委托
  > public event abcdelegate abc=NULL;
  > public static void run(){
  >     Console.Write("123");
  >     if(abc!=null)//如果事件内有委托，则调用事件
  >     {
  >         abc();    
  >     }
  > }
  > //QWQ类
  > public static void A1(){
  >     Console.Write("111");
  > }
  > public static void A2(){
  >     Console.Write("222");
  > }
  > 
  > ABC.abc+=A1;
  > ABC.abc=A2;//此处代码错误，因为事件在其他类只能增加或减少
  > ABC.abc();//此处错误，原因同上
  > //想要调用委托的正确方法：
  > ABC.run();//调用函数，因为已经有委托，所以if为true，会调用委托
  > ```

5. 事件(受限委托)

  > 事件也是一种委托，但是不同的是，事件委托只有在事件自身的类可以直接调用，在其余类中，只能进行合并委托或移出委托。同时别的类无非对其进行修改，直接调用。
  >
  > 事件使用方式:在实例化委托时，在public后加event
  >
  > 例如：
  >
  > ```c#
  > //ABC类
  > delegate void abcdelegate();//定义委托
  > public event abcdelegate abc=NULL;
  > public static void run(){
  >     Console.Write("123");
  >     if(abc!=null)//如果事件内有委托，则调用事件
  >     {
  >         abc();    
  >     }
  > }
  > //QWQ类
  > public static void A1(){
  >     Console.Write("111");
  > }
  > public static void A2(){
  >     Console.Write("222");
  > }
  > 
  > ABC.abc+=A1;
  > ABC.abc=A2;//此处代码错误，因为事件在其他类只能增加或减少
  > ABC.abc();//此处错误，原因同上
  > //想要调用委托的正确方法：
  > ABC.run();//调用函数，因为已经有委托，所以if为true，会调用委托
  > ```

  

## 2.常用语句

### 1.循环语句

1. while循环

	> ```c#
	> while(条件表达式){
	>     循环体
	> }
	> ```

2. do...while循环

	> ```c#
	> do{
	>     循环体
	> }while(条件表达式);
	> ```
	>
	> di…while语句每次最少会运行一次
	>
	> 而while语句如果直接为为false，则一次都不会运行

3. for循环

	> ```c#
	> for（初始化;条件表达式;增量表达式){
	>     循环体
	> }
	> ```
	>
	> 示例:
	>
	> ```c#
	> for(int i=0;i<10;i++){
	>     Console.Write(i);
	> }
	> ```

4. 循环中断语句

	- break

		> **break代表着停止循环**

	- continue

		> **continue代表着结束本次循环，运行下一次循环（跳过本次循环）**

### 2.分支语句

1. if语句

	> ```c#
	> if(条件表达式){
	>     代码
	> }
	> 
	> //分支
	> if(){
	> }
	> else if
	> {  
	> }
	> else{  
	> }
	> 
	> //嵌套
	> if(){
	>     if(){
	>         
	>     }
	> }
	> ```

2. switch

	> ```c#
	> switch(a)
	> {
	> case 1:
	> 代码;
	> break;
	> case 2:
	> 代码;
	> break;
	> default:
	> 代码;
	> break;
	> ｝
	> ```
	>
	> - switch后括号内的变量必须为int(整数)值，case后的数字可以自由设置，不用按顺序也可，最后结尾的default...break；可以不带
	> - switch语句，如果括号内的变量int值等于语句中一个case后的数字，则运行那个case后的代码，如果全都没有能对上的case，则运行default
	>
	> ```c#
	> switch(a)
	> {
	> case 1:
	> 
	> case 2:
	> 代码;
	> break;
	> default:
	> 代码;
	> break;
	> }
	> ```
	>
	> - 如果case 1，case 2两个条件结果都一样，执行的都是同一段代码，则可以将前面case的结果那行代码删除，两个case共用一串代码

## 3.数组

### 1.数组的形式

1. 一维数组

[^数组]:数组可以存储多个同类型值

  - 声明数组

> ```c#
> //声明数组
> int[] a;
> //int[]为声明数组
> //a为数组名
> ```

  - 创建数组

> 1. ```c#
> 	int[] a={1,2,3,4}；
> 	//int[]为声明数组
> 	//a为数组名
> 	//{}内为数值，每个数值之间用逗号隔开
> 	```
> 2. ```c#
> 	int[] a;
> 	a=new int[10];
> 	//10为数组长度，可根据情况修改，数组长度就是数组中的数值个数
> 	//这种方式不对数组中的数赋值，则默认为0(注：char和字符串类型的数值默认值是null)
> 	```
> 3. ```c#
> 	int[] a;
> 	a=new int[] {1,2,3,4};
> 	//这种方式和第一种方式相同，第一种方式是这种的缩写
> 	```
> 4. ```c#
> 	int[] a;
> 	a=new int[4] {9,5,4,2};
> 	//这种方式直接规定了数组的长度并进行了赋值
> 	//{}里的值的数量不可以少于或者多于数组长度
> 	```

  - 访问数组元素

> ```c#
> //声明数组，并赋值
> int[] a={1,2,3};
> //调用数组中的数值
> int num=a[0];
> Console.Write(num);//打印结果为：1
> //int num为声明变量
> //a{0}为调用数组中的数值
> //索引和数值大小，数值类型无关int[] a;
> a=new int[4] {9,5,4,2};
> Console.Write(a[2]);
> //a[2]中[]内的2称之为索引或下标
> //索引(下标)从0开始计时，数组内第一个数的索引(下标)就是0，第二个数对索引是1，以此类推
> ```

  - 索引(下标)

>  ```c#
>  int[] a;
>  a=new int[4] {9,5,4,2};
>  
>  Console.Write(a[2]);
>  //a[2]中[]内的2称之为索引或下标
>  //索引(下标)从0开始计时，数组内第一个数的索引(下标)就是0，第二个数对索引是1，以此类推
>  ```

  - 对数组内数值赋值

> ```c#
> int[] a;
> a=new int[4] {9,5,4,2};
> a[2]=999;
> //这样就会将999赋值给数组a下标为2的数值
> //所以此时数组a应该是{9,5,999,4}
> //进行赋值时仅能赋值给存在的数值，不能赋值给不存在的值，例如数组长度为4，赋值给第5个数则会报错
> ```

2. 二维数组

> ```c#
> string[,] names;
> //例如：
> int[,]=new int[3,2] arr={
> {2,3},
> {45,12},
> {13,5}
> };
> //[]中第一个参数代表二维数组中一维的个数，[]中第二个参数代表每个一维数组内包含多少个元素
> ```

3. 三维数组

> ```c#
> int[,,]=new int[2,3,4] arr=
> {
>    {{1,2,3,4},{1,2,3,4},{1,2,3,4}},
>    {{4,3,2,1},{4,3,2,1},{4,3,2,1}}    
> }
> //[]中第一个参数代表三维数组中包含多少个二维数组
> //[]中第二个参数代表每个三二维数组包含多少个一维数组
> //[]中第三个参数代表每个一维数组中包含的元素数量
> ```

4. 多维数组

> ```c#
> //几维数组[]内就需要多少个参数
> //第一个参数代表的n维数组中包含的n-1维数组的数量
> //第二个参数代表n-1维数组中包含的n-2维数组的数量
> //最后一个参数代表一维数组包含的元素个数
> ```


### 2.数组的处理

1. 数组的排序

	1. 官方函数

		> **官方函数**
		>
		> 从小到大排序
		>
		> Array.Sort函数
		>
		> ```c#
		> int[] array = new int[1,4,588,2];//声明一个数组
		> Array.Sort(array);//使用函数将数组进行排序
		> //最后数组为 1,2,4,588
		> ```

	2. 冒泡排序

		> 原理:从第一个数据与后一个数据比对，两个数据中，大的数换到后面然后与下一个数比对，循环往复，直到所有数从小到大排列；最后几次若其中一次循环没有交换位置则停止循环
		>
		> ![冒泡排序原理图](./assets/冒泡排序图.gif"冒泡排序")

2. 数组的属性及方法

	1. 字符串数组转其他数组 

		> ```c#
		> g[] sNums = new[] {"1", "2"};
		> int[] iNums;
		> //转换方法
		> iNums = Array.ConvertAll<string, int>(sNums , s => int.Parse(s));
		> //转换方法-简写
		> iNums = Array.ConvertAll<string, int>(sNums , int.Parse);
		> //转换方法-继续简写
		> iNums = Array.ConvertAll(sNums , int.Parse);
		> ```

	2. **属性**

		| 序号 | 属性 & 描述                                                  |
		| ---- | :----------------------------------------------------------- |
		| 1    | **IsFixedSize**获取一个值，该值指示数组是否带有固定大小。    |
		| 2    | **IsReadOnly**获取一个值，该值指示数组是否只读。             |
		| 3    | **Length**获取一个 32 位整数，该值表示所有维度的数组中的元素总数。 |
		| 4    | **LongLength**获取一个 64 位整数，该值表示所有维度的数组中的元素总数。 |
		| 5    | **Rank**获取数组的秩（维度）。                               |

	3. **方法**

		| 序号 | 属性 & 描述                                                  |
		| ---- | ------------------------------------------------------------ |
		| 1    | **IsFixedSize**获取一个值，该值指示数组是否带有固定大小。    |
		| 2    | **IsReadOnly**获取一个值，该值指示数组是否只读。             |
		| 3    | **Length**获取一个 32 位整数，该值表示所有维度的数组中的元素总数。 |
		| 4    | **LongLength**获取一个 64 位整数，该值表示所有维度的数组中的元素总数。 |
		| 5    | **Rank**获取数组的秩（维度）。                               |

## 4.函数(方法)

### 1.函数基础

1. 函数的声明

	> ```c#
	> static <T> name(){
	>     
	>     return xxx;//xxx为返回值,非空类型函数必须要有返回值
	> }
	> ```

2. 调用函数

	> 注意：函数可以调用自己！！！
	>
	> ```c#
	> static int maxvalue(int a)
	> {
	> int value=a;//将参数赋值给变量
	> return value;//将变量value的值返回
	> }        
	> static void Main(string[] args)
	> {
	> int abc=maxvalue(100);//调用函数并给参数值
	> Console.WriteLine(abc);
	> }
	> ```

3. 函数中的形参

	> ```c#
	> static int maxvalue(int a)//int a为形式参数，在声明的函数值创建变量供函数使用，并且调用函数所填参数应与形式参数类型相同
	> {
	> int value=a;
	> return value;//返回值为value的值
	> }    
	> static void Main(string[] args)
	> {
	> int abc=maxvalue(100);//100为实际参数，在调用函数时，实际参数将赋值给形参
	> //int abc则是maxvalue函数的返回值赋值给了abc
	> Console.WriteLine(abc);//打印
	> }
	> ```

### 2.泛型函数

> 泛型函数则是只定义一个泛型函数不讲整个类定义为泛型
>
> ```c#
> class progarm
>     {
>         static void Main(string[] args)
>         {
>             int number=Getnum<int>(123,456);
>             Console.Write(number);
>         }
>         public static T Getnum<T>(T num1,T num2)
>         {
>             dynamic  a=num1;
>             dynamic  b=num2;
>             return a+b;
>         }
>     }
> ```
>
> 定义方式:
>
> ```c#
> public T ABC<T>(){
>     
> }
> //使用泛类时需要定义泛型方法的类型，例如：
> ABC<int>()//定义泛型函数为int类型
> ```

### 3.虚函数

> 作用:在基类中创建visual函数可以在子类中进行重写
>
> 虚函数声明方法:
>
> ```c#
> //以下代码为基类中
> public virtual void abc(){
>     
> }
> ```
>
> 重写方法:
>
> ```c#
> ublic override void abc(){
>     
> }
> ```
>
> 实际用途:
>
> 在调用时，如果用基类进行声明，用子类进行构造，则只能调用基类本身有的东西，无法调用子类中的东西，及时名字相同，也只能调用基类的东西，但是如果使用虚函数重写，则可以调用子类重写后的内容，而不是基类本身的内容
>
> ```c#
> //基类代码：ABC
> public virtual void qwq(){
>     Console.Write("基类");
> }
> //派生类代码：abc:ABC
> public override void qwq(){
>     Console.Write("派生类");
> }  
> //调用代码：
> ABC cw;//利用父类声明
> cw= new abc();//利用子类构造
> cw.abc()//打印内容 派生类
> ```

### 4.隐藏函数new

> **隐藏函数new**
>
> 作用：
>
> 如果基类中已经有一个同样的函数，子类中也想要创建一个同类型的同名函数，则需要隐藏基类函数
>
> ```c#
> //基类代码：ABC
> public void qwq(){
>     
> }
> //子类代码：abc:ABC
> public new void qwq(){
>     
> }
> ```
>
> 实际作用:
>
> 和关键字base有异曲同工之妙，因为子类会继承父类，所以想要创建一个相同的函数，为了避免冲突要使用new隐藏函数

### 5.抽象函数

> 抽象函数必须在抽象类中声明，并且没有函数体，不过声明之后，此抽象类的子类在写代码的时候必须将这个抽象函数重写
>
> ```c#
> public abstract void abc();//抽象函数
> ```



### 6.函数的重载

> ```c#
> static int Xxx(int a){
>     int c=a;
>     return c;
> }
> static double Xxx(double){
>     double c=a;
>     return c;
> }
> static void Main(string[] args){
>     Xxx(value);//value代表实参
>     //以Xxx命名的函数有两个，但是函数的代码除类型之外全都一致，则这两个函数可以共存，并且会根据实参来自动选择调用的函数，假如value是整数则调用第一个函数
> }
> ```

### 7.函数个例

1. 随机数函数

	> ```c#
	> Random rd = new Random()
	> rd.Next(minvalue,maxvalue)
	> //rd是变量名
	> //rd.Next后面的括号是两个参数
	> //第一个参数是最小值
	> //第二个参数是最大值
	> //运行之后会在最小和最大之间取一个值，包括最小值但不包括最大值
	> ```

## 5.类

### 1.类的形式

#### 1.基本类

1. 类的概念

	> 类实际上是创建对象的模板,每个对象都包含数据,并提供了处理和访问数据的方法。类定义了类的每个对象(称为实例)可以包含什么数据和功能

2. 类的定义

	> **类的创建是一般用编译器在项目下创建的**，而**不是**通过代码在函数内定义的，也可以通过代码在一个.cs文件中创建多个类
	>
	> ```c#
	> //例如
	> public class class1{
	>     
	> }
	> public class class2{
	>     
	> }
	> ```

#### 2.抽象类

1. 抽象类的概念

	> C#允许把类和函数声明为abstract。抽象类不能实例化,抽象类可以包含普通函数和抽象函数,抽象函数就是只有函数定义没有函数体。显然,抽象函数本身也是虚拟的Virtual(只有函数定义,没有函数体实现)。 类是一个模板,那么抽象类就是一个不完整的模板,我们不能使用不完整的模板去构造对象。

2. 抽象类的作用

	> 作用:抽象类可以被继承，但不能实例化，但是可以利用抽象类声明，用其子类进行构造，子类进行重写来进行调用
	>
	> ```c#
	> abstract class ABC(){//抽象类
	>     
	> }
	> ```

#### 3.密封类

> 在c#中密封函数表示不能再重写
>
> 在子类中将虚函数进行重写之后，sealed重写函数将不能被再重写
>
> ```c#
> public sealed override abc(){//我们将基类的abc函数重写之后，因为是sealed函数所以不会再被重写
>     
> }
> ```



### 2.类的构成

#### 1.构造函数

1. 概念

	> 构造函数是一个没有类型的，名字与类名一致的函数
	>
	> 在进行对象实例化的过程中，系统会自动调用对应类内的构造函数，如果没有定义构造函数，则系统会自动调用一个没有任何参数的构造函数
	>
	> 比如:int a;没有赋值,在对象实例化时会自动调用无参的构造函数来进行赋值，最后a=0

2. 定义构造函数

	> **构造函数可以在一个类中定义多个**
	>
	> ```c#
	> public class Vip
	> {
	>     public Vip(){
	>             
	>     }
	> }
	> ```

3. 构造函数调用问题

	> 只有在一个类中没有任何一个构造函数的时候，系统才会自动调用一个无参的构造函数
	>
	> 所以当我们定义了一个构造函数后，实例化对象时必须按照我们的构造函数来填写参数

4. 构造函数参数问题

	> 在构造函数中，调用时编译器一般会提示参数原名以方便命名，如果我们多个参数命名都为temp1，temp2等等则难以区分，所以命名时应做到见名知意
	>
	> 例如：参数名字就是 string name;
	>
	> 但是如果我们定义变量时使用了相同的名字则会出现赋值错误的问题系统无法处理name = name;
	>
	> 这时候我们可以使用this
	>
	> ```c#
	> public class Vip{
	>     public string name;
	>     public Vip(string name){
	>         this.name=name;    
	>     }
	> }//this代表当前对象 而形参中的name只是一个参数而不是对象
	> ```

#### 2.属性

1. 属性解读

	> 在类中定义好成员之后，如果权限为private权限，则需要额外定义函数来进行读写，而系统提供了属性来帮助我们进行读写，不用再额外定义函数
	>
	> 不使用属性进行读写：
	>
	> ```c#
	> private int a;
	> public void SetA(int a){//写入
	>     this.a=a;
	> }
	> public int GetA(){//读取
	>     return a;
	> }
	> ```
	>
	> 使用属性读写：
	>
	> ```c#
	> private int a;
	> public int A{
	>     set;//写入
	>     get;//读取
	> }
	> ```

2. 属性的写法

	> ```c#
	> //第一种
	> private int a;
	> public int A{
	>     get;set;
	> }
	> //第二种
	> private int a;
	> public int A{
	>     set{
	>         a=value;//value为自带的形参不需要额外定义                
	>     }
	>     get{
	>        return a;     
	>     }
	> }
	> ```

3. 属性参数

	> ```c#
	> private int a;
	> public int A{
	>     set{
	>         a=value;//set方法会自带一个形参所以使用set时只需要 对<对象>.set(值)
	>     }
	>     get{
	>         return a;    
	>     }
	> }
	> ```

4. 属性的特性

	> ```c#
	> //在不声明private int a的情况下
	> public int A{
	>     set;get;
	> }
	> //这种情况会自动创建一个private权限的int类型的变量a
	> ```

### 3.类的继承

#### 1.继承

1. 概念

	> **概念**
	>
	> 类可以分为父类(基类)和子类(派生类)
	>
	> 子类可以继承父类中的所有东西包括变量，函数等
	>
	> 注意:一个类如果没有继承父类，则默认继承Object类

2. 继承方式

	> ```c#
	> class Vip:VIP//Vip继承VIP
	> ```
	>
	> 

#### 2.接口

1. 接口的概念

	> 只提供接口，不实现功能
	>
	> 定义一个接口在语法上跟定义一个抽象类完全相同，但不允许提供接口中任何成员的实现方式，一般情况下，接口只能包含方法，属性，索引器和事件的声明。 接口不能有构造函数，也不能有字段，接口也不允许运算符重载。接口定义中不允许声明成员的修饰符，接口成员都是公有的

2. 定义接口

	> ```c#
	> public interface abc{//abc为接口名
	>     public void awe();//awe为接口中的功能
	> }
	> ```

3. 实现接口

	> ```c#
	> public class ABC:abc{
	>     public void awe(){
	>       //注意，对接接口后，需要将接口中所有方法的功能写出来，否则报错，无法执行代码      
	>     }
	> }
	> //以下为错误示例
	> public class ABC:abc{
	>     public void aaa(){
	>         //此时这个ABC类会报错，因为没有将接口中的awe写出来所以会报错    
	>     }
	> }
	> ```

4. 接口的多态

	> ```c#
	> //接口具有多态性例如
	> //一下代码为接口代码
	> public interface ABC{
	>     public void qwe();
	> }
	> //以下代码为对接接口ABC的一个类BBC
	> public class BBC:ABC{
	>     public void qwe(){
	>         Console.WriteLine("BBC")    
	>     }
	> }
	> //以下代码为对接接口ABC的一个类CBC
	> public class CBC:ABC{
	>     public void qwe(){
	>         Console.WriteLine("CBC")    
	>     }
	> }
	> //以下代码为main方法代码
	> BBC qwq1 =new BBC()//打印qwq1.qwe结果为BBC
	> CBC qwq2 =new CBC()//打印qwq2.qwe结果为CBC
	> ABC qwe1 =new BBC()//打印qwe2.qwe结果为BBC
	> ABC qwe2 =new CBC()//打印qwe2.qwe结果为CBC
	> //从以上结果可以发现
	> //利用使用接口ABC进行声明并实例化对象
	> //依然可以调用对应类的函数，这就是接口的多态
	> ```

5. 接口的继承

	> ```c#
	> //接口是可以继承一个接口的，例如：
	> //接口1 ABC1
	> public interface ABC1{
	>     public void a1();
	> }
	> //接口2 ABC2
	> public interface ABC2:ABC1{//继承ABC1
	>     public void a2();
	> }
	> //对接接口ABC2的类 ZZZ
	> public class ZZZ:ABC2{
	>     public void a1{            
	>     }//实现a1功能
	>     public void a2{            
	>     }//实现a2功能
	>     //因为接口ABC2继承了接口ABC1，所以ABC2包含了ABC1，所以在对接ABC2时，需要将ABC1接口也需要的功能实现
	> }
	> ```

	

#### 3.子类的构造函数

1. 调用子类构造函数构造函数(无参)

	> 在调用子类构造函数时会先调用父类的构造函数再调用子类的构造函数
	>
	> 调用方式:
	>
	> 会自动调用父类构造函数，也可以写成下面的形式
	>
	> ```c#
	> public <构造函数名>():base()
	> //例子：
	> //父类 ABC
	> public ABCD()
	> {
	>     Console.WriteLine("123");
	> }
	> //子类 abc
	> public abcd():base//调用父类构造函数
	> {
	>     Console.WriteLine("一二三");
	> }
	> //main函数调用子类
	> abc qwq=new abc();
	> //最后打印结果为
	> 123
	> 一二三
	> ```

2. 调用子类构造函数构造函数(有参)

	> 在调用子类的有参构造函数时，会先调用父类的无参构造函数再调用子类的构造函数
	>
	> 方式：
	>
	> 同上
	>
	> 调用示例:
	>
	> ```c#
	> //父类 ABC
	> public ABCD()
	> {
	>     Console.WriteLine("123");
	> }
	> //子类abc
	> public abcd(int a)
	> {
	>     Console.WriteLine(a);
	> }
	> //main函数
	> abc qwq=new abc(112233);
	> //最后打印结果为：
	> 123
	> 112233
	> ```

3. 调用子类构造函数构造函数(有参)，并调用父类构造函数(有参)

	> 调用子类构造函数构造函数(有参)，并调用父类构造函数(有参) 在调用子类的有参构造函数时，会先调用父类的构造函数再调用子类的构造函数
	>
	> 调用方式:
	>
	> ```c#
	> public <构造函数名>(形参):base(实参)//base后面括号内地实参要对应父类对应的有参构造函数的形参
	> //示例：
	> //父类 ABC
	> public ABCD(int A, int B)
	> {
	>     Console.WriteLine("{0},{1}",A,B);
	> }
	> //子类abc
	> public abcd(int q,int qq,int qqq):base(qq,qqq)
	> {
	>     Console.WriteLine("{0}",q);
	> }
	> //main函数
	> abc qwq = new abc(456,157,134);
	> //最后打印结果为
	> 157,134
	> 456
	> ```

### 4.类的应用

#### 1.常用属性

1. **Tostring()**

	> Tostring直接使用并不会显示类中的数据，所以想要使用Tostring属性直接将里面的数据进行输出，需要讲该属性重写
	>
	> ```c#
	> //以下为main函数代码
	>         static void Main(string[] args)
	>         {
	>             Class1 temp = new Class1(12,13);
	>             Console.WriteLine(temp);
	>         }
	> //以下为Class1类的代码
	>         private int num1;
	>         private int num2;
	> 
	>         public Class1(int num1, int num2)//构造函数
	>         {
	>             this.num1 = num1;
	>             this.num2 = num2;
	>         }
	> //main函数的打印temp想直接取得num1和num2则需要进行Tostring重写
	>         public override string ToString()
	>         {
	>             string str = num1 + "," + num2;
	>             return str;
	>         }
	> //这样temp.Tostring则是直接打印num1和num2
	> ```

2. **Equals()**

	> **Equals的作用就是比较，如果两方相等则返回true，否则返回folse，不过区别于==的是，Equals可以用于两个对象进行比较**
	>
	> ```c#
	> //main函数
	>         static void Main(string[] args)
	>         {
	>             Class1 temp1 = new Class1(12,13);
	>             Class1 temp2 = new Class1(12,13);
	>             bool Bool = temp1.Equals(temp2);
	>             Console.WriteLine(Bool);
	>         }
	> //class1类
	>     internal class Class1
	>     {
	>         private int num1;
	>         private int num2;
	> 
	>         public Class1(int num1, int num2)
	>         {
	>             this.num1 = num1;
	>             this.num2 = num2;
	>         }
	> //如果想将在main函数内两个对象的值进行比较则需要对Equals函数进行重写
	>         public override bool Equals(object obj)
	>         {
	>             Class1 num = (Class1)obj;//将传回数据转换类型
	>             if (num.num1 == num1 && num.num2 == num2)//比较数据是否相等
	>             {
	>                 return true;
	>             }
	>             else
	>             {
	>                 return false;
	>             }
	>         }
	> ```

#### 2.对象

1. 对象的概念

	> 我们把类创建的变量称之为对象

2. 对象的创建与使用
	> ```c#
	> class Vip
	>     {
	>         int a1;//声明一个整型a1
	>         string str;//声明一个字符串str
	>         public void value(){
	>             Console.WriteLine("123");                            
	>         }//声明一个函数value
	>     }
	> class program
	>     {
	>         static void Main(string[] args){
	>             Vip c1 = new Vip();//声明一个对象并实例化
	>             //也可以分开写 先声明再实例化 Vip c1;声明 c1=new Vip();实例化
	>             c1.a1=10086;//将对象内的a1赋值
	>             c1.str="123&$r";//同上
	>             c1.value();//调用对象内函数    
	>         }    
	>     }
	> ```
	>



### 5.泛类

#### 1.泛型类

> 泛型：通过参数化类型来实现在同一份代码上操作多种数据类型。利用“参数化类型"将类型抽象化，从而实现灵活的复用
>
> 定义一个泛型类就是指的是，定义一个类，这个类中某些字段的类型是不确定的，这些类型可以在类构造的时候确定下来，例如:
>
> ```c#
> class progarm
>     {
>         static void Main(string[] args)
>         {
>             class2<double> ABC = new class2<double>();
>             Console.WriteLine(ABC.Getnum(11.2,11.6));
>         }
>     }
>     public class class2<T>
>     {
>         private T a;
>         private T b;
>         public T Getnum(T a,T b)
>         {
>             this.a = a;
>             this.b = b;
>             dynamic  num1 = a;
>             dynamic  num2 = b;
>             return num1 + num2;
>         }
>     }
> ```
>
> 泛型类的定义:
>
> ```c#
> public class classABC<T>//<>内可以为别的字符，也可以有多个泛型，不过通常使用T来代表，T1,T2代表多个
> {   
> }
> 
> //使用泛类时需要定义泛类的类型，例如：
> classABC<int> ABC = new classABC<int>();//定义泛类为int类型
> ```

#### 2.列表List

1. 列表的概念

	> 列表相当于一个不用定义大小的数组，可以方便的添加，删除，管理数据。
	>
	> List 是强类型对象的集合，可以通过索引对其进行访问，并具有用于排序，搜索和修改列表的方法。 它是System.Collection.Generic命名空间下的ArrayList的泛型版本。

2. 列表的知识点

	> 列表分为容量Capacity和数据个数Count
	>
	> 列表本质上是一个数组，在创建时，如果没有设置初始容量，则容量为0，当存储1个数据时，容量会扩大为4，存储第5个时会翻倍，同理第9个时会容量扩充为16，每次存储数据大于容量时，容量会自动翻倍。
	>
	> 原理:每次容量不够时，会自动创建一个容量为当前容量2倍的数组，并用Array.Copy()函数将当前数据复制到新的数组，从而完成扩容
	>
	> 所以，在知道数据个数多少个时，设定足够的初始容量可以减少工作量

3. **创建列表**

	> ```c#
	> //以下代码均是在引用System.Collections.Generic的情况下
	> //第一种：声明并实例化
	> List<int> ABC = new Lsit<int>();
	> /*格式:List<类型> 列表名 = new List<类型>();*/
	> //第二种:声明并实例化并设定初始容量
	> List<int> ABC = new Lsit<int>(10);
	> /*格式:List<类型> 列表名 = new List<类型>(初始容量);*/
	> //第三种:声明并实例化并设定初始容量并存储值
	> List<int> ABC = new Lsit<int>(10){123,124,257};
	> /*格式:List<类型> 列表名 = new List<类型>(初始容量){值1,值2…};*/
	> ```

4. **将元素添加至列表**

	> ```c#
	> //添加单个元素
	> List<int> ABC = new Lsit<int>();
	> ABC.Add(10086);
	> //格式:列表名.Add(元素);
	> 
	> //添加数组，或集合内的所有元素:
	> string[] cities = new string[3]{ "Mumbai", "London", "New York" };
	> var popularCities = new List<string>();
	> // 在列表中添加数组
	> popularCities.AddRange(cities);
	> var favouriteCities = new List<string>();
	> // 添加列表 
	> favouriteCities.AddRange(popularCities);
	> //格式:列表名.AddRange(列表/数组);
	> ```

5. **访问列表**

	> 列表访问方式和数组相同通过下标的方式
	>
	> ```c#
	> List<int> ABC = new Lsit<int>(3){17,33,64};
	> Console.WriteLine(ABC[2]);
	> //最后打印结果为64
	> //格式:列表名[索引/下标]
	> ```

6. **修改列表元素**

	> ```c#
	> List<int> ABC = new Lsit<int>(3){17,33,64};
	> ABC[2]=10086；//赋值
	> Console.WriteLine(ABC[2]);
	> //最后打印结果为10086
	> ```

7. **操作列表的属性和方法**

	| **属性** | **用法**           |
	| -------- | ------------------ |
	| Count    | 获取列表中元素个数 |
	| Capacity | 获取容量大小       |
	| **方法**     | **用法**                                           |
	| Add          | 在列表的末尾添加元素。                             |
	| AddRange     | 将指定集合的元素添加到列表的末尾。                 |
	| BinarySearch | 搜索元素并返回该元素的索引。                       |
	| Clear        | 从列表中删除所有元素。                             |
	| Contains     | 检查指定元素在列表中是否存在。                     |
	| Find         | 根据指定的谓词函数查找第一个元素。                 |
	| Insert       | 在列表中的指定索引处插入元素。                     |
	| InsertRange  | 在指定的索引处插入另一个集合的元素。               |
	| Remove       | 删除指定元素的第一次出现。                         |
	| RemoveAt     | 删除指定索引处的元素。                             |
	| RemoveRange  | 删除所有与提供的谓词功能匹配的元素。               |
	| Sort         | 对所有元素进行排序。                               |
	| TrimExcess   | 将容量设置为实际的元素数。                         |
	| TrueForAll   | 确定列表中的每个元素是否与指定谓词定义的条件匹配。 |
	
	
	
	#### 3.字典Dictionary
	
	1. 字典的概念
	
		> 在C#中，Dictionary的主要用途是提供快速的基于键值的元素查找
		>
		> 字典格式
		>
		> `Dictionary<[key], [value]>`
	
	2. Dictionary的描述
	
		> 1、从一组键（Key）到一组值（Value）的映射，每一个添加项都是由一个值及其相关连的键组成
		>
		> 2、任何键都必须是唯一的
		>
		> 3、键不能为空引用null（VB中的Nothing），若值为引用类型，则可以为空值
		>
		> 4、Key和Value可以是任何类型（string，int，custom class 等）
		>
		> > Dictionary常用用法：以 key 的类型为 int , value的类型为string 为例
	
	3. **创建及初始化**
	
		> ```c#
		>  Dictionary<int,string> myDictionary = new Dictionary<int,string>();
		> ```
	
	4. **添加元素**
	
		> ```c#
		> myDictionary.Add(1,"C#");
		> myDictionary.Add(2,"C++");
		> myDictionary.Add(3,"ASP.NET");
		> myDictionary.Add(4,"MVC");
		> ```
	
	5. **通过Key查找元素**
	
		> ```c#
		> if(myDictionary.ContainsKey(1)){
		>     Console.WriteLine("Key:{0},Value:{1}","1", myDictionary[1]);
		>  }
		> ```
	
	6. **仅遍历键 Keys 属性**
	
		> ```c#
		> Dictionary<int,string>.KeyCollection keyCol=myDictionary.Keys;
		> foreach(intkeyinkeyCol)
		> ...{
		>         Console.WriteLine("Key = {0}", key);
		> }
		> ```
	
	7. **仅遍历值 Valus属性**
	
		> ```c#
		> Dictionary<int,string>.ValueCollection valueCol=myDictionary.Values;
		> foreach(stringvalueinvalueCol)
		> ...{
		>         Console.WriteLine("Value = {0}", value);
		> }
		> ```
	
	8. **通过Remove方法移除指定的键值**
	
		> ```c#
		> myDictionary.Remove(1);
		> if(myDictionary.ContainsKey(1))
		> ...{
		> 　　Console.WriteLine("Key:{0},Value:{1}","1", myDictionary[1]);
		> }
		> else{
		>     Console.WriteLine("不存在 Key : 1"); 
		>  }
		> ```
	
	9. **其它常见属性和方法的说明：**
	
		| Comparer      | 获取用于确定字典中的键是否相等的 IEqualityComparer |
		| ------------- | -------------------------------------------------- |
		| Count         | 获取包含在 Dictionary中的键/值对的数目             |
		| Item          | 获取或设置与指定的键相关联的值                     |
		| Keys          | 获取包含 Dictionary中的键的集合                    |
		| Values        | 获取包含 Dictionary中的值的集合                    |
		| Add           | 将指定的键和值添加到字典中                         |
		| Clear         | 从 Dictionary中移除所有的键和值                    |
		| ContainsKey   | 确定 Dictionary是否包含指定的键                    |
		| ContainsValue | 确定 Dictionary是否包含特定值                      |
		| GetEnumerator | 返回循环访问 Dictionary的枚举数                    |
		| GetType       | 获取当前实例的 Type （从 Object 继承）             |
		| Remove        | 从 Dictionary中移除所指定的键的值                  |
		| ToString      | 返回表示当前 Object的 String （从 Object 继承）    |
		| TryGetValue   | 获取与指定的键相关联的值                           |

### 6.类的成员

#### 1.索引器

1. 索引器

	> **索引器（Indexer）** 允许一个对象可以像数组一样使用下标的方式来访问。
	>
	> ```c#
	> public 返回类型 this[索引类型 index]
	> {
	>     get{//get访问器，如果只设置，不读取可以不带get
	>          //将值返回时会调用get
	>          //用return返回值   
	>     }
	>     set{//set访问器，如果只读取，不设置值，可以不带set
	>         //对对应索引的值进行赋值           
	>     }
	> }
	> ```

2. 索引器的用途

	> 索引器的行为的声明在某种程度上类似于属性（property）。就像属性（property），您可使用 get 和 set 访问器来定义索引器。但是，属性返回或设置一个特定的数据成员，而索引器返回或设置对象实例的一个特定值。换句话说，它把实例数据分为更小的部分，并索引每个部分，获取或设置每个部分。 定义一个属性（property）包括提供属性名称。索引器定义的时候不带有名称，但带有 this 关键字，它指向对象实例。
	>
	> 使用案例:
	>
	> ```c#
	> //以下代码在ABC类
	> private string[] num=new string[250,147,369,4769];
	> public int this[int index]
	> {
	>     get{
	>         return num[index];  
	>     }
	>     set{
	>         num[index]=value;//此处的value为set函数自带的形参
	>     }
	> }
	> ```

	

## 6.线程

### 1.多线程
> `using System.Threading;`多线程需要在System.Threading;命名空间下使用

1. 线程的定义

	> **线程** 被定义为程序的执行路径。每个线程都定义了一个独特的控制流。如果您的应用程序涉及到复杂的和耗时的操作，那么设置不同的线程执行路径往往是有益的，每个线程执行特定的工作。
	>
	> **前台线程** 只要有前台线程还在运行，则程序不会关闭
	>
	> [^后台线程]: 后台线程服务于前台线程，当前台线程全部关闭时，无论后台线程有没有运行完，都会强制中断
	>
	> **后台线程** 服务于前台线程，当前台线程全部关闭时，无论后台线程有没有运行完，都会强制中断
	>
	> ***一般情况下***，Thread类创建的线程为前台线程，线程池内的线程都是后台线程
	>
	> 使用Thread创建线程时，可以通过`IsBackground`来设置是否为前台线程，例如:
	>
	> ```c#
	> Thread thread = new Thread(Threadtest){IsBackground=false};
	> //此时为前台线程
	> Thread thread = new Thread(Threadtest){IsBackground=false};
	> //此时为后台线程
	> ```
1. 线程的创建

	> ```c#
	> static void Main(string[] args)
	>      {
	>          ThreadStart threadStart = new ThreadStart(abc);//创建线程任务
	>          Thread thread = new Thread(threadStart);//创建新线程
	>          //Thread thread = new Thread(new ThreadStart(abc));
	>          //以上两步可合为上面这一行
	>          thread.Start();//线程开始运行            
	>          Console.WriteLine("123");
	>      }
	>      public static void abc()
	>      {
	>          Console.WriteLine("abc");
	>      }
	> 
	> ThreadStart 任务名 = new ThreadStart(要执行的函数名);//创建线程任务
	> Thread 线程名 = new Thread(要执行的任务名);//创建新线程
	> 线程名.Start();//线程开始运行
	> 
	> //可以将ThreadStart省略不写
	> Thread thread = new Thread(Threadtest);
	> 
	> Thread 线程名 = new Thread(要执行的任务名);
	> 线程名.Start();
	> ```
	>
	> 先通过ThreadStart实例化一个任务，执行这个任务的线程会运行对应函数，然后实例化一个线程，这个线程必须执行一个任务

2. 线程的控制

	> Thread.sleep(500);//线程休眠，单位是ms，1s=1000ms

2. 线程的优先级

	> 多个线程表面上是多个线程同时进行，实际上是CPU每次执行每个线程的一部分，立马执行下一个线程的一部分，所以，线程优先级高的线程会优先进行运算
	>
	> 默认优先级为`Normal`
	>
	> 可以通过`Priority`属性来设置线程的优先级,`Priority`的优先级对应的值为`ThreadPriority`这个`enum`的成员  
	>
	> `Lowest=0``BelowNormal=1``Normal=2``AboveNormal=3``Highest=4`
	>
	> ```c#
	> thread.Priority = ThreadPriority.BelowNormal;
	> //设置优先级为1
	> ```

3. 线程的插入

	> 可以使用join时线程插入此线程，当插入的线程执行完之后，才会继续执行当前线程
	>
	> ```c#
	>         public static void Main(string[] args)
	>         {
	>             Thread thread = new Thread(test);
	>            	thread.Start();
	>             thread.Join();
	>         }
	> ```
	>
	> 

4. **Thread 类常用的属性和方法**

	| 属性               | 描述                                                         |
	| :----------------- | :----------------------------------------------------------- |
	| CurrentContext     | 获取线程正在其中执行的当前上下文。                           |
	| CurrentCulture     | 获取或设置当前线程的区域性。                                 |
	| CurrentPrincipal   | 获取或设置线程的当前负责人（对基于角色的安全性而言）。       |
	| CurrentThread      | 获取当前正在运行的线程。                                     |
	| CurrentUICulture   | 获取或设置资源管理器使用的当前区域性以便在运行时查找区域性特定的资源。 |
	| ExecutionContext   | 获取一个 ExecutionContext 对象，该对象包含有关当前线程的各种上下文的信息。 |
	| IsAlive            | 获取一个值，该值指示当前线程的执行状态。                     |
	| IsBackground       | 获取或设置一个值，该值指示某个线程是否为后台线程。           |
	| IsThreadPoolThread | 获取一个值，该值指示线程是否属于托管线程池。                 |
	| ManagedThreadId    | 获取当前托管线程的唯一标识符。                               |
	| Name               | 获取或设置线程的名称。                                       |
	| Priority           | 获取或设置一个值，该值指示线程的调度优先级。                 |
	| ThreadState        | 获取一个值，该值包含当前线程的状态。                         |

### 2.线程池

1. 概念

  > 创建线程需要时间。如果有不同的小任务要完成,就可以事先创建许多线程，在应完成这些任务时发出请求。这个线程数最好在需要更多的线程时增加,在需要释放资源时减少。不需要自己创建线程池，系统已经有一个ThreadPool类管理线程。这个类会在需要时增减池中线程的线程数,直到达到最大的线程数。池中的最大线程数是可配置的。
  >
  > 线程池的线程均为后台线程[^后台线程]

2. 线程池的创建

	> 线程池不需要创建，系统自带一个ThreadPool类

3. 入池

	> 线程池特点:入池的任务运算完毕后，线程将销毁，下次调用时线程池随机分配线程，所以，线程池适用于每次执行小运算使用
	>
	> ```c#
	> public static void test(object state)//需要入池的函数形参需要有一个object类的参数，一般用state命名
	>         {
	>             Console.WriteLine("thread running...");
	>             Thread.Sleep(1000);
	>             Console.ReadKey();
	>         }
	>         public static void Main(string[] args)
	>         {
	>             ThreadPool.QueueUserWorkItem(test);//将test放入线程池运行
	>             Console.WriteLine("Main thread running...");
	>         }
	> ```

### 3.任务

任务需要引用`System.Threading.Tasks`命名空间才可以使用

> task是一个后台线程[^后台线程]

task的创建

> ```c#
> //方法一
> TaskFactory taskFactory = new TaskFactory();//通俗点通过工厂创建任务
> Task t = taskFactory.StartNew(test);//工厂将执行的任务交给任务类来执行
> 
> 
> //方法二
> Task task = new Task(test);//通俗点直接将任务交给任务类
> task.Start();//告诉任务类该执行任务了
> ```

连续任务

> 连续任务会执行完任务后执行指定的下一个任务
>
> ```c#
> 
> static void test1()
> {
>     Console.WriteLine("111");
> }
> static void test2(Task t)//要连续执行的任务需要填入Task类的参数,目的是可以判断上一个任务的状态
> {
>     Console.WriteLine("222");
> }
> 
> 
> Task t1 =new Task(test1);//创建第一个任务,t1
> Task t2 = t1.ContinueWith(test2);//第一个任务t1执行完后将执行t2任务test2
> ```



### 4.lock

- lock-锁

> 当多个线程访问一个数据进行读写时,可能会出现线程1调用完进行修改时,线程2进行调用时被修改,导致资源访问冲突
>
> 例如:
>
> ```c#
> private int A=0;
> public void temp(){
> A=123;
> Console.Write(A);
> A=124;  
> }
> //当线程1运行到第三行时,线程2刚开始运行第二行就会导致打印的结果为124
> ```
>
> 解决这个问题可以通过给方法上锁(lock)的方式来解决,被锁住的代码不允许多个线程同时操作,而是只有一个线程可以拿到lock,当上一个线程运行完后,下一个线程才能拿到lock再运行
>
> 实现方法:
>
> ```c#
> private object _lock = new object();//创建锁
> private int A=0;
> public void temp(){
> lock(_lock){//上锁
> 		A=123;
> 		Console.Write(A);
> 		A=124;
> 	}
> }
> ```

- 死锁问题

> 当一段代码上了两个lock,
>
> 假设函数A的解锁顺序是先拿lock1再拿lock2,
>
> 函数B是先拿lock2再拿lock1
>
> ,此时就会出现执行A的线程拿到了lock1,
>
> 而执行B的线程拿到了lock2,
>
> 两个线程都因为没有拿到另一把锁而导致卡住,这就是死锁问题


## 7.关键字

### 1.修饰符

#### 1.成员修饰符

1. abstract

	> abstract修饰方法的时候表示该方法为抽象方法，抽象方法需要由子类来实现，如果子类没实现该抽象方法那么子类同样是抽象类；含有抽象方法的类一定是抽象类

2. sealed

	> sealed修饰方法时表示该方法不能被覆盖

3. static

	> static修饰类成员时，该成员为类成员（静态成员），只能通过“类名.成员名”的方式访问；当static修饰构造函数时，构造函数不能含有任何参数，不能有其他修饰符，构造函数不能对对象成员进行初始化操作，但是能够对静态成员进行初始化或者调用，并在静态构造函数中初始化的静态成员为最终初始化结果。

4. virtual

	> virtual修饰方法成员，表示虚方法，虚方法允许在子类中重写来覆盖该方法

5. override

	> override表示该方法为覆盖父类的方法

6. readonly

	> readonly只读字段，只能在初始化时赋值，或者在构造函数中进行赋值，除此之外无法进行赋值

7. const

	> const常量字段，编译时必须指定其值，其值编译到程序中，无法进行修改

8. new

	> 注意是修饰符new，隐藏从父类成员继承的成员，在不使用 new 修饰符的情况下隐藏成员是允许的，但会生成警告；显然，new不能和abstract同时用。 另外New也可以是运算符，用于创建对象并调用构造函数

#### 2.访问权限修饰符

1. **public权限**

	> public权限为公开权限，不在当前类之下也可以修改，调用，不在当前程序集下可以通过引用当前程序集来调用

2. **private权限**

	> private为私密权限，仅在当前类下可以被调用，修改，别的类无法直接调用，修改

3. **protected权限**

	> protected权限为保护权限，仅在当前类和子类下可以被调用，修改，非子类无法直接调用修改

4. **internal权限**

	> 同一程序集中的任何代码都可以访问该类型或成员，但别的程序集的代码不可以访问

5. **protected internal权限**

	> 在一程序集中,protected internal体现的是 internal 的权限;在其他程序集中,protected internal权限体现的是protected的权限

6. **访问权限修饰函数**

	> public 和 private 修饰字段和函数的时候，表示该字段或者方法能不能通过对象去访问，只有 public 的才可以通过对象访问， private （私有的）只能在类模板内部访问。
	>
	>  protected 保护的，当没有继承的时候，它的作用和 private 是一样的，当有继承的时候， protected 表示可以被子类访问的字段或者函数

7. **类的访问权限修饰符**

	> public class .…
	>
	> class …
	>
	> 前者可以在别的项目下访问，后者不行

#### 3.类的修饰符

1. Partial

	> Partial：部分类（或分布式类），可以将一个类的定义分散为写在多个代码段中，这些代码段可以存放于多个不同的C#源文件，编译器在编译时将这些分散的部分类合并到一起编译成一个完整的类

### 2.常用关键字

1. base

	> base代表基类对象(父类对象)
	>
	> 在继承时，子类会继承父类的变量，函数等，但是，父类有一个变量，我们子类也创建一个变量，名字一样的话，最后会调用最近的，也就是子类的变量，这就导致父类变量无法使用，所以，这时候就可以使用base关键了来表示父类对象(基类对象)
	>
	> 例如:
	>
	> ```c#
	> private int A;
	> //假设上面的代码为基类代码，以下为子类代码
	> public int A;
	> public value(int A){
	>     base.A=A;//将参数A赋值给父类中的A
	>     this.A=A;//将参数A赋值给子类中的A
	> }
	> ```
	>
	> 

2. this

	> 1.当前对象
	>
	> this代表当前对象
	>
	> 在定时函数时，调用时编译器一般会提示参数原名以方便命名，如果我们多个参数命名都为temp1，temp2等等则难以区分，所以命名时应做到见名知意 例如：参数“名字”就是 string name; 但是如果我们定义变量时使用了相同的名字则会出现赋值错误的问题系统无法处理name = name;会报错 这时候我们可以使用this 例如:
	>
	> ```c#
	> public class Vip{    
	> public string name;
	> 
	> public Vip(string name){        
	> this.name=name;    
	> 
	>  }
	> }//this代表当前对象 而形参中的name只是一个参数而不是对象
	> ```
	>
	> 



## 8.特性

### 1.常用特性

#### Obsolete和Conditional

**Obsolete**

> 在定义函数的上一行增加次特性，会提示弃用的
>
> ```c#
> //例如
> [Obsolete]
> static void test()
> {
> 
> }
> //此时test()为弃用函数，会提示，不过可以调用
> //参数：
> [Obsolete("string",bool)]
> //string为额外提示内容，bool值如果为true则禁止调用，直接报错
> ```

**Conditional**

> 在定义函数的上一行增加次特性，会根据是否存在对应宏，而判断是否运行
>
> 如果定义了对应的宏，则运行此函数，反之
>
> 如果不运行，进行调用并不会报错，只是会没有结果，函数体不会运行
>
> ```c#
> //参数
> [Conditional("string")]//string为宏名
> //示例
> #define ABC
> [Conditional("ABC")]
> static void test()
> {
> 
> }
> ```

#### 调用者信息特性和DebuggerStepThrough特性

**调用者信息特性**

> `CallerFilePath`  调用该函数的文件路径
>
> `CallerLineNumber` 调用该函数的代码行数
>
> `CallerMemberName` 调用该函数的名称
>
> ```c#
> 使用方法：
> static void PrintOut(string str,
>     [CallerFilePath]string fileName = "", //三个特性都必须初始化赋值
>     [CallerLineNumber]int lineNumber = 0, 
>     [CallerMemberName]string methodName = "")
> 
> ```

**DebuggerStepThrough特性**

> ```c#
> //该特性可以让逐过程调试时，将这个函数所有过程全部当做一个直接跳过
> [DebuggerStepThrough]
> public static void test(){
>     
> }
> ```

### 2.自定义特性

特性一般新开一个类

1. 命名

	> 特性类命名可以直接命名，也可以在名字后增加`Attribute`,例如
	>
	> AuthorAttribute`在使用此特性时`[Author]`即可，但是如果用typeof等方式仍需引用`AuthorAttribute`
	>
	> 或者此特性可直接命名为`Author`
	>
	> **继承**

2. 继承

	> ```c#
	> //创建特性时，该类应继承Attribute类
	> public class AuthorAttribute : System.Attribute
	> public class AuthorAttribute : Attribute
	> ```

3. 参数

	> 特性只能包括字段，属性，构造函数
	>
	> 构造函数的参数是自定义特性的位置参数
	>
	> 所有公共读写字段或属性都是命名参数
	>
	> 位置参数属于必填，命名参数为选填
	>
	> ```c#
	> public class AuthorAttribute : System.Attribute  
	> {  
	>     private string name;  
	>     public double version;  
	>   
	>     public AuthorAttribute(string name)  
	>     {  
	>         this.name = name;  
	>         version = 1.0;  
	>     }  
	> } 
	> //在上述代码中，使用此特性时必须输入name，而vsrsion可选择使用默认值。
	> //使用案例
	> [Author("abc", version = 1.1)]
	> public static void test(){
	>     
	> }
	> [Author("abc")]
	> public static void test(){
	>     
	> }
	> ```

4. 目标

	> 可以通过`AttributeUsage`特性来设定特性使用对象
	>
	> ```c#
	> [System.AttributeUsage(System.AttributeTargets.Class | System.AttributeTargets.Struct)
	> public class Author: Attribute
	> {
	> }
	> [System.AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct)
	> public class Author: Attribute
	> {
	> }
	> //规定特性只作用于class和struct目标
	> ```
	>
	> 

## 9.LINQ

### 1.反射Reflection

#### Type类

> **Type类**
>
> 通过type类反射，可以获得另一个类的东西
>
> ```c#
> //获取对应类的信息
> Type type = typeof(Myclass);//获取反射
> //Myclass myclass =new Myclass();
> //Type type = typeof(myclass);//这种方式也可以进行反射
> //使用案例:
> //打印Myclass类的数据
> Console.WriteLine(type.Name);//类名
> Console.WriteLine(type.FullName);//解决方案.类名
> //获取类中的所有字段
> FieldInfo[] fis = type.GetFields();
> foreach (FieldInfo fi in fis)
> {
>     Console.WriteLine(fi.Name);//打印字段的名字
> }
> //获取类中的所有属性
> PropertyInfo[] pis = type.GetProperties();
> foreach (PropertyInfo pi in pis)
> {
>     Console.WriteLine(pi.Name);//打印属性的名字
> }
> //获取类中的所有方法
> MemberInfo[] mis = type.GetMembers();
> foreach (MemberInfo mi in mis)
> {
>     Console.WriteLine(mi.Name);//打印方法的名字
> }
> //以上仅为部分
> ```

## 10.文件的操作

### 1.Filelnfo和Directorylnfo类读取文件和文件夹属性

**注意**：使用此类需要引入`System.IO`  

1. 对文件的操作

  对文件操作一般有两种方式分别是静态方法,和实例方法

  静态方法属于静态类File,实例方法则属于FileInfo

  - 实例方法

```c#
//需要操作的文件的路径为D:\0.code\c#\对文件的操作\temp.txt
FileInfo myFile = new FileInfo("D:\\0.code\\c#\\对文件的操作\\temp.txt");
myFile.CopyTo(@"D:\0.code\c#\对文件的操作\temp1.txt");
//此方法将对象文件复制到指定路径并命名
```



  - 静态方法

```c#
//需要操作的文件的路径为D:\0.code\c#\对文件的操作\temp.txt
File.Copy("D:\\0.code\\c#\\对文件的操作\\temp.txt", @"D:\0.code\c#\对文件的操作\temp1.txt");
```

上文中`"D:\\0.code\\c#\\对文件的操作\\temp.txt"`与`@"D:\0.code\c#\对文件的操作\temp1.txt"`是等效的[^字符串前加@]

2. 对文件夹的操作

  对文件夹的操作同上,也分为静态方法和实例方法

  对文件操作一般有两种方式分别是静态方法,和实例方法

  静态方法属于静态类Directory,实例方法则属于DirectoryInfo

  - 实例方法

```c#
//需要创建的文件夹的路径为D:\0.code\c#\对文件的操作\
//创建的文件夹叫做newfolder
DirectoryInfo myfolder = new DirectoryInfo(@"D:\0.code\c#\对文件的操作\newfolder");
myfolder.Create();
```



  - 静态方法

```c#
//需要创建的文件夹的路径为D:\0.code\c#\对文件的操作\
//创建的文件夹叫做newfolder
Directory.CreateDirectory(@"D:\0.code\c#\对文件的操作\newfolder");
```



3. 路径

  - 绝对路径(完整路径)

​	绝对路径是将要操作的文件路径完整写出,从盘符开始,到文件
​	优点:可以保证读取文件的正确
​	缺点:兼容性极差!

  - 相对路径

	相对路径是以程序执行的路径为准,写一个相对的路径

	相对路径的三种形式:

	```c#
	//以下演示中,均以D:\notes\temp.txt为准
	//同级的文件处于notes文件夹中的-test.txt
	.\test.txt
	//上一级处于D:\中的-test.txt
	..\test.txt
	//下一级处于D:\notes\myFolder中的-test.txt
	.\myFolder\test.txt
	```

4. Filelnfo和DirectoryInfo的常用属性方法

	[常用属性及其方法](.\supplement\Filelnfo和Directorylnfo类常用属性.md)

## 11.DEBUG

### 1.异常

1. **概念**

  > 程序运行中产生的错误，称之为异常
  >
  > 出现异常时，一般会停止运行代码

2. **异常处理**

  > **捕捉异常**
  >
  > ```C#
  > try
  > {
  >     <代码>//可能出现异常的代码
  > }
  > catch(<异常类型> e)
  > {
  >     <代码>//出现异常则执行这个代码
  > }//可以出现多个catch
  > finally{
  >     <代码>//不论是否出现异常，都执行的代码
  > }
  > ```
  >
  > 注意：**如果对异常进行捕捉，则出现异常时，不会中断代码，会继续执行try…catch…finally语句后的代码**
  >
  > **原理：**
  >
  > try后花括号内的代码为可能出现异常的代码，catch会对代码的异常进行捕捉，捕捉到的异常如果与提前声明的异常类型相等则运行catch后花括号的代码
  >
  > finally的作用是不管是否出现异常都会运行的代码
  >
  > **结构**
  >
  > ```C#
  > try
  > 
  > {
  > 
  >     <代码>//可能出现异常的代码
  > }
  > 
  > 
  > finally{
  > 
  >     <代码>//不论是否出现异常，都执行的代码
  > }
  > 
  > 
  > try
  > {
  >     <代码>//可能出现异常的代码
  > }
  > catch(<异常类型> e)
  > {
  >     <代码>//出现异常则执行这个代码
  > }//可以出现多个catch
  > ```
  >
  > 注意：
  >
  > **try…catch…finally`语句中，`catch`和`finally`两个最少存在一个，并且`finally`最多只能有一个**

