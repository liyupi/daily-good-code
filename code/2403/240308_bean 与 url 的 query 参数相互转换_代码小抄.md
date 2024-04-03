# 今日代码大赏 | 还在自己转 URL？

不知道大家有没有遇到过这样一种场景？

需要将一个 Bean 转成能够拼接在 url 后面的 query 参数。

自己来做的话需要一个一个 get 从对象中获取值，然后拼接或者通过反射实现。

但其实 Hutool 里提供了现成的工具方法，如下：

```java
CommentAddRequest request = new CommentAddRequest();
request.setPostId(1L);
request.setContent("hh");
request.setType("sdf");
request.setContentType(0);


// 将对象转换为 Map
Map<String, Object> paramMap = BeanUtil.beanToMap(request);

// 将 Map 转换为 URL Query 参数
// postId=1&content=hh&type=sdf&contentType=0
String queryString = HttpUtil.toParams(paramMap);
```



当然还有其逆向方法：将 query 参数转成 map

```java
Map<String, String> map = HttpUtil.decodeParamMap("postId=1&content=hh&type=sdf&contentType=0", StandardCharsets.UTF_8);
CommentAddRequest commentAddRequest = BeanUtil.mapToBean(map, CommentAddRequest.class, true, null);
```



完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：https://www.codecopy.cn/post/4ohv35

（小程序）



