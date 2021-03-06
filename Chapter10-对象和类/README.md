# 第10章 对象和类

## 本章内容包括:

- 过程性编程和面向对象编程
- 类概念
- 如何定义和实现类
- 公有类访问和私有类访问
- 类的数据成员
- 类方法（类函数成员）
- 创建和使用类对象
- 类的构造函数和析构函数
- const成员函数
- this指针
- 创建对象数组
- 类作用域
- 抽象数据类型

**总结**：C++所做的最重要的改进是提供了类。本章首先介绍类，将解释抽象、封装、数据隐藏，并演示类是如何实现这些特性的。本章还将讨论如何定义类、如何为类提供公有部分和私有部分以及如何创建使用类数据的成员函数。另外，还将介绍this指针，对于有些类编程而言，它是至关重要的。后面的章节还将讨论扩展到运算符重载（另一种多态）和继承，它们是代码重用的基础。

**Q**：什么叫**面向对象编程**？

**A**：面向对象编程（OOP）是一种特殊的、设计程序的概念性方法，C++通过一些特性改进了C语言，使得应用这种方法更容易。

**Q**：OOP**最重要的特性**有哪些？

**A**： **抽象**、**封装和数据隐藏**、**多态**、**继承**、**代码的可重用性** 。

##  10.1 过程性编程和面向对象编程

**小结**：本小节通过垒球球队的统计数据来说明过程性编程和面向对象编程的概念，并且进行了比较。

**Q**：如何比较**过程性编程**和**面向对象编程**？

**A**：

1）**过程性编程**：采用过程性编程方法时,首先**考虑要遵循的步骤**,然后**考虑如何表示这些数据**(并不需要程序一直运行,用户可能希望能够将数据存储在一个文件中,然后从这个文件中读取数据).

2）**面向对象编程**：采用OOP方法时,首先**从用户的角度考虑对象—描述对象所需的数据以及描述用户与数据交互所需的操作**.完成对**接口的描述**后,需要确定如何**实现接口**和**数据存储**.最后,使用新的设计方案**创建出程序**.

##  10.2 抽象和类

生活中充满复杂性，处理复杂性的方法之一是**简化**和**抽象**。

 抽象是通往用户定义类型的捷径,在C++中,用户定义类型指的是实现抽象接口的类设计. 

### 10.2.1 类型是什么

**小结**：本小节说明了指定基本数据类型完成的工作。

**Q**：指定基本类型完成了哪些工作？

**A**：

1）决定数据对象需要的**内存数量**；

2）决定如何**解释内存中的位**；

3）决定可使用**数据对象执行的操作或方法**。

### 10.2.2 C++中的类

**小结**：本小节介绍了什么是类、类规范的组成、类中接口的概念、类中的访问控制、数据隐藏、封装等。

**程序清单：**

### 程序清单10.1 stock00.h是类声明的helloworld,看懂并会写这个程序,是不是可以说面向对象编程入门了呢?!

**Q**：类的**定义**？

**A**：类是一种**将抽象转换为用户定义类型**的C++工具，它将**数据表示**和**操纵数据的方法**组合成一个整洁的包。

**Q**：**类规范(class specifiication)**由哪些部分组成？

**A**：

1）一般来说,类规范由两个部分组成：**类声明**和**类方法定义**.

2）**类声明**:以**数据成员**的方式描述数据部分,以**成员函数**(被称为方法)的方式描述公有接口.

3）**类方法定义**:描述如何实现类成员函数.

4）简单的说,类声明提供了类的**蓝图**,而方法定义则提供了**细节** 。

**Q**：什么是接口？

**A**：

1）接口是一个**共享框架**，**供两个系统交互时使用**；对于类,我们说**公共接口**;

2）在这里,公众public是使用类的程序,交互系统由类对象组成,而接口由编写类的人提供的方法组成.

3）如果希望更人性化,不要将使用类的程序视为公共用户,而将编写程序的人视为公共用户.

4）然而,要使用某个类,必须了解其公共接口;要编写类,必须创建其公共接口.

**1.访问控制**

**Q**：类是**如何实现**访问控制的？

**A**：通过**关键字**private、public和protected。

**Q**：如何理解类的公有和私有？

**A**：

1）使用类对象的程序都可以直接访问公有部分，但只能通过**公有成员函数**（或**友元函数**，参见第11章）来访问对象的**私有成员**；

2）因此，公有成员函数是程序和对象的私有成员之间的桥梁，提供了对象和程序之间的接口。

