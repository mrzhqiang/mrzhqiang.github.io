# 前言
最开始接触 [Play Framework][1] 是从 Android 开发转型为 Java 后端开发，公司有现成的项目可以模仿，再加上本身对新技术的追求，便义无反顾地拥抱了它。之后花费不少时间打磨钻研，对比以前了解过的 JavaEE 开发，深觉 Play 真是太方便了。

我不想复制 Play 官网上的介绍，我觉得找到这篇新手入门文章的同学，都是对 Play 有一定的兴趣，或者也像我一样，有现成的项目需要快速了解它。

不管怎样，你需要知道的就是，Play 也是排行前五的 Java Web 开发框架，通过 [环信-本周头条][2] 你可以找到它的身影，里面有一些比较中立的观点。

另外，从开发者角度来看，Play 也是一个全栈式开发框架，使用简单的前端技术（HTML、CSS 和 JavaScript）加上内置的模板引擎，就可以渲染出绚丽多彩的网页，并且它从上到下都是纯异步的，基于线程池对每个请求都分配处理线程，构建于 Java8 之上的 Play 天生就支持并发编程，可以更合理地分配资源。

最后，你还可以从 Github 的收藏数量，坚定你的学习信念：

![github](https://img.shields.io/github/stars/playframework/playframework)


# 正文
~~更新这篇新手入门时，Play 的版本是 `2.6.15`，所以接下来的内容，都是基于这个版本的吐槽。~~

现在 [Play Framework][1] 官方发布的稳定版本是：`2.8.0`。

[Maven 中央库][3] 上的最新版本是：

![Maven](https://img.shields.io/maven-central/v/com.typesafe.play/play_2.13.svg)

而 Github 上的 Play 仓库已经在着手准备 [2.9.0-SNAPSHOT][4] 版本。

由此可见，Play 的社区也很活跃，至少他们在积极开发新功能和修复缺陷。

## 一、快速启动
按照惯例，我们通过启动一个 `Hello World` 项目，来观察 [Play Framework][1] 到底有多简单。

### 1.1 准备环境
查看 [Play Requirements][6] 得知运行 Play 程序需要：

1. Java SE 1.8 或更高版本
2. 构建工具：推荐是最新版本的 [SBT][7]。

我不准备介绍如何搭建开发环境，因为这是 Java 开发的基本功，即便你现在不会搭建，通过百度/谷歌等搜索引擎，你也可以轻松学会这一点。

对于构建工具，其实只要你使用 IntelliJ IDEA 旗舰版，那就不用额外下载，IDEA 已经内置好了。另外，在所有 Play 的样例中，也是自带了构建工具，所以暂时可以跳过它们。

### 1.2 下载运行
包含 `Hello World` 的示例项目已经打包成 `zip` 压缩文件，并且拥有两个不同的开发语言版本：

- [Play Java Starter Example][8]
- [Play Scala Starter Example][9]

这里我们下载 Java 版本，并解压出来：

![](https://upload-images.jianshu.io/upload_images/7426376-cd9e9e8438e67258.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在 Windows 10 上，按住 Shift 键点击目录中的空白部分，选择 `在此处打开 Powershell 窗口(S)`，然后输入命令 `./sbt run` 即可运行。

你也可以通过其他命令行跳转到这个目录，然后运行 `./sbt run` 命令。

经过**漫长的等待**后，Play 程序终于运行成功：

![](https://upload-images.jianshu.io/upload_images/7426376-ba253000b9e07fc8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

通过在浏览器中访问 `http://localhost:9000` 可以看到 Play 呈现在用户面前的样子：

![](https://upload-images.jianshu.io/upload_images/7426376-95c62720c7214aa1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

*提示：Play 在开发模式下内置了热部署插件，因此每当访问 Play 应用时，如果检测到未编译字节码（或源代码已被修改），则会自动触发一次编译（需要等待一会儿），以便展现最新样式。*

## 二、基本开发
`Play 2.8.0` 版本的主页完全变了模样，不过不用担心，所谓万变不离其宗，只要知晓其中的关键开发流程，它再怎么变也不怕。

### 2.1 路由表
首先用记事本打开示例项目中的 `confg/routes` 文件：

![](https://upload-images.jianshu.io/upload_images/7426376-5e5aaa3d92579a2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

路由表提供所有接口的相关信息，我们可以试着添加以下内容到文件尾行并保存：

```text
GET  /hello  controllers.HomeController.hello
```

然后我们刷新浏览器，查看 Play 是否重新编译代码，以及在编译过程中出错，是如何反馈的：

![](https://upload-images.jianshu.io/upload_images/7426376-55e8b69fb3bba17c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

非常清晰的错误反馈，它告诉我们，在哪个文件的哪一行代码出了问题，具体是在 `controllers.HomeController` 中没有找到 `hello` 成员。

### 2.2 控制器
现在让我们打开 `app/controllers/HomeController`，添加一个 `hello` 方法：

```text
    public Result hello() {
        return ok("hello Play!");
    }
```

访问 `http://localhost:9000/hello`，看看 Play 会带给我们什么样的信息：

![](https://upload-images.jianshu.io/upload_images/7426376-2c42a657a7689b46.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2.3 视图渲染
接下来，我们复制 `app/views/index.scala.html` 为 `app/views/hello.scala.html`，修改并保存：

![](https://upload-images.jianshu.io/upload_images/7426376-b42cd3b24f8ea534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

做完这一步，我们还需要引用这个新文件，现在进入 `app/controlles/HomeController` 的 `hello` 方法，修改为以下内容：

```text
    public Result hello() {
        return ok(views.html.hello.render());
    }
```

现在让我们刷新浏览器，看看发生了什么变化：

![](https://upload-images.jianshu.io/upload_images/7426376-c67acd8a4dec867f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Play 的视图由 Twirl 引擎负责渲染，它通过一些模板语法将各个页面模块化，开发者只需要关心 `<body>` 里面的细节，而不用每次都添加 HTML 的重复内容。

本节内容基本参考 `http://localhost:9000/tutorial` 教程，有兴趣的同学可以深入探索一下。

## 三、官方文档
我希望简单介绍一下官方文档，以便大家遇到问题，可以第一时间找到解决方案。

Play 官方网站分为三大部分：1.开始入门；2.阅读文档；3.加入讨论。

第一部分的开始入门，我们已经在前面简单学习过，想要深入了解的话，可以点击[传送门][10]进去看看。

第三部分的加入讨论，不是本文的重点，因此将略过不提，有兴趣的同学可以去一探究竟。

所以主要讲解的是第二部分：阅读文档。

### 3.1 文档侧边栏
在文档侧边栏的顶部位置，可以选择**文档版本**、**开发语言**、**文档语言**，可惜没有中文。

![](https://upload-images.jianshu.io/upload_images/7426376-2e14ccf3cee97205.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

接下来是文档主目录，列举了一些文档章节，比如：最新发布、开始入门、Hello World 教程等等。

![](https://upload-images.jianshu.io/upload_images/7426376-1ef1b878198d0a24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后是一些相关书籍，有兴趣的同学可以看看。

### 3.2 文档核心
整个文档的核心部分是 `Working with Play` 章节，大概看一下它的结构：

![](https://upload-images.jianshu.io/upload_images/7426376-effba8e66523b6c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

它分为 Java 开发者和 Scala 开发者需要了解的内容，以及公共的主题。

这里以 Java 开发者的主要内容为例，列举需要重点了解的内容：

![](https://upload-images.jianshu.io/upload_images/7426376-21aff138053a1e47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

还有公共主题里面的重点了解内容：

![](https://upload-images.jianshu.io/upload_images/7426376-36c9b7134c6f57e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

文档的其他内容也非常重要，只是对于初级开发者来说，除非项目需要，否则只是看看即可。

## 四、在 IntelliJ IDEA 中开发 Play
这部分内容是以前写的，可能与最新版本的 Play 有一点点出入，仅供参考。

### 4.1 打开 Play 项目
首先确认已经关闭运行 Play 的命令行，这一点很重要，因为 [SBT] 构建时，采用的是单任务模式，其他任务没有退出，将不能进行下一次任务。

运行 IDEA，在欢迎页面点击 `Open`，选择下载下来的 [入门样例]：

![](https://upload-images.jianshu.io/upload_images/7426376-49b1c4c1a1c2b6ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

继续展开，选择项目目录下的 `build.sbt` 文件，点击 `OK` 按钮：

![](https://upload-images.jianshu.io/upload_images/7426376-2dfc9d390add9002.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这是作为 [SBT] 项目来打开，那么我们选择 `Open as Project`：

![](https://upload-images.jianshu.io/upload_images/7426376-5fb70e9a21d95b86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所有选项都保持默认状态，点击 `OK` 按钮，这就在 IDEA 中打开了这个项目。

**需要注意的是，你有可能会看到 IDEA 提示需要安装 Scala 插件：**

![](https://upload-images.jianshu.io/upload_images/7426376-7f6eef29339069df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击 `Install plugins`，等待所有安装完成后，重启一下 IDEA，然后再下载一些依赖，比如 `scala-sbt`，这样就可以在 IDEA 中玩耍 Play 样例了。比较舒服的是，一般这样的步骤只需要进行一次，以后即便 IDEA 版本更新，也不用对此重复劳动。当然，Scala 插件相关的更新，另当别论。

![](https://upload-images.jianshu.io/upload_images/7426376-d774512eda457af1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.2 启动 Play 项目
首先，点击图片中被红色椭圆圈中的地方（二选一）：

![](https://upload-images.jianshu.io/upload_images/7426376-a6ea55b9a3be29b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择 `Edit Configurations...` 选项，在弹出的窗口中，按照图片中的内容操作：

![](https://upload-images.jianshu.io/upload_images/7426376-f03ba192146f28d6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`Play 2 App` 和 `sbt Task` 也是二选一，通常推荐 `Play 2 App`。

如果你选择了 `sbt Task`，那么你需要做如下的处理：

![](https://upload-images.jianshu.io/upload_images/7426376-57bee2e8649b971d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

而 `Play 2 App` 只需要给定一个别名：

![](https://upload-images.jianshu.io/upload_images/7426376-4e00b48e75ca8a3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当然，如果 `localhost:9000` 不可用（比如启动多个 Play 项目的情况下），你可以在此选择其他端口。

完成以上配置后，你可以选择 `SBT` 或者 `APP`，然后点击 `Run` 按钮。

![](https://upload-images.jianshu.io/upload_images/7426376-e603cc402aa3471e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

经过一段时间等待后，在 `Play 2 App` 下，会自动打开浏览器弹出主页。

而在 `sbt Task` 下，你需要打开浏览器去访问：

```
localhost:9000
```

随后你将看到【快速启动】那一节，你所看到的页面。

# 总结
Play 像玩具一样，三岁小孩都可以轻松上手QAQ，只要你有 Java 语言基础，并对 HTTP 有一定了解，那么你就可以胜任后台开发任务。

[1]:https://www.playframework.com
[2]:http://www.easemob.com/news/3751
[3]:https://mvnrepository.com/
[4]:https://raw.githubusercontent.com/playframework/playframework/master/version.sbt
[5]:https://www.playframework.com/documentation/2.8.x/HelloWorldTutorial
[6]:https://www.playframework.com/documentation/2.8.x/Requirements
[7]:https://www.playframework.com/documentation/2.8.x/Requirements#Verifying-and-installing-sbt
[8]:https://developer.lightbend.com/start/?group=play&project=play-samples-play-java-hello-world-tutorial&_ga=2.253450825.1333703747.1576486766-1827099051.1576234536
[9]:https://developer.lightbend.com/start/?group=play&project=play-samples-play-scala-hello-world-tutorial&_ga=2.253450825.1333703747.1576486766-1827099051.1576234536
[10]:https://www.playframework.com/getting-started