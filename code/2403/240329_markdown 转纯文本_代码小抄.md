# 今日代码大赏 | markdown 转纯文本

前几天我们分享了将[富文本转为纯文本](https://mp.weixin.qq.com/s/G8Q-HaP4jvp7vif4QFMBEQ)后校验，

在类似场景下，我们可能需要将`markdown`格式转化为纯文本。

如果我们自己来做的话，肯定是比较麻烦而且不一定完善的，

我们可以借助`commonmark `来实现，示例代码：

```java
public static String markdownToText(String markdown) {
    if (StringUtils.isBlank(markdown)) {
        return "";
    }
    Parser parser = Parser.builder().build();
    Node document = parser.parse(markdown);
    TextContentRenderer textContentRenderer = TextContentRenderer.builder().build();
    return textContentRenderer.render(document);
}
```

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/fz2ktz](https://www.codecopy.cn/post/fz2ktz)

更多优质代码欢迎进入小程序查看！

![代码小抄.png](..%2Fimgs%2F%E4%BB%A3%E7%A0%81%E5%B0%8F%E6%8A%84.png)


