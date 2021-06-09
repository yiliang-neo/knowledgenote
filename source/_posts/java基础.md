- `char`在`java`中占两个字节，`byte`占一个字节

- 单行注释`//`，多行注释`/*...*/`，文档注释`/**...*/`

- java泛型类，泛型接口，泛型方法

```java
//此处T可以随便写为任意标识，常见的如T、E、K、V等形式的参数常用于表示泛型
//在实例化泛型类时，必须指定T的具体类型
public class Generic<T>{

    private T key;

    public Generic(T key) {
        this.key = key;
    }

    public T getKey(){
        return key;
    }
}


public interface Generator<T> {
    public T method();
}


public static < E > void printArray( E[] inputArray )
{

     for ( E element : inputArray ){

        System.out.printf( "%s ", element );

     }

     System.out.println();

}
```

- java类型/泛型擦除

- **基本数据类型==比较的是值，引用数据类型==比较的是内存地址**

- `String`中的`equals`方法是被重写过的，比较的是对象的值；而`Object`中的`equals`比较的是对象的内存地址

- 重写`equals`方法时，必须也要重写`hashCode`方法

- java基本数据类型**Byte,Short,Integer,Long,Character,Boolean**实现了常量池，**Float,Double 并没有实现常量池技术**

- **但是new的时候不会指向常量池**

- java中都是**值传递**，但是与c++中的值传递不同
  
  - 一个方法**不能修改**一个**基本数据类型**的参数（即数值型或布尔型）
  
  - 一个方法**可以改变**一个**对象**参数的状态
  
  - 一个方法**不能**让对象参数引用一个新的对象（即使这个新对象的作用域覆盖出方法）

- 重载：相同方法不同参数；重写：对祖先方法进行重写

- java不想序列化：`transient`关键字修饰变量
* 获取键盘输入：`Scanner`或`BufferedReader`

```java
Scanner in = new Scanner(System.in);
in.nextLine(); in.hasNext(); in.nextInt();

BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
String s = in.readLine();
```

* java中的字符串
  
  * 不经常改变的场景，用**String**
  
  * 单线程下经常改变，用**StringBuilder**
  
  * 多线程下经常改变，用**StringBuffer**

* 反射：JAVA 反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为 java 语言的反射机制。
  
  - **优点：** 运行期类型的判断，动态加载类，提高代码灵活度。
  - **缺点：** 1,性能瓶颈：反射相当于一系列解释操作，通知 JVM 要做的事情，性能比直接的 java 代码要慢很多。2,安全问题，让我们可以动态操作改变类的属性同时也增加了类的安全隐患。
  - 1. 我们在使用 JDBC 连接数据库时使用 `Class.forName()`通过反射加载数据库的驱动程序；
    2. Spring 框架的 IOC（动态加载管理 Bean）创建对象以及 AOP（动态代理）功能都和反射有联系；
    3. 动态配置实例的属性；

* 异常

![](C:\Users\MYYL\AppData\Roaming\marktext\images\2021-04-11-09-18-31-image.png)

* try-catch-finally和try-with-resources（后一种就是在try后面加括号，里面写声明语句）

* IO模式：BIO阻塞IO，NIO非阻塞IO，AIO异步IO

* 序列化
  
  * transient 关键字声明 不被序列化
  - **序列化**： 将数据结构或对象转换成二进制字节流的过程
  - **反序列化**：将在序列化过程中所生成的二进制字节流的过程转换成数据结构或者对象的过程
  - **序列化的主要目的是通过网络传输对象或者说是将对象存储到文件系统、数据库、内存中。**

* 注意==在哪都没有重写，是equals被重写了；equals没有重写之前，就是用的return this == o;所以只有重写过的equals方法才是比较的值，而不是equals方法本来就比较的值

* **Override(覆写)，Overload(重载)，Overwrite(重写)**
  
  * 事实上，**后两种都不是注解**
    
    |       | Override                                            | 重载                                                                      |
    |:-----:|:---------------------------------------------------:|:-----------------------------------------------------------------------:|
    | 访问修饰符 | 只能高于或等于父类方法的权限，不能降级<br/>不能覆写父类的private方法，因为子类没有访问权限 | 也是只能升级或同级；<br/>可以重载父类的private方法（不对，实际上要是private的，也不叫重载，因为各自都不知道对方有这个方法） |
    | 返回值   | 不能更改                                                | 可以不同，但不能仅仅只有返回值不同；（不代表子类必须要不同，可以完全相同）                                   |
    | 方法名   | 不能更改                                                | 方法名改了，就不叫重载了；那是定义了一个新方法啊                                                |
    | 参数    | 不能更改                                                | 可以更改                                                                    |
    | 方法内容  | 可以更改                                                | 可以更改                                                                    |

* **方法覆写**
  
  * 可以直接使用匿名函数 在对象声明时 覆写类的方法，实现自己想要的功能
    
    ```java
    int k = ...;
    Map<Integer, Integer> lhm = new LinkedHashMap<Integer, Integer>(16, 0.75f, true){
        @Override
        protected boolean removeEldestEntry(Map.Entry<Integer, Integer> entry) {
            return size() > k;
        }
    };
    ```

* 