**Q**：什么叫**数据隐藏**？

**A**：防止程序直接访问数据被称为**数据隐藏**.私有成员函数的存在就是为了实现数据隐藏的。

**Q**：什么叫**封装**？

**A**：

1）类设计尽可能将**公有接口**与**实现细节**分开；

2）公有接口表示设计的抽象组件；

3）将实现细节放在一起并将他们与抽象分开被称为**封装**.

**OOP和C++**

 C++中包括了许多专门用来实现OOP方法的特性,因此它使程序员更进一步.首先,将数据表示和函数原型放在一个类声明中(而不是放在一个文件中),通过将所有内容放在一个类声明中,来使描述称为一个整体.其次,让数据表示称为私有,使得数据只能被授权的函数访问.

**Q**：为什么要将实现细节从接口设计中分离出来？这样的好处是什么？

**A**：如果以后找到了更好的、实现数据表示或成员函数细节的方法，可以对这些细节进行修改，而无需修改程序接口，这使程序维护起来更容易。

**2.控制对成员的访问：公有还是私有**

**Q**：将成员设置成公有还是私有的**原则**是什么？

**A**：由于**隐藏数据**是OOP主要的目标之一，因此数据项通常放在私有部分，组成类接口的成员函数放在公有部分，如果不将成员函数放在公有部分，则无法从程序中直接调用这些函数。

### 10.2.3 实现类成员函数

***程序清单10.2 stock00.cpp***

程序清单10.1进行了类声明,程序清单10.2进行了类定义(换句话说就是**实现类方法**),两个程序清单密不可分.

**Q**：成员函数定义与常规函数定义的共同点和不同点？

**A**：

**共同点**：它们有函数头和函数体，也可以有返回类型和参数。

**不同点**：

1）定义成员函数时，使用作用域解析运算符（::）来标识函数所属的类。作用域解析运算符确定了方法定义对应的类的身份。如果试图使用非成员函数访问该类的数据成员，编译器禁止这样做(但第11章中将介绍的友元函数例外)；

2）类方法可以访问类的private组件（当然更包括public组件）。

1）决定数据对象需要的内存数量；

2）决定如何解释内存中的位；

3）决定可使用数据对象执行的操作或方法。

1.**成员函数说明**

**小结**：本小节对程序清单10.2 stock00.cpp中的成员函数进行了说明。

2.**内联方法**

**Q**：将类中的成员函数定义为内联函数的**原则**是什么？

**A**：我们将短小的成员函数作为内联函数。

**Q**：将类中的成员函数定义为内联函数的**方法**是什么？

**A**：

1）定义于**类声明中的函数**都将自动成为内联函数；

2）可以在类声明之外定义成员函数，并使其成为内联函数。声明处和一般的成员函数一样，只不过在定义处：开头要加关键字`inline`：

```c++
class Stock
{
private：
	...
	void set_tot(); // definition kept separate
public:
	...
};

inline void Stock::set_tot()	// use inline in definition
{
	total_val = shares * share_val;
}
```

**说明**：一般讲类的内联函数定义在该定义类的**头文件**中。

3.**方法使用哪个对象**

**小结**：本小节主要介绍了如何创建对象、如何通过对象使用成员函数、对象的存储空间有什么特征。

**Q**：如何**创建对象**？

**A**：最简单的方式是声明类变量：

```c++
Stock kata, Joe;
```

**Q**：如何**使用对象的成员函数**？

**A**：和使用结构成员一样，通过成员运算符:

```c++
kata.show();
joe.show();
```

**Q**：**对象**的**存储空间**有什么**特性**？

**A**：所创建的每个新对象都有自己的存储空间，用于存储其**内部变量**和**类成员**；但同一个类的所有对象**共享同一组类方法**，即每种方法只有一个副本。可以看书本图10.2加深理解。

### 10.2.4 使用类

**程序清单10.3 usestock0.cpp**

程序清单10.1为声明类,程序清单10.2为定义类,程序10.3为使用类,3者是有机整体,密不可分,有了这3者才构成了面向对象编程的**helloworld**.

**Q**：C++中使用类的**原则**是什么？

**A**：**简单性**!!!C++的目标是使得使用类与使用基本的内置类型（如int和char）尽可能相同。具体体现为如下几点：

1）要创建类对象，可以声明类变量，也可以使用new为类对象分配内存空间；

2）可以将对象作为函数的参数和返回值，也可以将一个对象赋给另一个；

