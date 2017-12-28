## 通过GAPID分析和弄清app的GPU运作

原文地址：https://android-developers.googleblog.com/2017/12/diagnose-and-understand-your-apps-gpu_13.html

作者是软件工程师 PAndrew Woloszyn

为3D进行开发是很复杂的，不管你是用原生的图形API或者是借助你最喜爱的游戏引擎，都有数千条图形指令，你需要把它们完美地搭配在一起才能在你的手机或电脑或VR头戴设备中生成美丽的3D图像。

[GAPID ( Graphics API Debugger 图形API调试器)](https://developers.google.com/vr/tools/gapid)是一个新的能帮助开发者分析在应用程序中图形的生成和性能问题的工具。通过GAPID，你可以捕捉到应用程序的图形轨迹并且步进每一条图形命令。这可以让你看到你最终的图像是怎么形成的并且将有问题的调用分离出来，所以你在试错上会花更少的时间。

GAPID 支持 Android 上的 OpenGL ES 和 Vulkan , Windows 和 Linux 。

![](https://3.bp.blogspot.com/-ut-Ed4OeCHI/WjCAvs_aWdI/AAAAAAAAE3o/N56-WPhSNm8ONeCvWHkMWSEYPfysHzOpACLcBGAs/s1600/image2.gif)
*按绘制函数一个接一个调试*

GAPID 不但能分析你的图像生成指令的问题，还可以改变这些指令并运行一个快速的测试去看看会如何影响当前显示的帧。

下面是一些关于在什么情况下GAPID能帮你挑出你应用程序的问题并且修正它的例子：

### GAPID是做什么的?

![](https://4.bp.blogspot.com/-u1zx8IJeo3Q/WjCAKWyxWNI/AAAAAAAAE3c/-nL6OS90cUU8FpFQev57j9PzVj7FvQEWQCLcBGAs/s1600/image1.gif)
*为什么我的文本不显示？！*

当你用一个图形API却没有得到预期结果，会很让人灰心,无论它是一个空白的屏幕显示，一个上下颠倒的三角形，还是一个缺失的网格。作为一个离线的调试器,GAPID能让你记录这些应用程序的图形生成轨迹，然后会检查函数调用。你可以通过查看帧缓存追踪具体是哪条指令导致了不正确的结果，并且检查在那个点的状态，对分析问题有帮助。

### 如果执行某个操作会怎样？

![](https://2.bp.blogspot.com/-o6ZkArxfVjE/WjCAerAsozI/AAAAAAAAE3k/xIbFTI30ai46zkCQudrQUaTfs8SDKrYmgCLcBGAs/s1600/image3.gif)
*使用 GAPID 去编辑着色器代码*

即使当程序按预期执行，有时你也想试验别的东西。 GAPID 允许你任意修改 API 调用和着色器，所以你可以像下面这样测试：

* 如果我让这个物体呈现不同的质感？
* 如果我在这个着色器里面更改花朵的计算方式？

有了 GAPID ，不用重新编译你的应用程序或重建你的图形资源，你现在直接迭代指令就可以从视觉上观察应用程序的变化。

不管你是在用 Vulkan 开发一个新的很棒的电脑游戏或在 Android 上想实现沉浸式的虚拟现实体验，我们希望在最大化利用你的GPU上面GAPID可以为你节省时间也不会你失望。为了开始使用 GAPID 并且发现它的强大之处，[下载它](https://github.com/google/gapid/releases)，选你最喜欢的应用程序，[捕捉其图形生成轨迹](https://google.github.io/gapid/tutorials/capturetrace)！
