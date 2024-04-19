# 今日代码大赏 | **arrayCopy 优雅使用**

数组复制是一项使用频率很高的功能，JDK 中提供了一个高效的 API 来实现它。

下面先让我们来看下官方对这个 API 的解释。

```java
/**
 * @param      src      the source array.
 * @param      srcPos   starting position in the source array.
 * @param      dest     the destination array.
 * @param      destPos  starting position in the destination data.
 * @param      length   the number of array elements to be copied.
 * @exception  IndexOutOfBoundsException  if copying would cause
 *               access of data outside array bounds.
 * @exception  ArrayStoreException  if an element in the <code>src</code>
 *               array could not be stored into the <code>dest</code> array
 *               because of a type mismatch.
 * @exception  NullPointerException if either <code>src</code> or
 *               <code>dest</code> is <code>null</code>.
 */
public static native void arraycopy(Object src,  int  srcPos,
                                    Object dest, int destPos,
                                    int length)
```

如果在应用程序中需要进行数组复制，应该使用这个函数，而不是自己实现。

下面来举个例子展示下，数组复制自己实现和直接调用官方的在性能上的差别吧。

自己实现数组复制示例代码：

```java
@Test
public void testArrayCopy(){
    int size = 100000;
    int[] array = new int[size];
    int[] arraydest = new int[size];

    for(int i=0;i<array.length;i++){
        array[i] = i;
    }
    long start = System.currentTimeMillis();
    for (int k=0;k<1000;k++){
        for(int i=0;i<size;i++){
            arraydest[i] = array[i];
        }
    }
    long useTime = System.currentTimeMillis()-start;
    System.out.println("useTime:"+useTime);
}
```

运行结果：`useTime:102`

调用 arrayCopy() 的示例代码：

```java
@Test
public void testArrayCopy(){
    int size = 100000;
    int[] array = new int[size];
    int[] arraydest = new int[size];

    for(int i=0;i<array.length;i++){
        array[i] = i;
    }
    long start = System.currentTimeMillis();
    for (int k=0;k<1000;k++){
        //进行复制
        System.arraycopy(array,0,arraydest,0,size);
    }
    long useTime = System.currentTimeMillis()-start;
    System.out.println("useTime:"+useTime);
}
```

运行结果：`useTime:59`

通过运行结果可以看出效果，自己实现数组复制，和直接调用官方的性能差别还是挺大的。

因为 `System.arraycopy()`函数是 native 函数，通常 native 函数的性能要优于普通函数。

所以仅出于性能考虑，在程序开发时，应尽可能调用 native 函数。

大家感觉今天的代码大赏性能优化技巧如何呢？

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/09ncvq](https://www.codecopy.cn/post/09ncvq)

![](https://cdn.nlark.com/yuque/0/2024/jpeg/38420467/1712227391271-37735cbc-6af4-492d-8ab1-67f7d16d4ac6.jpeg#averageHue=%23dfdfde&clientId=ud95bb593-9f83-4&from=paste&id=uedfc9b19&originHeight=430&originWidth=430&originalType=url&ratio=1.125&rotation=0&showTitle=false&status=done&style=none&taskId=u6d4a4640-51db-4a94-8d18-e3630006e70&title=)

在代码小抄可以看到更多优质代码，也欢迎大家积极分享，可能会获得我们官方的小礼品 🎁~

![](https://cdn.nlark.com/yuque/0/2024/jpeg/38420467/1712227408140-7be9f466-422c-48d5-9395-3189121f0e1b.jpeg#averageHue=%23d3df71&clientId=ud95bb593-9f83-4&from=paste&id=u660947fb&originHeight=267&originWidth=724&originalType=url&ratio=1.125&rotation=0&showTitle=false&status=done&style=none&taskId=ube8adf59-d6d7-4b1e-b600-f98a6a2b04e&title=)

以上就是本期分享。哝，你们要的封面图（来源于网络），有收获的话记得给我们点赞哦~<br />![](https://cdn.nlark.com/yuque/0/2024/png/33547719/1711979964255-be9a3aeb-2ace-4191-9e98-f036549c41b1.png?x-oss-process=image%2Fformat%2Cwebp%2Fresize%2Cw_636%2Climit_0#averageHue=%23dfdfde&from=url&id=Mt5ag&originHeight=337&originWidth=636&originalType=binary&ratio=1.125&rotation=0&showTitle=false&status=done&style=none&title=)