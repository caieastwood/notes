# Mockito

## 添加方式
在类声明上面加上  
`@RunWith(MockitoJUnitRunner.class)`  
或加入以下方法  
```java
@Before
public void setUp() {
    MockitoAnnotations.initMocks(this);
}
 ```