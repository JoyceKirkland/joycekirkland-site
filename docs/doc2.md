---
id: doc2
title: Windows10下 JAVA 环境配置
---
## 下载 JDK8

下载链接（需要注册登陆后才能下载）：

## https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html

点开之后长这样：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117143939.png)

往下滑找到这个，点下载，注意是 .exe 文件，别滑到下面去下载 .zip 文件了：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117144045.png)

# 记住你的下载路径！
---
## 安装 JDK8

在你的下载路径中找到你的 exe 文件，双击：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117144655.png)

在安装过程中有两步可以更改安装目录， 
# 文件夹要空的，并且记住你这两步的安装目录！

然后等就行了。

---
## 配置环境变量

1、Windows10 下需要手动配置。

控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 环境变量

（关键是找到高级系统设置，有些人的 Windows 可能不太一样。）

找到之后点开，找到一个环境变量，长这样：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117145217.png)

2、我们有三个环境变量要添加：

① JAVA_HOME （设置为 jdk 的安装路径）【非必须】【但是如果添加的话后面可以方便点】

② Path （添加 jdk 的 bin 文件夹所在路径）【必须】

③ Classpath（添加 jdk 的 lib 文件夹所在路径）

## 注意： 
① 你日后在配置其他库或者什么其他环境变量的时候 
# 不要也起名为 path / Path / PATH 
等等（ Windows 下不管大小写只要是这个四个字母 ），如果你不记得 Java 的 path 变量长什么样，原来的 Java 的 Path 变量很有可能会被你后来配置的其他环境变量顶掉，然后导致你的 Java 不能用！而且这个 Path 原本就是有很多其他的环境变量的（比如我的 Python 环境变量也在里面）！

② 如果你是先配置 Java （配置好了能用了）再配置其他环境的，如无例外 Java 的 Path 变量名应该是不能改了（我曾经尝试过修改成 『JAVA_PATH 』，不能用）这个时候只要将你后来配置的库或者环境变量前加一个什么标志，跟 Java 的区分开，添加完之后看看 Java 的环境变量是否跟你后来添加的其他环境变量是能共存的就行了。

像我的话就是后来配置 Opencv 的时候，把 Opencv 的 Path 命名成：『OPENCV_PATH』，然后 Java 和 Opencv 都能正常使用了。

或者说你直接在这个 Path 里面编辑再新建一个新的也可以，总之就不要直接完全新建一个 Path（就是 JAVA_HOME 的那种新建变量方式，下文会说）！

3、点开环境变量

① 系统->新建->输入变量名和变量值：
```
变量名：JAVA_HOME

变量值：你自己的jdk安装路径，就是在 exe 安装的时候第一个弹出来可以让你更改文件路径的那个。
```

如图：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117152057.png)

② 系统变量 -> Path（ Windows 下面自带的那个）：
```
添加Path变量： %JAVA_HOME%\bin
```
或者你跳过了上面 JAVA_HOME 这一步的话其实就是：
```

你自己jre1.8.0_xxx的安装路径\bin
```
如图:

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117152502.png)

③ 按照上面 JAVA_HOME 的方式新建 CLASSPATH : 
```
.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
```
# 注意这一条百分号前面是有个点和分号的喔。
---
## 验证安装

其实到这里 Java 环境变量就已经装好啦。

下面就来验证是否安装成功：

打开命令提示符( Windows 下的终端 )：在左下角搜索栏里输入『cmd』，或者快捷键 win+R 打开。

第一步输入：

```
java -version
```

若配置成功，则终端显示如下图所示：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117153144.png)


第二步输入：

```
javac
```

若配置成功，则终端显示如下图所示：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117153250.png)

第三步输入：

```
java
```

若配置成功，则终端显示如下图所示：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117153504.png)


恭喜，你的 Java 配置成功啦！

PS：如果出现：

『 ‘javac’ 不是内部或外部命令，也不是可运行的程序。』

就说明在环境变量设置中可能有路径出错了，那就从头到尾检查一遍。

如果输入 java -version 是成功的但是这一步出错了，大概率就是 jdk 的路径出错了（ JAVA_HOME 那一步）

---
## eclipse的安装

# 建议不要安装 2020 以上的最新版本！会有很多坑！很多坑！真的很多坑！我一开始就是装了2020-9版本的踩了很多坑，踩坑实录我也一并放在下面了，最后是重装下回了 2019-12 解决的！ 2019-12 的版本一点事都没有！所以这里让你们装 2019-12 的版本，如果你实在很想用最新的也行……

2019-12 版本：
# https://www.eclipse.org/downloads/packages/release/2019-12/r

其他版本选择：
# https://www.eclipse.org/downloads/packages/release

点开之后长这样，看到上面显示的是 2019-12 ，选择下面蓝色大圈里旁边的那个 windows x86_64 ：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117162427.png)

下载完之后原地解压 -> 解压之后点开和压缩包同名的文件夹 -> 点开有一个『 eclipse 』文件夹->找到『 eclipse.exe 』文件，双击点开。

在这里建议可以把它右键->固定到任务栏，下次打开就比较方便不用从文件夹里翻了。

双击 exe 文件之后会有一个弹窗，里面有一个 workspace 路径是可以改的，这个 workspace 就是你放 Java 项目的地方，我在这就改成了自己的目录。

选好目录后点右下角的『 Launch 』。

等显示出这个界面，恭喜你，已经可以开始用 Java 进行测试开发了！

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117163239.png)


---
## 新建文件与测试代码

如图

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117163406.png)

然后在弹出的窗口中的 project name 那里输入你自定义的文件名，输入完点右下角的 finish 。

Java 代码基本上都是通过『类』来实现，因此我们要运行一个 Java 程序，就必须新建一个类。

点左边你刚建好的 project ，下面有个 src 文件夹，右键 src -> new -> class。

在弹出的窗口中，下半部分有一个选项叫『public static void main(String[] args)』，如果勾选则表示编辑器会给你建好 main 主函数，这一步可不选，如果不选一会可以自己手打上去。
# 反正程序运行必须要有 main 主函数。
测试代码：

```
package java_test;//这里注意是你自己建的文件名

public class Demo {//这里注意是你自己建的Class名
	
void output()
{
	System.out.println("hello world!");
}

public static void main(String[] agrs)
{
	Demo demo1=new Demo();//实例化类
	demo1.output();
}
}
```

然后点这里运行：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117163934.png)


如果程序无误，就能看到输出结果啦：

![](https://image-up-1304421499.cos.ap-guangzhou.myqcloud.com/img/20210117163955.png)

---
## eclipse 的一点使用技巧

放大：ctrl+shift+『+』（键盘上的+号）

缩小：ctrl+『-』（键盘上的减号）（我也不知道为什么）

代码分屏：ctrl+shift+『-』（键盘上的-号）功能应该是可以两边对比，然后再按一遍就可以还原了

---
## 奇奇怪怪的踩坑实录

都是 2020 以上版本的问题，2019-12 版本无事发生。

eclipse 下载好之后双击 exe 发现弹出来一个报错：

『Version 1.8.0_201 of the JVM is not suitable for this product. Version: 11 or greater is required.』

解决办法：
# https://blog.csdn.net/jcmj123456/article/details/109020920





