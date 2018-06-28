* 测试代码：

  ```java
  package 面试题;
  
  public class StaticClass {
      static {
          System.out.println("StaticClass loading...");
      }
      public static String VALUE = "static value loading";
      public static final String FIANL_VALUE = "final value loading";
  }
  ```

  ```java
  package 面试题;
  
  public class StaticAndFinalTest {
      public static void main(String[] args) {
          System.out.println(StaticClass.FIANL_VALUE);  
          System.out.println(StaticClass.VALUE); 
      }
  }
  ```

* 运行结果

  ```shell
  final value loading
  StaticClass loading...
  static value loading
  ```

常量值存储在JVM内存中的常量区，在类不加载时即可访问。



当然，如果说所有的静态常量访问都不需要类的加载是不对的。要看这个常量是否属于编译期常量，即在编译期即可确定常量值。如果常量值必须在运行时才能确定，也会引起类的加载。

如下：

* 测试代码

  ```java
  package 面试题;
  
  import java.util.Random;
  
  public class StaticClass {
  
      static {
          System.out.println("StaticClass loading...");
      }
  
      public static String VALUE = "static value loading";
  
      public static final String FIANL_VALUE = "final value loading";
      
      public static final String FINAL_VALUE2 = String.valueOf(new Random(66).nextInt());
  }
  
  ```

  ```java
  package 面试题;
  
  public class StaticAndFinalTest {
  
      public static void main(String[] args) {
          System.out.println(StaticClass.FINAL_VALUE2);  
          System.out.println(StaticClass.VALUE); 
      }
  
  }
  ```

* 执行结果

  ```shell
  StaticClass loading...
  -1179339008
  static value loading
  ```

  
