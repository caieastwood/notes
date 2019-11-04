## AOP

### execution

`execution(* com.ehm..*Assistant.*(..))`

1. `execution()`表示方法体
2. 第一个*号的位置表示返回类型，*号表示所有的类型
3. `com.ehm..`中的两个句点表示com.ehm当前包及其所有子包
4. `*Assistant`表示所有名字以Assistant结尾的类
5. `*(..)`中的*号表示所有的方法，(..)中的括号表示方法里的参数，两个句点表示所有参数
