## Lambda表达式
```java
public static void main(String[] args) {
    // 用匿名内部类的方式来创建线程
    new Thread(new Runnable() {
        @Override
        public void run() {
            System.out.println("Hello world!");
        }
    });

    // 使用Lambda来创建线程
    new Thread(() -> System.out.println("Hello world!"));
}
```
### Runnable接口

![Runnable](/images/Runnable.png)

函数式编程接口的特点是：只有一个抽象方法

### 方法引用
```java
public class Demo {
    public static void main(String[] args) {
        // 静态方法引用--通过类名调用
        Consumer<String> consumerStatic = User::myNameStatic;
        consumerStatic.accept("Bruce Wayne");

        // 实例方法引用--通过实例调用
        User user = new User();
        Consumer<String> consumerInstance = user::myNameInstance;
        consumer.accept("Batman");

        // 构造方法方法引用--无参数
        Supplier<User> batman = User::new;
        System.out.println(batman.get());
    }
}
```
```java
class User {
    // 静态方法
    public static void myNameStatic(String name) {
        System.out.println(name);
    }

    // 实例方法
    public void myNameInstance(String name) {
        System.out.println(name);
    }

    // 无参构造方法
    public User() {
    }
}
```
