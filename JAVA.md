## Lambda表达式

### Demo
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
> 使用Lambda表达式创建线程的时候，并不关心接口名，方法名，参数名。我们只关注他的参数类型，参数个数，返回值。Lambda表达式返回的是接口的实例对象。

### Runnable接口

![Runnable](/images/Runnable.png)

> `@FunctionalInterface`表示这是一个函数式编程接口

### 方法引用
```java
public class Demo {
    public static void main(String[] args) {
        // 一个入参，无返回值
        Consumer<String> consumerLambda = s-> System.out.println(s);
        consumerLambda.accept("Bruce Wayne1");

        // 无入参，有返回值
        Supplier<String> supplierLambda = () -> "Bruce wayne2";
        System.out.println(supplierLambda.get());

        // 静态方法引用--通过类名调用
        Consumer<String> consumerStatic = User::myNameStatic;
        consumerStatic.accept("Bruce Wayne3");

        // 实例方法引用--通过实例调用
        User user = new User();
        Consumer<String> consumerInstance = user::myNameInstance;
        consumerInstance.accept("Bruce Wayne4");

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
