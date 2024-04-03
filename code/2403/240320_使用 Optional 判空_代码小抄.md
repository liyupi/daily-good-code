# 今日代码大赏 | 使用 Optional 判空

对于 Java 开发来说，判空可以说是一种素养，很多 bug 都是由空指针引起的。

为了避免空指针异常，我们通常会在使用对象前进行判空，

如果某个必要的对象为空，可以抛出相应的异常。

示例代码如下：

```java
Item item = itemService.lambdaQuery()
        .eq(Item::getUserId, userId)
        .eq(Item::getName, itemName)
        .one();
if (item == null) {
    throw new RuntimeException();
}
```

当然还有另外一种使用 `Optional`的方式，更加的简洁，但是有一点的学习和熟悉成本，

示例代码如下：

```java
Item item = Optional.ofNullable(itemService.lambdaQuery()
                .eq(Item::getUserId, userId)
                .eq(Item::getName, itemName)
                .one())
        .orElseThrow(RuntimeException::new);
```

大家更喜欢哪种呢？欢迎投票并在评论区留下自己的看法。

投票

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/iklcx9](https://www.codecopy.cn/post/iklcx9)

《小程序卡片》

更多优质代码欢迎进入小程序查看！

《小程序卡片》

《往期推荐》
