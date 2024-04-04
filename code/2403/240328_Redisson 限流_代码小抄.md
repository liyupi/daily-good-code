# 今日代码大赏 | Redisson 限流

作为后端开发，我们免不了要经常跟锁打交道，

其中`Redisson`框架里包含了强大的分布式锁实现，

但除了分布式锁，`Redisson`里限流的功能。

假设我们已经写好了配置及配置类，

就可以通过下面的代码非常简单的实现限流，

示例代码：

```java
@Resource
private RedissonClient redissonClient;

public void doRateLimit(String key) {
    if (StringUtils.isBlank(key)) {
        return;
    }
    // 用户限流，每 3 秒 1 次
    RRateLimiter rateLimiter = redissonClient.getRateLimiter(key);
    // 设置限流参数，比如每秒钟最多处理的请求数
    rateLimiter.trySetRate(RateType.OVERALL, 1, 3, RateIntervalUnit.SECONDS);
    boolean permit = rateLimiter.tryAcquire();
    ThrowUtils.throwIf(!permit, ErrorCode.OPERATION_ERROR, "操作过于频繁");
}
```

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/tzwijz](https://www.codecopy.cn/post/tzwijz)

![代码小抄.png](..%2Fimgs%2F%E4%BB%A3%E7%A0%81%E5%B0%8F%E6%8A%84.png)


