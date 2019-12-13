**基础**

1. 面向过程和面向对象的区别?
  
- 面向过程：可以理解为对于一个机器的具体工作的内容，步骤。过程繁琐，维护比较困难。
- 面向对象：可以理解为你对这个操作这个机器的调用者。具有封装，继承，多态的特性。所以设计的系统具有低耦合性。
2. Java 语言有哪些特点？
	面向对象 ， （封装，继承，多态），跨平台（Java虚拟机）
3. 如何理解JVM JDK 和 JRE ？
	Java虚拟机 是运行在Java 字节码的虚拟机。JVM有针对不同系统的特定实现（windows，linux ，macOS），目的是使用相同的字节码。
   什么是字节码？如何理解？
	在Java中，jvm可以理解的代码叫做字节码（及.class 文件），它不面向任何特定的处理器，只面对虚拟机。

   JDK 和 JRE 
	JDK 意义为Java Development kit ，包括了JRE的包，还有编译器javac，能够编译程序。
	
	JRE 开发环境，运行Java程序，平常的开发就是需要这个JRE.

4. Java和C++ 的区别？
	都是面向对象的语言，都是支持继承，封装，多态。
	
	区别在于，指针内存处理方面。Java无需手动释放内存，且没有指针，直接访问。

5.字符型常量和字符串常量的区别？

6. 构造器Constructor 是否可被override？
   	
7. 重载和重写的区别
	重载的定义是方法名相同，参数类型不同，个数不同，顺序不同。方法返回值和修饰符也可以不同。
	
	重写的定义是必须要有继承，子类的方法重新写方法，但是方法名和参数是一致性的。访问的修饰符，必须大于父类的。而且private不能被重写。

8.  Java 面向对象编程的三大特性：封装，继承，多态
	- 封装
	- 继承
	- 多态
9. String StringBuffer 和 StringBuilder的区别是？
	
10. 自动装箱与拆箱


11. 接口和抽象类的区别是什么？
	 接口类中不能有实现方法，但是抽象类可以有实现方法。
	
	 一个类可以实现多个接口，但是只能实现一个抽象类

	从设计层面来说，抽象是一个对象，而接口是提供可用的一个规范。

12. 成员变量和局部变量的区别有那些？
	范围上：成员变量定义在类中方法外。
	初始化上：成员变量是有初始值，
	存在时间上：成员变量是对象的一部分，随着对象创建而存在，而局部变量随着方法的调用而消失。

13. **== 和 equals 的区别？**
	== 比较是的两个对象的地址是否相等。（基本数据类型 == 比较的是值， 引用数据类型 == 比较的是内存地址）
	
	equals ： 它的作用时判断两个对象是否相等。
	- 没有覆盖equals 方法，比较同`==` 一样
	- 覆盖了equals 方法。比较的是内容是否相等。hashcode也相等
	`` public class test1 {
    public static void main(String[] args) {
        String a = new String("ab"); // a 为一个引用
        String b = new String("ab"); // b为另一个引用,对象的内容一样
        String aa = "ab"; // 放在常量池中
        String bb = "ab"; // 从常量池中查找
        if (aa == bb) // true
            System.out.println("aa==bb");
        if (a == b) // false，非同一对象
            System.out.println("a==b");
        if (a.equals(b)) // true
            System.out.println("aEQb");
        if (42 == 42.0) { // true
            System.out.println("true");
        }
    }
	} ``

14 hashCode 与equals ？

  HashCode：hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位	置。hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode() 函数。
	散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！（可以快速找到所需要的对象）

	为什么有hashcode？
      我们先以“HashSet 如何检查重复”为例子来说明为什么要有 hashCode： 当你把对象加入 HashSet 时，HashSet 会先计算对象的 hashcode 值来判断对象加入的位置，同时也会与其他已经加入的对象的 hashcode 值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同 hashcode 值的对象，这时会调用 equals()方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。（摘自我的Java启蒙书《Head first java》第二版）。这样我们就大大减少了 equals 的次数，相应就大大提高了执行速度
		
	  **防止现在出现一夫多妻的现象，由于set 是key-value 的方式，所以每个hashcode都不能重复。即hashcode相等的说明是一个对象。**
	
hashCode（）与equals（）的相关规定
	如果两个对象相等，则hashcode一定也是相同的
	两个对象相等,对两个对象分别调用equals方法都返回true
	两个对象有相同的hashcode值，它们也不一定是相等的
	因此，equals 方法被覆盖过，则 hashCode 方法也必须被覆盖
	hashCode() 的默认行为是对堆上的对象产生独特值。如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）