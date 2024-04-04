# 今日代码 PK | 使用 try-with-resources 关闭资源

`try-with-resources` 是 `Java 7` 中引入的一个语法糖，

用于自动关闭实现了 `AutoCloseable` 或 `Closeable` 接口的资源，

比如 文件输入输出流 等。

使用`try-with-resources`关闭资源非常方便，

示例代码如下：

```java
try (InputStream in = new FileInputStream("input.txt");
     OutputStream out = new FileOutputStream("output.txt")) {
    // 处理输入输出流
} catch (IOException e) {
    e.printStackTrace();
}
```

如果不使用这种方式，那么就需要我们在 `finally`块中手动处理，

示例代码如下：

```java
InputStream in = null;
OutputStream out = null;

try {
    in = new FileInputStream("input.txt");
    out = new FileOutputStream("output.txt");
    
    // 处理输入输出流
} catch (IOException e) {
    e.printStackTrace();
} finally {
    try {
        if (in != null) {
            in.close();
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
    try {
        if (out != null) {
            out.close();
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

可以明显的发现，下面这种方式更加繁琐，也容易出现遗漏关闭资源的情况。

因此推荐大家使用`try-with-resource`方式来关闭资源。

大家更喜欢哪种呢？

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/umo6m1](https://www.codecopy.cn/post/umo6m1)

更多优质代码欢迎进入小程序查看！

![代码小抄.png](..%2Fimgs%2F%E4%BB%A3%E7%A0%81%E5%B0%8F%E6%8A%84.png)