3）C++提供了一些工具，可用于初始化对象、让cin和cout识别对象，甚至在相似的类对象之间进行自动类型转换。

**Q**：什么叫**客户/服务器模型**？

**A**： 

1)OOP程序员常依照**客户/服务器模型**来讨论程序设计.

2)**客户的定义**:**客户**是**使用类的程序**.

3)**服务器的定义**:类声明(包括类方法)**构成了**服务器**,**它是程序可以使用的资源**.

4)**客户**只能通过以公有方式定义的接口使用服务器,这意味着客户(客户程序员)唯一的责任是**了解该接口**.

5)**服务器**(服务器设计人员)的责任是确保服务器根据该接口可靠并准确地执行.

6)**服务器设计人员**只能修改类设计的实现细节,而**不能修改接口**.

7)这样程序员独立地对客户和服务器进行改进,对服务器的修改不会对客户的行为造成意外的影响.

### 10.2.5 修改实现

本小节相关章节为程序清单8.8和第17章,以后再学该小节的内容吧!

### 10.2.6 小结

本小节小结了类的**基本设计步骤**:**先类声明后类定义**,并且介绍了关于**类的基本概念**,值得反复品读.

## 10.3 类的构造函数和析构函数

**Q**：为什么需要**构造函数**？

**A**：

1）C++的目标之一是让使用类对象就像使用**标准类型**一样，然而，到现在为止，本章提供的代码还不能让您像**初始化**int或结构那样来初始化Stock对象：

```c++
int year = 2001；								// valid initialization
struct thing
{
    char* pn;
    int m;
};
thing amabob = {"wodget", -23};					// valid initialization
Stock hot = {"Sukie's Autos, Inc.", 200, 50.25};// NO! compile error
```

