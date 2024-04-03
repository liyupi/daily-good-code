<a name="z5ZF1"></a>
# 今日代码大赏 | try-catch 优雅使用

在`Java`开发中，`try-catch`语句经常用于异常捕获。

值得注意的是，尽管一次`try-catch`中的性能损失难以觉察，但是一旦将`try-catch`语句应用于循环或遍历体内，就可能给系统性能造成极大的损害。

示例代码：

```java
@Test
public void test() {

    long start = System.currentTimeMillis();
    int a = 0;
    for(int i=0;i<1000000000;i++){
        try {
            a++;
        }catch (Exception e){
            e.printStackTrace();
        }
    }
    long useTime = System.currentTimeMillis()-start;
    System.out.println("useTime:"+useTime);
}
```

上面这段代码运行结果：`useTime:10`。

下面是一段将`try-catch`移到循环体外的代码，性能直接提升了将近一半，

示例代码：

```java
@Test
public void test(){
    long start = System.currentTimeMillis();
    int a = 0;
    try {
        for (int i=0;i<1000000000;i++){
            a++;
        }
    }catch (Exception e){
        e.printStackTrace();
    }
    long useTime = System.currentTimeMillis()-start;
    System.out.println(useTime);
}
```

上面这段代码运行结果是：`useTime:6`。

大家感觉今天的性能优化技巧怎么样呢，欢迎在评论区留下自己的看法。

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://codecopy.cn/post/92nqby](https://codecopy.cn/post/92nqby)

更多优质代码欢迎进入小程序查看！

![代码小抄.png](..%2Fimgs%2F%E4%BB%A3%E7%A0%81%E5%B0%8F%E6%8A%84.png)
