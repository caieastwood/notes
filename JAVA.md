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
        Consumer<String> consumerLambda = s -> System.out.println(s);
        consumerLambda.accept("Bruce Wayne1");
        
        // 两个入参，无返回值
        BiConsumer<String, Integer> biConsumerLambda = (s, i) -> System.out.println(s+i);
        biConsumerLambda.accept("Bruce wayne", 11);

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

## 泛型

### 泛型方法

```java
public class TestGenericMethod {
    // 泛型方法printArray
    public static < E > void printArray(E[] inputArray) {
        // 输出数组元素            
        for(E element : inputArray) {
            System.out.printf("%s ", element);
        }
        System.out.println();
    }
 
    public static void main(String args[]) {
        // 创建不同类型数组：Integer, Double, Character
        Integer[] intArray = {1, 2, 3, 4, 5};
        Double[] doubleArray = {1.1, 2.2, 3.3, 4.4};
        Character[] charArray = {'H', 'E', 'L', 'L', 'O'};
        
        // 传递一个整型数组
        printArray(intArray);

        // 传递一个双精度型数组
        printArray(doubleArray);

        // 传递一个字符型数组
        printArray(charArray);
    }
}
```

### 类型参数有界的泛型方法

```java
public class TestMaximum {
    // 比较三个值并返回最大值，此处类型T限制为Comparable的子类
    public static <T extends Comparable<T>> T maximum(T x, T y, T z) {
        T max = x; // 假设x是初始最大值
        if (y.compareTo(max) > 0) {
            max = y; // y更大
        }
        if (z.compareTo(max) > 0) {
            max = z; // 现在z更大
        }
        return max; // 返回最大对象
    }
    public static void main(String args[]) {
        System.out.printf("%d, %d 和 %d 中最大的数为%d\n\n", 3, 4, 5, maximum(3, 4, 5));
 
        System.out.printf("%.1f, %.1f 和 %.1f 中最大的数为%.1f\n\n", 6.6, 8.8, 7.7, maximum(6.6, 8.8, 7.7));
 
        System.out.printf("%s, %s 和 %s 中最大的数为%s\n","pear", "apple", "orange", maximum("pear", "apple", "orange"));
    }
}
```

### 泛型类

```java
public class Box<T> {
    private T t;
 
    public void add(T t) {
        this.t = t;
    }

    public T get() {
        return t;
    }

    public static void main(String[] args) {
        Box<Integer> integerBox = new Box<Integer>();
        Box<String> stringBox = new Box<String>();
 
        integerBox.add(new Integer(10));
        stringBox.add(new String("Bruce wayne"));
 
        System.out.printf("整型值为:%d\n\n", integerBox.get());
        System.out.printf("字符串为:%s\n", stringBox.get());
    }
}
```
