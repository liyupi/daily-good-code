# 今日代码大赏 | 优雅创建客户端对象

我们在开发中，会根据需求使用各种第三方接口或类库，比如要使用云服务商的对象存储来存储用户图片。

一般情况下，我们首先要去看官网文档，然后按照文档引入 SDK、并且通过示例代码去初始化一个客户端对象，之后调用该客户端对象的方法就能调用第三方接口了。

大家会怎么创建客户端对象呢？是每次调用方法时，都去写一堆 new 对象的方法么？或者运用单例模式来复用对象实例？

如果是 Spring Boot 项目，其实有更优雅、更便捷的实现方式，通过编写一个 @Configuration 配置类来创建一个可以自动读取配置文件来填充属性、并且可以复用的 Bean。

比如我们通过配置类来创建一个 MySQL 的客户端，代码可能是下面这样的：

```java

@Configuration
@ConfigurationProperties(prefix = "mysql")
@Data
public class DBClientConfig {

    /**
     * 用户名
     */
    private String username;
  
    /**
     * 密码
     */
    private String password;

    @Bean
    public DBClient dBClient() {
        return new DBClient(username, password);
    }
}
```



再给大家分享一个可以拿来直接用的代码片段，使用 Java 实现腾讯云对象存储的客户端。

代码片段已发布在代码小抄，欢迎点击进入小程序阅读！

在线访问：https://www.codecopy.cn/post/by4xa0

（小程序）

![](https://pic.yupi.icu/1/WX20240309-220207@2x.png)

