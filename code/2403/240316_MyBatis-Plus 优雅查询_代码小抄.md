# 今日代码大赏 | MyBatis-Plus 优雅查询

对于 Java 开发来说，MyBatis-Plus 可以说是再熟悉不过的持久层框架了。

其中 Wrapper 给我们提供了十分方便和灵活的方式来构造数据库查询条件。

我们经常写出类似如下的代码：

```java
QueryWrapper<Post> postQueryWrapper = new QueryWrapper<>();
postQueryWrapper.eq("userId", userId);
postQueryWrapper.like("content", searchText);
List<Post> postList = postService.list(postQueryWrapper);
```

但其实它并不优雅！

因为在拼装查询条件时，我们使用了类似 “userId”，“content” 等魔法值。

那我们该怎么改进呢？其实 MyBatis-Plus 为我们提供了另一种写法。

示例代码如下：

```java
List<Post> postList = postService.lambdaQuery()
        .eq(Post::getUserId, userId)
        .like(Post::getContent, searchText)
        .list();
```

大家觉得哪种写法更好呢？欢迎在评论区留下自己的看法。

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：https://www.codecopy.cn/post/s8gdd5

《小程序卡片》

更多优质代码欢迎进入小程序查看！

《小程序卡片》

《往期推荐》

