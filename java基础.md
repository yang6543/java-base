<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-generate-toc again -->
**Table of Contents**


   * [Java语言特性](#Java语言特性)
      * [1 Java方法的重载](#1-Java方法的重载)
      * [2 ArrayList](#2-ArrayList)
      * [3 面向对象](#3-面向对象)
      * [4 多态](#4-多态)
   * [编程题](#编程题)
      * [1 水仙花练习功能实现](#1-水仙花练习功能实现)
      * [2 99乘法表](#2-99乘法表)
      * [3 数组逆序](#3-数组逆序)
      * [4 选择排序](#4-选择排序)
      * [5 冒泡排序](#5-冒泡排序)
      * [6 数组的折半查找](#6-数组的折半查找)

<!-- markdown-toc end -->





# Java语言特性

## 1 Java方法的重载

  - A: 方法的重载
      - 在同一个类中，方法名相同，参数列表不同。与返回值类型无关。
    
      - 参数列表不同：
        - A:参数个数不同
        - B:参数类型不同
        - C:参数的顺序不同(算重载,但是在开发中不用)

  * B: 案例代码
    ```java
    public static int getSum(int a,int b){
      System.out.println("两个int参数");
      return a+b;
    }
    public static int getSum(int a,int b,int c){
      System.out.println("三个int参数");
      return a+b+c;
    }
    public static double getSum(double a,double b){
      System.out.println("两个double参数");
      return a+b;
    }
    ```

  * 注：方法重载注意事项
      * a: 参数列表必须不同
      * b: 重载和参数变量名无关
      * c: 重载和返回值类型无关
      * d: 重载和修饰符无关
      * e: 技巧: 重载看方法名和参数列表
  
## 2 ArrayList

  * A: ArrayList创建变量
    * a: 导入包 java.util包中
    * b: 创建引用类型的变量
      数据类型<集合存储的数据类型>  变量名 = new 数据类型<集合存储的数据类型>();  
      集合存储的数据类型: 要将数据存储到集合的容器中创建集合引用变量的时候,必须要指定好,存储的类型是什么
    * c: 变量名.方法 
        注意: 集合存储的数据,8个基本类型对应8个引用类型
      存储引用类型,不存储基本类型

    基本数据类型|对应的引用数据类型表示形式
    :-:|:-:|:-:
    byte|Byte
    short|Short
    Int|Integer
    long|Long
    float|Float
    double|Double
    char|Character
    boolean|Boolean

  * B: ArrayList创建变量的示例代码
    ```java
    import java.util.ArrayList;
    public class ArrayListDemo{
      public static void main(String[] args){
        //创建集合容器,指定存储的数据类型
        //存储字符串
        ArrayList<String> array = new ArrayList<String>();
        
        //创建集合容器,存储整数
        ArrayList<Integer> array2 = new ArrayList<Integer>();
        
        //创建集合容器,存储手机类型
        ArrayList<Phone> array3 = new ArrayList<Phone>();
      }
    }
    ```

  * C: ArrayList的常见方法
    * a: add(参数) 向集合中添加元素
    * b: get(int index) 取出集合中的元素,get方法的参数,写入索引
    * c: size() 返回集合的长度, 集合存储元素的个数
    * d: add(int 索引,存储的元素)  将元素添加到指定的索引上
    * e: set(int 索引,修改后的元素)   将指定索引的元素,进行修改
    * f: remove(int 索引)       删除指定索引上的元素
    * g: clear()          清空集合中的所有元素
  * D: 案例代码
    ```java
    import java.util.ArrayList;
    public class ArrayListDemo_1{
      public static void main(String[] args){
        //定义集合,存储字符串元素
        ArrayList<String> array = new ArrayList<String>();
        //调用集合方法add存储元素
        array.add("abc");
        array.add("itcast");
        array.add("love");
        array.add("java");
        //输出集合的长度,调用集合方法size, size方法的返回值类型 int
        int size = array.size();
        System.out.println(size);
        
        //获取出集合中的一个元素,获取1索引的元素
        //集合的方法get, 获取元素后结果数据类型
        String s = array.get(1);
        System.out.println(s);

        //在索引2上,添加元素7
        array.add(2,7);
        
        //将0索引上的元素,修改成10
        array.set(0,10);
        
        //将4索引上的元素,删除
        array.remove(4);
        
        array.clear();
        
        
        System.out.println(array.get(0));
        System.out.println(array.get(1));
        System.out.println(array.get(2));
        System.out.println(array.get(3));
      }
    }
    ```

## 3 面向对象

  * 成员变量和局部变量区别
    - a.定义位置上的区别
      - 1.成员变量，定义在类中，方法外
      - 2.局部变量，定义在方法内，语句内({})
    
    - b.作用域不同
      - 1.成员变量，作用于整个类中
      - 2.局部变量，作用于方法内，语句内
    
    - c.默认值不同
      - 1.成员变量，有自己的默认值
      - 2.局部变量，没有默认值，且不赋值不能使用
    
    - d.内存位置不同
      - 1.成员变量，跟随对象进入堆内存存储
      - 2.局部变量，跟随方法，语句进入栈内存
    
    - e.生命周期不同
      - 1.成员变量，跟随对象，在堆中存储，等待JVM清理(生命周期相对较长)
      - 2.局部变量，跟随方法，方法出栈就消失(生命周期相对较短)
  
  * A.面向对象三大特征
    * 封装、继承、多态
  * B.封装表现
    * 1、方法就是一个最基本封装体
    * 2、类其实也是一个封装体  
  * C.封装的好处
    * 1、提高了代码的复用性
    * 2、隐藏了实现细节，还要对外提供可以访问的方式。便于调用者的使用。这是核心之一，也可以理解为就是封装的概念
    * 3、提高了安全性   
  
    - private概述
      - private可以修饰成员内容包括成员方法和成员变量，不能修饰局部变量
      - 被private修饰的内容不能在其他类访问
    - C.完整代码 
      ```java
      class Person {
        private int age;
        private String name;
      
        public void show() {
          System.out.println("age=" + age + ",name" + name);
        }
      }
      ```

    * get和set方法
    * 年龄已被私有，错误的值无法赋值，可是正确的值也赋值不了，这样还是不行，那肿么办呢？按照之前所学习的封装的原理，隐藏后，还需要提供访问方式。只要对外提供可以访问的方法，让其他程序访问这些方法。同时在方法中可以对数据进行验证。
一般对成员属性的访问动作：赋值(设置 set)，取值(获取 get)，因此对私有的变量访问的方式可以提供对应的 setXxx或者getXxx的方法。
    class Person {
      // 私有成员变量
      private int age;
      private String name;
    
      // 对外提供设置成员变量的方法
      public void setAge(int a) {
        // 由于是设置成员变量的值，这里可以加入数据的验证
        if (a < 0 || a > 130) {
          System.out.println(a + "不符合年龄的数据范围");
          return;
        }
        age = a; 
      }
    
      // 对外提供访问成员变量的方法
      public void getAge() {
        return age;
      }
    }
    * 总结
      * 类中不需要对外提供的内容都私有化，包括属性和方法。
以后再描述事物，属性都私有化，并提供setXxx getXxx方法对其进行访问
    * 注意
      * 私有仅仅是封装的体现形式而已
    
    * 当类中存在成员变量和局部变量同名的时候为了区分，就需要使用this关键字
      * this关键字：表示哪个对象调用，就是哪个对象

  * 继承
    *A:继承的概念
      *a:继承描述的是事物之间的所属关系，通过继承可以使多种事物之间形成一种关系体系
        *b:在Java中，类的继承是指在一个现有类的基础上去构建一个新的类，
            构建出来的新类被称作子类，现有类被称作父类
      *B:继承关系的子类特点  
        *a:子类会自动拥有父类所有非private修饰的属性和方法

    *C:继承的好处：
        *1、继承的出现提高了代码的复用性，提高软件开发效率。
        *2、继承的出现让类与类之间产生了关系，提供了多态的前提。(父类有多个子类继承，从而父类就有了多态)

    *D:继承的注意事项 
     *a:在Java中，类只支持单继承，不允许多继承，也就是说一个类只能有一个直接父类，例如下面这种情况是不合法的。
         class A{} 
         class B{}
         class C extends A,B{}  // C类不可以同时继承A类和B类
      假如支持多继承例如:
      ```java
         class A{
          int a=3;
            public void method(){

            }
         } 
         class B{
          int a=5;
          public void method(){

          }
         }
         class C extends A,B{
                
         } 
         class Demo{
          public static void main(String[] args){
            C c=new C();
            System.out.println(c.a);//到底是调用A的还是B的成员变量??无法确定
            c.method();//到底是调用A的还是B的成员方法??无法确定
          } 
         }
         ```
     
        *b:多个类可以继承一个父类，例如下面这种情况是允许的(就像你爹可以多个儿子,但是这些儿子都只有一个爹)
         class A{}
         class B extends A{}
         class C extends A{}   // 类B和类C都可以继承类A
    
       *c:在Java中，多层继承是可以的，
          即一个类的父类可以再去继承另外的父类，
          例如C类继承自B类，而B类又可以去继承A类，这时，C类也可称作A类的子类。下面这种情况是允许的。
         class A{}
         class B extends A{}   // 类B继承类A，类B是类A的子类
         class C extends B{}   // 类C继承类B，类C是类B的子类，同时也是类A的子类
      
          *d:在Java中，子类和父类是一种相对概念，
            也就是说一个类是某个类父类的同时，也可以是另一个类的子类。
            例如上面的这种情况中，B类是A类的子类，同时又是C类的父类。

    *E:继承后子类父类成员变量的特点
     a:子类的对象调用成员变量的时候,子类自己有,使用子类,子类自己没有调用的父类
     ```java
       class Fu{
        //Fu中的成员变量。
        int num = 5;
      }
      
      class Zi extends Fu{
        //Zi中的成员变量
        int num2 = 6;
        //Zi中的成员方法
        public void show()
        {
          //访问父类中的num
          System.out.println("Fu num="+num);
          //访问子类中的num2
          System.out.println("Zi num2="+num2);
        }
      }
      
      class Demo{
        public static void main(String[] args) 
        {
          Zi z = new Zi(); //创建子类对象
          z.show(); //调用子类中的show方法
        }
      }
      ```
     b:当子父类中出现了同名成员变量
     ```java
    class Fu{
      //Fu中的成员变量。
      int num = 5;
    }
    
    class Zi extends Fu{
      //Zi中的成员变量
      int num = 6;
      void show(){   
        //子类的局部变量
        int num=7
        
        //直接访问,遵循就近查找原则
                System.out.println(num);//7
        
        //子父类中出现了同名的成员变量时
        //在子类中需要访问父类中非私有成员变量时，需要使用super关键字
        //访问父类中的num
        System.out.println("Fu num="+super.num);//5
        

        //访问子类中的num2
        System.out.println("Zi num2="+this.num);//6
      }
    }
    
    class Demo5 {
      public static void main(String[] args) 
      {
        Zi z = new Zi(); //创建子类对象
        z.show(); //调用子类中的show方法
      }
    }
    ```

    F:继承后子类父类成员方法的特性
    a:子类的对象调用方法的时候,子类自己有,使用子类,子类自己没有调用的父类
    ```java
      class Fu{
      public void show(){
        System.out.println("Fu类中的show方法执行");
      }
    }
    class Zi extends Fu{
      public void show2(){
        System.out.println("Zi类中的show2方法执行");
      }
    }
    public  class Test{
      public static void main(String[] args) {
        Zi z = new Zi();
        z.show(); //子类中没有show方法，但是可以找到父类方法去执行
        z.show2();
      }
    }
    ```  
     
     b:为什么要有重写?
     ```java
         class Fu{
          public void method(){
            //上千行代码
                //Fu类中的方法最先存在,那么如果项目需求变了,该方法
                //功能不能够满足我们的需求,此时我们也不会去改这个方法
                //因为项目中可能有大量的功能已经使用到该方法,如果随意修改可能使调用该方法的功能出现问题
                //所以使用重写方式基于原有功能提供更强的功能
          }   
         }
         class Zi extends Fu{
          
         }
         ```
     c:子类中出现与父类一模一样的方法时，会出现覆盖操作，也称为override重写、复写或者覆盖。  
     重载：同一个类中，方法名一样，参数列表不同。

     ```java
       class Fu{
      public void show(){
        System.out.println("Fu show");
      }
       }
     
     class Zi extends Fu{
      //子类复写了父类的show方法
      public void show(){
        System.out.println("Zi show");
      }
    }
       public  class Test{
      public static void main(String[] args) {
        Zi z = new Zi();
        z.show(); //Zi show 子类有直接使用子类
      }
    }
    ```

    G:方法覆盖的注意事项 
    a:权限:子类方法覆盖父类方法，必须要保证权限大于等于父类权限。
      四大权限:public>默认(default,前面不写修饰符)=protected>private
     
     class Fu{  
      void show(){

      }
      public void method(){

      }
      }
      class Zi() extends Fu{
      public void show(){//编译运行没问题

      }  
      void method(){//编译错误

        }     
      }
   b:方法定义:子类方法和要重写的父类的方法:方法的方法名和参数列表都要一样。
     关于方法的返回值:
       如果是基本数据类型,子类的方法和重写的父类的方法返回值类型必须相同
       如果是引用数据类型,子类的方法和重写的父类的方法返回值类型可以相同或者子类方法的返回值类型是父类方法返回值类型的子类
       class Fu{  
      int show(){

      }
      public Fu method(){

      }
      
      public Fu method2(){

      }
      
      }
      class Zi() extends Fu{
      public int show(){//返回值为基本类型的重写

      }  
      public Fu method(){//子类的方法和重写的父类的方法返回值类型可以相同

        }     
        public Zi method2(){//子类方法的返回值类型是父类方法返回值类型的子类

        }     
      }
     c:重载与重写对比:
        重载:
        权限修饰符(public private 默认):无关
        方法名:重载的两个方法的方法名必须相同
        形参列表:
          形参类型的顺序不同
          形参的个数不同
          形参的类型不同
          三者至少满足一个
        返回值类型:
          重载与返回值类型无关
    重写:
        权限修饰符(public private 默认): 
          子类方法的权限>=父类的方法的权限
        方法名: 
          子类方法和父类方法必须相同
        形参列表: 
           子类方法和父类方法的形参列表必须相同
        返回值类型:
          基本类数据类型:
            必须相同
          引用数据类型:
           子类方法的返回值类型和父类方法的返回值类型相同
           或者
           子类方法的返回值类型是父类方法的返回值类型的子类

    * 抽象类产生
      A:抽象类的产生
        a:分析事物时，发现了共性内容，就出现向上抽取。会有这样一种特殊情况，就是方法功能声明相同，但方法功能主体不同。那么这时也可以抽取，但只抽取方法声明，不抽取方法主体。那么此方法就是一个抽象方法。
    * 抽象类格式
      A:抽象方法定义的格式：
     a:public abstract 返回值类型 方法名(参数);
       抽象类定义的格式：
       ```java
     abstract class 类名 {
      
      }
      b:抽象类示例代码：
       /*
       *  定义类开发工程师类
       *    EE开发工程师 :  工作
       *    Android开发工程师 : 工作
       *    
       *    根据共性进行抽取,然后形成一个父类Develop
       *    定义方法,工作: 怎么工作,具体干什么呀
       *    
       *    抽象类,不能实例化对象, 不能new的
       *    不能创建对象的原因:  如果真的让你new了, 对象.调用抽象方法,抽象方法没有主体,根本就不能运行
       *    抽象类使用: 定义类继承抽象类,将抽象方法进行重写,创建子类的对象
       */
      public abstract class Develop {
         //定义方法工作方法,但是怎么工作,说不清楚了,讲不明白
        //就不说, 方法没有主体的方法,必须使用关键字abstract修饰
        //抽象的方法,必须存在于抽象的类中,类也必须用abstract修饰
        public abstract void work();
      }
      ```
    * 使用形式
      A:抽象类的使用方式
   /*
   *  定义类,JavaEE的开发人员
   *  继承抽象类Develop,重写抽象的方法
   */
   ```java
  public class JavaEE extends Develop{
    //重写父类的抽象方法
    //去掉abstract修饰符,加上方法主体
    public void work(){
      System.out.println("JavaEE工程师在开发B/S 软件");
    }
  }

  /*
   *  测试抽象类
   *    创建他的子类的对象,使用子类的对象调用方法
   */
  public class Test {
    public static void main(String[] args) {
       JavaEE ee = new JavaEE();
       ee.work();//"JavaEE工程师在开发B/S 软件"
    }
  }
  ```
    * 抽象类特点
      A:抽象类的特点
    a:抽象类和抽象方法都需要被abstract修饰。抽象方法一定要定义在抽象类中。
    b:抽象类不可以直接创建对象，原因：调用抽象方法没有意义。
    c:只有覆盖了抽象类中所有的抽象方法后，其子类才可以创建对象。否则该子类还是一个抽象类。
    之所以继承抽象类，更多的是在思想，是面对共性类型操作会更简单。
    ```java
      abstract class A{
        public abstract void func();
        public abstract void func2();
      }
      class A2 extends A{//A2把A中的两个抽象方法都重写掉了
                         //A2类不再是抽象类
         public void func(){}
         public void func2(){}
      }

      abstract class A3 extends A{//含有抽象方法的类一定是抽象类
         public void func(){

         }
         //public abstract void func2();//func2相当于被继承下来
      }
      ```

  * 接口
    * A:接口的概念
      接口是功能的集合，同样可看做是一种数据类型，是比抽象类更为抽象的”类”。
    接口只描述所应该具备的方法，并没有具体实现，具体的实现由接口的实现类(相当于接口的子类)来完成。这样将功能的定义与实现分离，优化了程序设计。
    请记住：一切事物均有功能，即一切事物均有接口。

    * B: 接口的定义
      与定义类的class不同，接口定义时需要使用interface关键字。
      定义接口所在的仍为.java文件，虽然声明时使用的为interface关键字的编译后仍然会产生.class文件。这点可以让我们将接口看做是一种只包含了功能声明的特殊类。
             
    * C : 定义格式
    ```java
      public interface 接口名 {
        抽象方法1;
        抽象方法2;
        抽象方法3;
      }
    ```

    * D: 定义步骤
      使用interface代替了原来的class，其他步骤与定义类相同：
      接口中的方法均为公共访问的抽象方法
      接口中无法定义普通的成员变量，只能定义常量

  * 接口的实现
    * A: 类与接口的关系
      类与接口的关系为实现关系，即类实现接口。实现的动作类似`继承`，只是关键字不同，实现使用implements。
      其他类(实现类)实现接口后，就相当于声明：”我应该具备这个接口中的功能”。实现类仍然需要重写方法以实现具体的功能。
    * B: 类实现接口的格式
    ```java
      class 类 implements 接口 {
        重写接口中方法
      }
    ``` 
    * C:注意事项
      在类实现接口后，该类就会将接口中的抽象方法继承过来，此时该类需要重写该抽象方法，完成具体的逻辑。
      接口中定义功能，当需要具有该功能时，可以让类实现该接口，只声明了应该具备该方法，是功能的声明。
      在具体实现类中重写方法，实现功能，是方法的具体实现。

  * 接口的成员变量
    * A:成员变量特点
     * a 接口中可以定义变量，但是变量必须有固定的修饰符修饰，public static final 所以接口中的变量也称之为常量，其值不能改变。

    * B:案例
    ```java
      interface Demo { ///定义一个名称为Demo的接口。
        public static final int NUM = 3;// NUM的值不能改变
      }
    ```

  * 接口中成员方法特点
    * A: 成员方法特点
      * a 接口中可以定义方法，方法也有固定的修饰符，public abstract
      * b 子类必须覆盖掉接口中所有的抽象方法后，子类才可以实例化。否则子类是一个抽象类。

    * B: 案例
    ```java
      interface Demo { ///定义一个名称为Demo的接口。
        public abstract void show1();
        public abstract void show2();
      }
      
      //定义子类去覆盖接口中的方法。类与接口之间的关系是 实现。通过 关键字 implements
      class DemoImpl implements Demo { //子类实现Demo接口。
        //重写接口中的方法。
        public void show1(){}
        public void show2(){}
      }
    ```

  * 类和接口的多实现
    * A：接口的多实现
    了解了接口的特点后，那么想想为什么要定义接口，使用抽象类描述也没有问题，接口到底有啥用呢？
    接口最重要的体现：`解决多继承的弊端`。将多继承这种机制在java中通过多实现完成了。
    
    * B：多实现的优点
    * 怎么解决多继承的弊端呢？
    * 弊端：多继承时，当多个父类中有相同功能时，子类调用会产生不确定性。
    * 其实核心原因就是在于多继承父类中功能(方法)有主体，而导致调用运行时，不确定运行哪个主体内容。
    * 为什么多实现能解决了呢？
    * 因为接口中的功能都没有方法体，由子类来明确。

    * C：案例演示
    ```java
    interface Fu1{
      void show1();
    }
    interface Fu2{
      void show2();
    }
    class Zi implements Fu1,Fu2 {    // 多实现。同时实现多个接口。
      public void show1(){}
      public void show2(){}
    }

    interface Fu1{
      int show1();
    }
    interface Fu2{
      void show1();
    }
    //  若出现接口的(show1)方法名相同，参数列表相同，返回值类型不同这类情况，只能放弃其中一个接口。无法重写两个方法。
    ```

  * 类在继承类的同时实现多接口
    * A: 继承的同时实现接口
    * 接口和类之间可以通过实现产生关系，同时也学习了类与类之间可以通过继承产生关系。当一个类已经继承了一个父类，它又需要扩展额外的功能，这时接口就派上用场了。
    * 子类通过继承父类扩展功能，通过继承扩展的功能都是子类应该具备的基础功能。如果子类想要继续扩展其他类中的功能呢？这时通过实现接口来完成。
    * 接口的出现避免了单继承的局限性。父类中定义的事物的基本功能。接口中定义的事物的扩展功能。
    
    * B: 代码演示
    ```java
    class Fu {
      public void show(){}
    }
    interface Inter {
      pulbic abstract void show1();
    }
    class Zi extends Fu implements Inter {
      public void show1() {
      }
    }
    ```

    接口的出现避免了单继承的局限性。父类中定义的事物的基本功能。接口中定义的事物的扩展功能。

  * 接口的多继承
    * A: 接口的多继承
    * 学习类的时候，知道类与类之间可以通过继承产生关系，接口和类之间可以通过实现产生关系，那么接口与接口之间会有什么关系。
    * 多个接口之间可以使用extends进行继承。
    * Java有多继承吗？
      类与类之间没有多继承
      接口之间有多继承
    
    * B 代码演示
    ```java
    interface Fu1{
      void show();
    }
    interface Fu2{
      void show1();
    }
    interface Fu3{
      void show2();
    }
    interface Zi extends Fu1,Fu2,Fu3{
      void show3();
    }
    ```
    
    在开发中如果多个接口中存在相同方法，这时若有个类实现了这些接口，那么就要实现接口中的方法，由于接口中的方法是抽象方法，子类实现后也不会发生调用的不确定性。

  * 接口思想
    * A:接口的思想
    * 前面学习了接口的代码体现，现在来学习接口的思想，接下里从生活中的例子进行说明。
    * 举例：我们都知道电脑上留有很多个插口，而这些插口可以插入相应的设备，这些设备为什么能插在上面呢？
    * 主要原因是这些设备在生产的时候符合了这个插口的使用规则，否则将无法插入接口中，更无法使用。发现这个插口的出现让我们使用更多的设备。
  
    * B: 接口的好处  
    * 总结：接口在开发中的好处
    * 1、接口的出现扩展了功能。
    * 2、接口其实就是暴漏出来的规则。
    * 3、接口的出现降低了耦合性，即设备与设备之间实现了解耦。
    
    * 接口的出现方便后期使用和维护，一方是在使用接口（如电脑），一方在实现接口（插在插口上的设备）。例如：笔记本使用这个规则（接口），电脑外围设备实现这个规则（接口）。
  
  * 接口和抽象类区别
    * A: 明白了接口思想和接口的用法后，接口和抽象类的区别是什么呢？接口在生活体现也基本掌握，那在程序中接口是如何体现的呢？
    通过实例进行分析和代码演示抽象类和接口的用法。
    * B: 举例：
      * 犬：
        行为：
        吼叫；
        吃饭；
      * 缉毒犬：
        行为：
        吼叫；
        吃饭；
        缉毒；
  
    * C:思考：
    * 由于犬分为很多种类，他们吼叫和吃饭的方式不一样，在描述的时候不能具体化，也就是吼叫和吃饭的行为不能明确。
    * 当描述行为时，行为的具体动作不能明确，这时，可以将这个行为写为抽象行为，那么这个类也就是抽象类。
    * 可是当缉毒犬有其他额外功能时，而这个功能并不在这个事物的体系中。这时可以让缉毒犬具备犬科自身特点的同时也有其他额外功能，可以将这个额外功能定义接口中。

    * D: 代码演示
    ```java
    interface 缉毒{
      public abstract void 缉毒();
    }
    //定义犬科的这个提醒的共性功能
    abstract class 犬科{
    public abstract void 吃饭();
    public abstract void 吼叫();
    }
    // 缉毒犬属于犬科一种，让其继承犬科，获取的犬科的特性，
    //由于缉毒犬具有缉毒功能，那么它只要实现缉毒接口即可，这样即保证缉毒犬具备犬科的特性，也拥有了缉毒的功能
    class 缉毒犬 extends 犬科 implements 缉毒{
    
      public void 缉毒() {
      }
      void 吃饭() {
      }
      void 吼叫() {
      }
    }
    class 缉毒猪 implements 缉毒{
      public void 缉毒() {
      }
    }
    ```

    * E: 接口和抽象类区别总结
    相同点:
      都位于继承的顶端,用于被其他类实现或继承;
      都不能直接实例化对象;
      都包含抽象方法,其子类都必须重写这些抽象方法;
    区别:
      抽象类为部分方法(可以不是抽象方法)提供实现,避免子类重复实现这些方法,提高代码复用性;接口只能包含抽象方法;
      一个类只能继承一个直接父类(可能是抽象类),却可以实现多个接口;(接口弥补了Java的单继承)
      抽象类是这个事物中应该具备的基本内容, 继承体系是一种 is..a关系
      接口是这个事物中的额外内容,继承体系是一种 like..a关系
    
    二者的选用:
      优先选用接口,尽量少用抽象类;
      需要定义子类的行为,又要为子类提供共性功能时才选用抽象类;

## 4 多态
    * A: 多态概述
    多态是继封装、继承之后，面向对象的第三大特性。
    现实事物经常会体现出多种形态，如学生，学生是人的一种，则一个具体的同学张三既是学生也是人，即出现两种形态。 
    Java作为面向对象的语言，同样可以描述一个事物的多种形态。如Student类继承了Person类，一个Student的对象便既是Student，又是Person。
    Java中多态的代码体现在一个子类对象(实现类对象)既可以给这个子类(实现类对象)引用变量赋值，又可以给这个子类(实现类对象)的父类(接口)变量赋值。
    如Student类可以为Person类的子类。那么一个Student对象既可以赋值给一个Student类型的引用，也可以赋值给一个Person类型的引用。
    最终多态体现为父类引用变量可以指向子类对象。
    多态的前提是必须有子父类关系或者类实现接口关系，否则无法完成多态。
    在使用多态后的父类引用变量调用方法时，会调用子类重写后的方法。

    * B:多态的定义格式：就是父类的引用变量指向子类对象
       父类类型  变量名 = new 子类类型();
       变量名.方法名();
    
    * C: 普通类多态定义的格式
      父类 变量名 = new 子类();
      举例： 
      ```java
        class Fu {}
        class Zi extends Fu {}
        //类的多态使用
        Fu f = new Zi();
      ```
    * D: 抽象类多态定义格式      
      抽象类 变量名 = new 抽象类子类();
      举例： 
      ```java
      abstract class Fu {
               public abstract void method();
             }
      class Zi extends Fu {
      public void method(){
                System.out.println(“重写父类抽象方法”);
      }
      }
      //类的多态使用
      Fu fu= new Zi();
      ```
    * E: 接口多态定义的格式
      接口 变量名 = new 接口实现类();
      ```java
      interface Fu {
               public abstract void method();
      }
      class Zi implements Fu {
               public void method(){
                    System.out.println(“重写接口抽象方法”);
      }
      }
      //接口的多态使用
      Fu fu = new Zi();
      ```
    * F: 注意事项
      同一个父类的方法会被不同的子类重写。在调用方法时，调用的为各个子类重写后的方法。
      如 Person p1 = new Student();
         Person p2 = new Teacher();
         p1.work(); //p1会调用Student类中重写的work方法
         p2.work(); //p2会调用Teacher类中重写的work方法
      当变量名指向不同的子类对象时，由于每个子类重写父类方法的内容不同，所以会调用不同的方法。

    * G：多态成员特点
      * A: 多态成员变量
    当子父类中出现同名的成员变量时，多态调用该变量时：
    编译时期：参考的是引用型变量所属的类中是否有被调用的成员变量。没有，编译失败。
    运行时期：也是调用引用型变量所属的类中的成员变量。
    简单记：编译和运行都参考等号的左边。编译运行看左边。
      * B: 多态成员方法
    编译时期：参考引用变量所属的类，如果没有类中没有调用的方法，编译失败。
    运行时期：参考引用变量所指的对象所属的类，并运行对象所属类中的成员方法。
    简而言之：编译看左边，运行看右边。
      * C: 多态出现后会导致子父类中的成员变量、方法有微弱的变化。看如下代码
    ```java
    class Fu {
      int num = 4;
      void show() {
        System.out.println("Fu show num");
      }
    }
    class Zi extends Fu {
      int num = 5;
      void show() {
        System.out.println("Zi show num");
      }
    }
    class Demo {
      public static void main(String[] args)  {
        Fu f = new Zi();
        System.out.println(f.num);
        f.show();
      }
    }
    ```

  * instanceof关键字
    * A: 作用
     可以通过instanceof关键字来判断某个对象是否属于某种数据类型。如学生的对象属于学生类，学生的对象也属于人类

    * 格式:
    boolean  b  = 对象  instanceof  类;

    * 举例:
    Person p1 = new Student(); // 前提条件，学生类已经继承了人类
    boolean flag = p1 instanceof Student; //flag结果为true
    boolean flag2 = p2 instanceof Teacher; //flag结果为false

  * 总结
    * 封装：把对象的属性与方法的实现细节隐藏，仅对外提供一些公共的访问方式
    * 继承：子类会自动拥有父类所有可继承的属性与方法
    * 多态：配合继承与方法重写提高了代码的复用性与扩展性；若无方法重写，则多态无意义


# 编程题

## 1 水仙花练习功能实现

  * A: 水仙花练习功能实现
    * a: 题目分析
      * 明确什么样的数就是水仙花数。水仙花数是指一个3位数（100-999之间），其每位数字立方之和等于该3位数本身。
        如153 = 1*1*1 + 3*3*3 + 5*5*5，即 3位数本身 = 百位数立方 + 十位数立方 + 个位数立方;
      * 获取水仙花范围内的所有3位数（100-999之间的每个3位数）
      * 判断该3位数是否满足水仙花数，满足，打印该3位数
      
    * b: 解题步骤
      * 使用for循环，得到100-999之间的每个3位数
      * 获取3位数中百位数字、十位数字、个位数字
      * 使用if条件语句，判断该3位数是否满足水仙花数，满足，使用输出语句，打印该3位数
      
    * c: 案例代码
      ```java
      public class Test02 {
        public static void main(String[] args) {
          for (int i = 100; i < 1000; i++) {
            int bai = i/100%10;
            int shi = i/10%10;
            int ge = i%10;
            
            if (i == bai*bai*bai + shi*shi*shi + ge*ge*ge) {
              System.out.println(i);
            }
          }
        }
      }
      ```

## 2 99乘法表

  * A: 99乘法表的分析
    * a: 题目分析
      通过观察发现，如果把1`*`1=1这样的内容 看做一颗*的话，那么打印结果就成了如下效果:  
      `*`  
      `**`  
      `***`  
      `****`  
      …
      这样，就是打印9行星，每行打印星的个数与当前行数相等。
      再观察“1`*`3=3 2`*`3=6 3`*`3=9”得出它们如下的变化规律：
          每行第n次 +`*`+ 行号 +"="+ 每行第n次 * 行号
        如:  1 +`*`+  2    +"="+   1`*`2; // 相当于1`*`2=2
          2 +`*`+  2    +"="+   2`*`2; // 相当于2`*`2=4  

    * b: 解题步骤
      * 定义一个外层for循环，初始值从1开始，循环9次。用来控制打印的行数
      * 在外层for循环内部，定义一个for循环，初始值从1开始，循环次数与当前行数相等。用来完成每行打印指定次数的乘法公式 如1*1=1
      * 在内层for循环中，完成每行指定次数的乘法公式打印 如1`*`1=1
        System.out.print(k +`*`+ j +"="+ j*k +"\t");
        // 变量k代表：每行中的第n次
        // 变量j代表：行号
      * 在外循环中，当每行指定次数的乘法公式打印完毕后，通过System.out.println()切换到下一行。
        这样，再次打印乘法公式时，就在下一行输出打印了

  * B: 99乘法表的功能实现
    * a: 案例代码  
      利用嵌套for循环,实现99乘法表示
      实现步骤:
        1. 定义外循环控制行数
        2. 内循环控制个数,个数,每次都在递增
        3. 循环中输出,乘法表的格式   1*3=3
        
      ```java
      public class Test05 {
        public static void main(String[] args) {
          for (int j = 1; j < 10; j++) {
            for (int k = 1; k <= j; k++) {
              System.out.print(k +"*"+ j +"="+ j*k +"\t");
            }
            System.out.println();
          }
        }
      }
      ```

## 3 数组逆序

  * A: 数组逆序原理
    * a: 题目分析
      * 本题目要实现原数组元素倒序存放操作。即原数组存储元素为{11,22,33,44}，
        逆序后为原数组存储元素变为{44,33,22,11}。
      * 通过图解发现，想完成数组元素逆序，其实就是把数组中索引为start与end的元素进行互换。
      * 每次互换后，start索引位置后移，end索引位置前移，再进行互换
      * 直到start位置超越了end位置，互换结束，此时，数组元素逆序完成。
      
    * b: 解题步骤
      * 定义两个索引变量start值为0，变量end值为数组长度减去1（即数组最后一个元素索引）
      * 使用循环，完成数组索引start位置元素与end位置元素值互换。
      * 在循环换过程中，每次互换结束后，start位置后移1，end位置前移1
      * 在循环换过程中，最先判断start位置是否超越了end位置，若已超越，则跳出循环

  * A：案例代码  
    数组的逆序:
    数组中的元素,进行位置上的交换  
    逆序 不等于 反向遍历  
    就是数组中最远的两个索引,进行位置交换,实现数组的逆序  
    使用的是数组的指针思想,就是变量,思想,可以随时变换索引反转 reverse  
    实现步骤:
      1. 定义方法,实现数组的逆序
      2. 遍历数组
      实现数组的最远索引换位置
      使用临时的第三方变量
    ```java
    public class ArrayMethodTest_1{
      public static void main(String[] args){
        int[] arr = {3,5,7,1,0,9,-2};
        //调用数组的逆序方法
        reverse(arr);
      }
      
      /*
         定义方法,实现数组的逆序
         返回值: 没有返回值
         参数:   数组就是参数
      */
      public static void reverse(int[] arr){
        //利用循环,实现数组遍历,遍历过程中,最远端换位
        //for的第一项,定义2个变量, 最后,两个变量++ --
        for( int min = 0 , max = arr.length-1 ; min < max  ; min++,max--){
          //对数组中的元素,进行位置交换
          //min索引和max索引的元素交换
          //定义变量,保存min索引
          int temp = arr[min];
          //max索引上的元素,赋值给min索引
          arr[min] =  arr[max];
          //临时变量,保存的数据,赋值到max索引上
          arr[max] = temp;
        }
      }
    }
    ```

## 4 选择排序

  * A: 选择排序原理
    * a: 题目分析  
      * 通过观察发现，本题目要实现把数组元素{13,46,22,65,3}进行排序
      * 提到数组排序，就要进行元素值大小的比较，想完成排序要经过若干次的比较才能够完成。
      * 比较的第一个元素与该元素后面的数组元素依次比较到数组的最后一个元素，把小的值放在第一个数组元素中，数组循环一圈后，则把最小元素值互换到了第一个元素中。
      * 数组再循环一圈后，把第二小的元素值互换到了第二个元素中。按照这种方式，数组循环多圈以后，就完成了数组元素的排序。这种排序方式我们称为选择排序。

      
    * b: 解题步骤
      * 使用for循环（外层循环），指定数组要循环的圈数（数组循环的圈数为数组长度 - 1）
      * 在每一圈中，通过for循环（内层循环）完成数组要比较的第一个元素与该元素后面的数组元素依次比较到数组的最后一个元素，把小的值放在第一个数组元素中
      * 在每一圈中，要参与比较的第一个元素由第几圈循环来决定。
        * 进行第一圈元素比较时，要比较的第一个元素为数组第一个元素，即索引为0的元素
        * 进行第二圈元素比较时，要比较的第一个元素为数组第二个元素，即索引为1的元素
        * 依次类推，得出结论：进行第n圈元素比较时，要比较的第一个元素为数组第n个元素，即数组索引为n-1的元素
  * B: 案例代码
    ```java
    /*
      数组的排序: 一般都是升序排列,元素,小到大的排列
      
      两种排序的方式
       选择排序: 数组的每个元素都进行比较
       冒泡排序: 数组中相邻元素进行比较
       规则: 比较大小,位置交换
    */
    public class ArrayMethodTest_2{
      public static void main(String[] args){
        int[] arr  = {3,1,4,2,56,7,0};
        //调用选择排序方法
        selectSort(arr);
      }
      /*
        定义方法,实现数组的选择排序
        返回值: 没有
        参数:  数组
        实现步骤:
          1.嵌套循环实现排序
          外循环,控制的是一共比较了多少次
          内循环,控制的是每次比较了多少个元素
          2. 判断元素的大小值
          小值,存储到小的索引
      */
      public static void selectSort(int[] arr){
        for(int i = 0 ; i < arr.length - 1; i++){
          //内循环,是每次都在减少,修改变量的定义
          for(int j = i+1 ; j < arr.length ; j++){
            //数组的元素进行判断
            if(arr[i] > arr[j]){
              //数组的换位
              int temp = arr[i];
              arr[i] = arr[j];
              arr[j] = temp; 
            }
          }
        }
      }
      
      /*
         定义方法,实现功能
         返回值: void
         方法参数: 数组
      */
      public static void printArray(int[] arr){
        //输出一半中括号,不要换行打印
        System.out.print("[");
        //数组进行遍历
        for(int i = 0 ; i < arr.length ; i++){
          //判断遍历到的元素,是不是数组的最后一个元素
          //如何判断 循环变量 到达 length-1
          if( i == arr.length-1 ){
            //输出数组的元素和]
            System.out.print(arr[i]+"]");
          }else{
          //不是数组的最后一个元素,输出数组元素和逗号
            System.out.print(arr[i]+",");
          }
        }
        System.out.println();
      }
    }
    ```

## 5 冒泡排序

  * A: 冒泡排序功能实现
      * a: 题目分析
        * 通过观察发现，本题目要实现把数组元素{13,46,22,65,3}进行排序
        * 提到数组排序，就要进行元素值大小的比较，通过发现，我们想完成排序要经过若干次的比较才能够完成。
        * 相邻的元素值依次比较，把大的值放后面的元素中，数组循环一圈后，则把最大元素值互换到了最后一个元素中。
          数组再循环一圈后，把第二大的元素值互换到了倒数第二个元素中。按照这种方式，数组循环多圈以后，
          就完成了数组元素的排序。这种排序方式我们称为冒泡排序。
          
      * b: 解题步骤
        * 使用for循环（外层循环），指定数组要循环的圈数（数组循环的圈数为数组长度 - 1）
        * 在每一圈中，通过for循环（内层循环）完成相邻的元素值依次比较，把大的值放后面的元素中
        * 每圈内层循环的次数，由第几圈循环来决定。如上图所示
          * 进行第一圈元素比较时，内层循环次数为数组长度 - 1
          * 进行第二圈元素比较时，内层循环次数为数组长度 - 2
          * 依次类推，得出结论：进行第n圈元素比较时，内层循环次数为数组长度 - n
          
      * c: 案例代码 
        ```java
        /*
          数组的排序: 一般都是升序排列,元素,小到大的排列
          
          两种排序的方式
           选择排序: 数组的每个元素都进行比较
           冒泡排序: 数组中相邻元素进行比较
           规则: 比较大小,位置交换
        */
        public class ArrayMethodTest_2{
          public static void main(String[] args){
            int[] arr  = {3,1,4,2,56,7,0};
            //调用选择排序方法
            //selectSort(arr);
            
            //调用冒泡排序方法
            bubbleSort(arr);
            printArray(arr);
          }
          /*
             定义方法,实现数组的冒泡排序
             返回值: 没有
            参数:  数组
          */
          public static void bubbleSort(int[] arr){
            for(int i = 0 ; i < arr.length - 1; i++){
              //每次内循环的比较,从0索引开始, 每次都在递减
              //arr.length-i-1  arr.length-i内循环循环次数，-1保证索引不越界
              for(int j = 0 ; j < arr.length-i-1; j++){
                //比较的索引,是j和j+1
                if(arr[j] > arr[j+1]){
                  int temp = arr[j];
                  arr[j] = arr[j+1];
                  arr[j+1] = temp;
                }
              }
            }
          }
          
          /*
             定义方法,实现功能
             返回值: void
             方法参数: 数组
          */
          public static void printArray(int[] arr){
            //输出一半中括号,不要换行打印
            System.out.print("[");
            //数组进行遍历
            for(int i = 0 ; i < arr.length ; i++){
              //判断遍历到的元素,是不是数组的最后一个元素
              //如何判断 循环变量 到达 length-1
              if( i == arr.length-1 ){
                //输出数组的元素和]
                System.out.print(arr[i]+"]");
              }else{
              //不是数组的最后一个元素,输出数组元素和逗号
                System.out.print(arr[i]+",");
              }
            }
            System.out.println();
          }
        }
        ```

## 6 数组的折半查找

  * A: 数组的折半查找原理
      * a: 题目分析
        * 通过观察发现，本题目要实现查找指定数值在元素有序的数组中存储的位置（索引），返回该位置（索引）。
        * 我们使用数组最中间位置的元素值与要查找的指定数值进行比较，若相等，返回中间元素值的索引
        * 最中间位置的元素值与要查找的指定数值进行比较，若不相等，则根据比较的结果，缩小查询范围为上次数组查询范围的一半；
          再根据新的查询范围，更新最中间元素位置，然后使用中间元素值与要查找的指定数值进行比较
           比较结果相等，返回中间元素值的索引
           比较结果不相等，继续缩小查询范围为上次数组查询范围的一半，更新最中间元素位置，继续比较，依次类推。
        * 当查询范围缩小到min>max时，则指定数值没有查询到，返回索引值-1。
        
      * b: 解题步骤
        * 定义3个用来记录索引值的变量，变量min记录当前范围最小索引值，初始值为0；变量max记录当前范围最大索引值，初始值为数组长度-1；变量mid记录当前当前范围最中间元素的索引值(min+max)/2，初始值为0
        * 使用循环，判断当前范围下，最中间元素值与指定查找的数值是否相等
         若相等，结束循环，返回当前范围最中间元素的索引值mid
         若不相等，根据比较结果，缩小查询范围为上一次查询范围的一般
         中间元素值 比 要查询的数值大，说明要查询的数值在当前范围的最小索引位置与中间索引位置之间，此时，更新查询范围为:
            范围最大索引值 = 上一次中间索引位置 -1；
         中间元素值 比 要查询的数值小，说明要查询的数值在当前范围的最大索引位置与中间索引位置之间，此时，更新查询范围为:
            范围最小索引值 = 上一次中间索引位置 +1；
         在新的查询范围中，更新中间元素值的位置，再次使用最中间元素值与指定查找的数值是否相等。
            中间索引值 = (范围最小索引值 +范围最大索引值) / 2;
        * 每次查询范围缩小一半后，使用if语句判断，查询范围是否min>max，若min>max，则说明指定数值没有查询到，返回索引值-1。
  * B: 案例代码
    ```java
    /*
       数组的查找功能
       在一个数组中,找一个元素,是否存在于数组中,如果存在,就返回索引
       
       普通查询:
         找到元素在数组中出现的索引,如果没有这个元素,结果就是负数
        
    */
    public class ArrayMethodTest_3{
       public static void main(String[] args){
         int[] arr = {1,3,5,7,9,11,15};
         int index = binarySearch(arr,10);
         System.out.println(index);
         
       }
       
       /*
         定义方法,实现,折半查找
         返回值: 索引
         参数: 数组,被找的元素 
         实现步骤:
           1. 需要的变量定义
            三个,三个指针
            
           2. 进行循环折半
            可以折半的条件  min <= max
           
           3. 让被找元素,和中间索引元素进行比较
             元素 > 中间索引  小指针= 中间+1
             元素 < 中间索引  大指针= 中间-1
             元素 == 中间索引  找到了,结束了,返回中间索引
             
          4. 循环结束,无法折半
            元素没有找到 ,返回-1
       */
       public static int binarySearch(int[] arr, int key){
         //定义三个指针变量
         //数组长度可能为0,mid初始化为0
         int min = 0 ;
         int max = arr.length -1 ;
         int mid = 0;
         //循环折半,条件 min<=max
         while( min <= max){
           //公式,计算中间索引
           mid = (min+max)/2;
           //让被找元素,和中间索引元素进行比较
           if(key > arr[mid]){
             min = mid + 1;
           }else if (key < arr[mid]){
             max = mid - 1;
           }else{
             //找到元素,返回元素索引
             return mid;
           }
         }
         return -1;
       }
       
      /*
         定义方法,实现数组的普通查询
         返回值: 索引
         参数:   数组, 被找的元素
         
         实现步骤:
         1. 遍历数组
         2. 遍历过程中,使用元素和数组中的元素进行比较
          如果相同,返回元素在数组中的索引
          如果不同,返回负数
      */
      public static int search(int[] arr, int key){
        //遍历数组
        for(int i = 0 ; i < arr.length ; i++){
          //数组元素,被查找的元素比较
          if(arr[i] == key){
            //返回索引
            return i;
          }
        }
        return -1;
      }
    }
    ```