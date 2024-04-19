# 我成功复刻了安卓 6 彩蛋 Flappy Droid !

今天终于星期五了，可恶的调休，上了整整六天班 ❛‿˂̵✧。

所以为了庆祝今天是星期五，我们今天浅浅摸鱼一下，在代码小抄实现玩游戏自由。

这个功能多亏了代码小抄前端同学的努力哈，才给了我们在上班时也能摸鱼的机会，给前端小哥加🍗（bushi，其实是运行自己写的前端代码的效果了，顺便当一手测试，我这是给老板节省人力和财力支出，❛‿˂̵✧）。

其实，代码小抄早已经支持了少部分语言的在线运行（如 Java、JavaScript、C++、C、Python3、Go、TypeScript），这次支持前端在线展示效果，是对代码小抄功能进一步的完善。

好了，切入正题，首先给大家小小的科普下，自从 Android 2.3 以来，每代安卓系统中都会隐藏一个小彩蛋，而这些彩蛋的内容都与本代系统的版本代号相呼应。

比如今天在代码小抄实现的安卓 6 彩蛋游戏 Flappy Droid。

![](https://cdn.nlark.com/yuque/0/2024/webp/38420467/1712734555769-78f56487-9d7b-4367-8147-2cfe9c853654.webp#averageHue=%23485f6f&clientId=u687fa189-06b8-4&from=paste&id=u3b4017e1&originHeight=402&originWidth=720&originalType=url&ratio=1.125&rotation=0&showTitle=false&status=done&style=none&taskId=u4d56504b-f7d5-43c9-98aa-41aec2b19f9&title=)

废话不多说，由于完整代码太长，我这里展现下 ”快活鸟“ 游戏的 JavaScript 部分代码。

```javascript
// Bird object
let bird;
// Array to hold pipes
let pipes = [];
// Gravity effect
let gravity = 0.6;
// Lift on jump
let lift = -15;

function setup() {
  createCanvas(400, 350);
  bird = new Bird();
  pipes.push(new Pipe());
}

function draw() {
  background(0);

  // Display and update bird
  bird.update();
  bird.show();

  if (frameCount % 100 == 0) {
    pipes.push(new Pipe());
  }

  // Display and update pipes
  for (let i = pipes.length - 1; i >= 0; i--) {
    pipes[i].show();
    pipes[i].update();

    if (pipes[i].hits(bird)) {
      console.log("HIT");
    }

    if (pipes[i].offscreen()) {
      pipes.splice(i, 1);
    }
  }
}

function keyPressed() {
  if (key == ' ') {
    bird.up();
  }
}


//...剩下代码请访问代码小抄
```

完整代码可在下方小程序中查看，更适合在电脑上进行体验游戏哦。若您正在使用电脑阅读本文，可复制下方链接到浏览器或点击文末的“阅读原文”即可快速体验安卓 6 彩蛋游戏 Flappy Droid。

[https://www.codecopy.cn/post/etz2vz](https://www.codecopy.cn/post/etz2vz)

今天的轻松一刻到此结束，欢迎你在代码小抄贡献更多可以在线运行的小游戏哦！

也欢迎大家给我们的产品提需求，好的需求会得到我们官方的小礼品 🎁~

完整代码片段来源于代码小抄，欢迎点击进入小程序阅读！

在线访问：[https://www.codecopy.cn/post/etz2vz](https://www.codecopy.cn/post/etz2vz)

![image.png](https://cdn.nlark.com/yuque/0/2024/jpeg/38420467/1712735543296-2f7c72c2-75ad-4f27-9fac-28f3d27567d9.jpeg#averageHue=%23dadada&clientId=u687fa189-06b8-4&from=paste&id=u8674a032&originHeight=430&originWidth=430&originalType=url&ratio=1.125&rotation=0&showTitle=false&size=85862&status=done&style=none&taskId=u2a5b9788-a797-4ab7-8c52-c83c4ffc070&title=)

具体游玩方式，可参考下方图片中的红色框框。

![image.png](https://cdn.nlark.com/yuque/0/2024/png/38420467/1712735633391-7fda48fe-2f06-4129-907b-5d3fe1911847.png#averageHue=%23151514&clientId=u687fa189-06b8-4&from=paste&height=671&id=zIx4R&originHeight=839&originWidth=1539&originalType=binary&ratio=1.125&rotation=0&showTitle=false&size=115808&status=done&style=none&taskId=ue866b784-6d39-4660-bfc3-c9a1fe54481&title=&width=1231.2)

在代码小抄可以看到更多优质代码，也欢迎大家积极分享，可能会获得我们官方的小礼品 🎁~

![](https://cdn.nlark.com/yuque/0/2024/jpeg/38420467/1712227408140-7be9f466-422c-48d5-9395-3189121f0e1b.jpeg#averageHue=%23d3df71&clientId=ud95bb593-9f83-4&from=paste&id=u660947fb&originHeight=267&originWidth=724&originalType=url&ratio=1.125&rotation=0&showTitle=false&status=done&style=none&taskId=ube8adf59-d6d7-4b1e-b600-f98a6a2b04e&title=)