2）常规的初始化语法不适用于类(具体如上面的代码段）。因为**数据部分**的访问状态往往是**私有的**。

**Q**：构造函数**是什么**？

**A**：

1）构造函数是**特殊的**成员函数；

2）构造函数名和类名**一致**；

3）构造函数**没有返回值**；

4）程序声明对象时，将**自动调用**构造函数。

### 10.3.1 声明和定义构造函数

**小结**：本小节2小段代码介绍了**如何声明和定义构造函数**，可以看做声明和定义构造函数的**helloworld**。

**相关章节**：第8章中讲的**默认参数**

**说明**：构造函数的声明位于类的公有部分。

**成员名和参数名**

**声明**：需要注意构造函数的参数与类成员的区别。构造函数的参数表示的不是类成员，而是赋给类成员的值。

### 10.3.2 使用构造函数

**小结**：本小节介绍了**初始化构造函数**的几种方法。这里需要强调的是，正在因为初始化构造函数和一般的成员函数赋值不同，才会介绍如何初始化构造函数！

**相关章节**:第11章中的对象指针。

**Q**：C++提供了哪些方法来使用构造函数来初始化构造函数？

**A**：显示地、隐式地、使用new方式：

```c++
Stock food = Stock("World Cabbage", 250, 1.25);
Stock garment("Furry Mason", 50, 2.5);
Stock *pstock = new Stock("Electroshock Games", 18, 19.0);
```

**Q**：为什么构造函数被用来创建对象，而不能通过对象来调用？

**A**：因为在构造函数构造出对象之前，对象是不存在的。

### 10.3.3 默认构造函数

**小结**：本小节介绍了默认构造函数的定义、程序员提供默认构造函数的必要性、如何定义默认构造函数、调用默认构造函数的3种方法。

**Q**：默认构造函数的**定义**？

**A**：默认构造函数是在未提供显示初始值时，用来创建对象的构造函数，具体语法如下（程序清单10.3就是这么做的）：

```c++
Stock fluffy_the_cat;	// uses the default constructor
```

**Q**：程序员提供默认构造函数有何必要性？

**A**：

1）当且仅当没有定义任何构造函数时，编译器才会提供默认构造函数。为类定义了构造函数后，程序员就必须为它提供默认构造函数；

2）对象本质上也是一种变量。对于变量，初始化很重要，因而对象也不例外，系统提供的默认构造函数所有成员变量赋0，这往往不是我们想要的，因而程序员需要自己写默认构造函数；

3）一般情况下，一个完整的类至少包含程序员提供的默认构造函数和另一个构造函数。

**Q**：**定义**默认构造函数的**方法**有哪几种？

**A**：

1）给已有构造函数的所有参数提供默认值；

2）通过函数重载来定义另一个构造函数——一个没有参数的构造函数；

```c++
Stock(const string & co = "Error", int n = 0, double pr = 0.0);	// 方法(1)
Stock();														// 方法(2)
```

**说明**：由于只能有一个默认构造函数，因此不要同时采用这两种方式；

**声明**：不要被非默认构造函数的隐式所误导：

```c++
//  调用默认结构体的3种方法
Stock first；					// calls default constructor implicitly
Stock first = Stock();			 // calls it explicitly
Stock *prelief = new Stock;		 // calls it implicitly

// 不是调用默认结构体
Stcock first("Concrete Conglomerate"); // calls constructor
Stock second();						   // second()是一个返回Stock对象的函数
```

### 10.3.4 析构函数

**小结**：本小节讲了为什么需要构造函数，如何声明和定义析构函数，何时调用析构函数。

**相关章节**：第12章的“再谈定位new运算符”。

**Q**：**为什么需要**析构函数？

**A**：对象过期时，程序自动调用一个特殊的成员函数，即析构函数，析构函数的存在是为了完成清理工作。

**Q**：如何**声明**和**定义**析构函数？

**A**：

```c++
~Stock();			// 声明析构函数

Stock::~Stock()		// 定义析构函数
{
}
```

**Q**：何时调用析构函数？

**A**：由编译器决定，通常不应在代码中显式地调用析构函数（有关例外情形，请参阅12章的“再谈定位new运算符”）。具体来讲，分为如下几种：静态存储类对象、自动存储对象、通过new创建的、临时对象，具体何时调用析构函数见书籍。

**结论**：一个类必然要有一个析构函数，如果程序员不提供，那么编译器就隐式地声明一个默认析构函数。

### 10.3.5 改进Stock类

**程序清单**：程序清单10.4 stock10.h、10.5 stock10.cpp、10.6 usestock2.cpp添加了关于构造函数的内容，这样面向对象的Helloworld才是规范完整的，因此这3个文件意义重大！！！

**相关章节**：第1章和第9章介绍的多文件程序技术。

1.**头文件** & 2. **实现文件** & 3. **客户文件**

**说明**：

1）头文件声明类，实现文件实现方法的定义，客户文件使用类，这或许是实现OOP最基本的流程吧；

2）学习“3. 客户文件”，有助于理解何时调用析构函数。

4.**程序说明**

**提示**：如果既可以通过初始化，也可以通过赋值来设置对象的值，则应采用初始化方式。通常这种方式的效率更高。

5.**C++11列表初始化**

**小结**：本小节介绍了C++11列表构造函数初始化的方法。

**相关章节**：第16章中C++11的std::initialize_list。

**Q**：在C++11中，可将列表初始化语法用于类吗？

**A**：可以，只要提供与某个构造函数的参数列表匹配的内容，并用大括号将它们括起来：

```c++
Stock hot_tip = {"Derivatives Plus Plus", 100, 45.0};
Stock jock {"Sport Age Storage, Inc"};
Stock temp {};
```

​	说明：在前两个声明中，用大括号括起的列表与下面的构造函数匹配,第三个声明与默认构造函数匹配。

```c++
Stock::Stock(const std::string & co, long n = 0, double pr = 0.0);
```

#### 6. const成员函数

**小结**：本小节介绍了将成员函数定义为const成员函数的原则和方法，原则就是**不修改调用对象的成员函数就定义为cosnt成员函数**。

请看下面的代码段：

```c++
const Stock land = Stock{"Kludgehorn Properties"};
land.show();
```

对于当前的C++来说，编译将拒绝第二行。因为show()的代码无法确保调用对象不被修改，调用对象和const一样，不应被修改。我们以前通过将函数参数声明为const引用或指向const的指针来解决这个问题。但这里存在语法问题：show()方法没有任何参数。相反它所有使用的对象是由方法调用隐式提供的。需要一种新的语法来保证函数不会修改调用对象。C++的解决方法是将const关键字放在函数的括号后面。即，show()声明如下：

```c++
void show() const;	// 类中const成员函数的声明
```

同样，函数定义的开头也应该如下：

```c++
void Stock::show() const  // 类中const成员函数的定义
```

以这种方式声明和定义的类函数被称为**const成员函数**。

**原则**：就像应**尽可能将const引用和指针用作函数形参**一样，只要类方法不修改调用对象，就应该将其声明为const。

### 10.3.6 构造函数和析构函数小结

该小结是10.3节的精华，总结了构造函数、默认构造函数和析构函数的声明、定义、语法以及关于构造函数和默认构造函数的初始化方法，本小结值得仔细品读。

## 10.4 this指针

**小结**：本小节介绍了this指针的**技术背景**（需要使用this指针的原因）、**使用方法**、方法原型中3个不同位置`const`的含义。

**程序清单**：程序清单10.8介绍了使用this指针的方法，需要特别关注`Stock::topval()`成员函数，该成员函数可以看做使用**this指针的Helloworld**。

**相关章节**：第4章的->运算符，通过指针访问结构成员；本小节还使用了引用的概念。

**Q**：this指针的**技术背景**是什么？

**A**：当方法涉及到**2个对象**，在这种情况下需要使用C++的this指针。

**Q**：如何理解如下方法的原型？

```c++
const Stock & topval(const Stock & s) const;
```

**A**：

1）该函数隐式地访问一个对象，而显式地访问另一个对象，并返回其中一个对象的引用；

2）括号中的const表明，该函数不会修改**被显式地访问的对象**；

3）而括号后的const表明，该函数不会修改**被隐式地访问的对象**；

4）由于该函数返回了两个const对象之一的引用，因此返回类型也应为const引用。

**Q**：this指针的**定义**？

**A**：this指针是特殊的指针（本质上就是指针！），this指针指向用来调用成员函数的对象（this被作为隐藏参数传递给方法）。

## 10.5 对象数组

**小结**：本小节介绍了对象数组的**声明**、**初始化**、**使用方法**。

**程序清单**：

1）程序清单10.9介绍了如何声明对象数组并且如何对对象数组进行初始化；

2）该程序清单的功能是找出对象数组中某个成员变量的最大值；

3）与该程序清单关系关系最为密切的就是第10.4节this指针；

4）该程序清单使用了程序清单10.7的头文件和程序清单10.8中的方法文件。

**Q**：如何**定义**对象数组？

**A**：声明对象数组的方法与声明标准类型数组相同：

```c++
Stock mystuff[4]; // creates an array of 4 Stock objects
```

## 10.6 类作用域

**Q**：为什么可以在不同类中使用相同的类成员名而不会引起冲突？

**A**：在类中定义的名称（如类数据成员名和类成员函数名）的作用域都为整个类，作用域为整个类的名称只在该类中是已知的，在类外是不可知的。因此，可以在不同类中使用相同的类成员名而不会引起冲突。

### 10.6.1 作用域为类的常量

**小结**：本小节介绍了作用域为类的常量的**技术背景**（即为什么需要有作用域为类的常量）、如何正确的创建所有对象共享的常量。

**Q**：创建作用域为类的常量错误和正确做法？

**A**：

1）错误做法:声明类只是描述了对象的形式,并没有创建对象。因此，在创建对象前，将没有用于存储值的空间。

```c++
class Bakery{
private：
	const int Months = 12；	// declare a constant? FAILS
    double costs[Months];
    ...
}
```

2）正确做法1：在类中声明一个枚举。在类声明中声明的枚举的作用域为整个类，因此可以用枚举为整型常量提供作用域为整个类的符号名称。

3）正确做法2：使用关键字`static`。该常量将与其他静态变量存储在一起，而不是存储在对象中。因此，只有一个Months常量，被所用Bakery对象共享。第12章将深入介绍静态类成员。

```c++
class Bakery{
private:
	static const int Months = 12;
	double costs[Months];
	...
}
```

### 10.6.2 作用域内枚举（C++11）

**小结**：

1）本小节介绍了作用域内枚举（C++11）的技术背景；

2）常规枚举可以自动转换为整型，但作用域内枚举不能隐式地转换为整型；

3）不过，作用域内枚举可以显式地转换为整型。

**Q**：作用域内枚举（C++11）的技术背景是什么？

**A**：传统的枚举存在一些问题，其中之一是两个枚举定义中的枚举量可能发生冲突，因而需要作用域内枚举（C++11）。

## 10.7 抽象数据类型

**小结**：本小节基于类并以栈为例说明如何声明、定义、使用抽象数据类型。

**程序清单**：程序清单10.10 stack.h、10.11 stack.cpp、10.12 stacker.cpp分别对应栈的声明、定义、使用。

**相关章节**：使用第14章的**类模板**知识可以简化这里的程序清单代码。

**Q**:栈的定义?

**A**:具体见书本.

## 10.8 总结

**小结**：本小节对本章的内容大体按照本章的目录顺序进行总结，值得反复品读。