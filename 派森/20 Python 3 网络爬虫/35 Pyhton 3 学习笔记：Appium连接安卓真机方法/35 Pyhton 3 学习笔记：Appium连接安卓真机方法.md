> 人生苦短，我用 Python

# 环境配置

## 电脑

- Windows 7 x64 旗舰版

## 手机

- Redmi 6A（Android 9）

# 系统配置

## 安装 Appium

去 Appium [官网](http://appium.io/)下载最新版的应用即可，安装的第一步让你选择可以使用的用户（好像是这个意思吧？），我当时选的只为当前用户安装，结果报错（不知道为什么），所以选择为所有用户安装。其余的步骤就没有什么特殊的配置了，正常安装即可。

## 安装 Android Studio

去 Android Studio [官网](https://developer.android.google.cn/studio/)下载最新版的IDE即可，然后正常安装即可。安装完成之后，需要下载对应版本的 SDK ，在 File 里找到 Setting 打开，找到 Android SDK 设置页面，如下图所示：

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/Android%20SDK.jpg)

默认已经安装了一个 Android 10 的 SDK，我们只需要安装和手机系统版本对应的 SDK 即可，例如：我的手机是 Android 9.0 的，所以我只安装了一个 9.0 版本的。勾选之后，点击下方的 OK 按钮即可，IDE 会自动下载并安装（速度视电脑配置和网速而定）。

## 配置 SDK 环境变量

首先，我们在环境变量（系统和用户）中新建一个名为 ANDROID_HOME 的变量，值为 上图 Android SDK Location 中的路径；然后，进入该路径，其中有两个目录：tools 和 platform-tools，把这两个目录加到 PATH 变量中。

## 手机设置

首先，就是开启手机的开发者选项，请自行百度自己手机如何开启？一般可能就是在系统版本那里连点七下，就会开启开发者选项（我试了手里的华为和小米都是如此）。

然后，开启开发者选项，如下图所示：

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E5%BC%80%E5%8F%91%E8%80%85%E9%80%89%E9%A1%B9.jpg)

打开 USB 调试模式，这里需要将 USB 安装和 USB 调试（安全设置）两个选项打开，否则在后续的调试过程中 Appium 会报很多权限错误（小米打开这两个选项必须安装电话卡，我又去搞了张手机卡，不知道别的手机是不是这样，还是 Android 系统就是这样的），如下图所示：

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/USB%E8%B0%83%E8%AF%95.jpg)

选择默认 USB 配置中的 MTP 模式，

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/%E9%BB%98%E8%AE%A4USB%E9%85%8D%E7%BD%AE.jpg)

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/MTP%E6%A8%A1%E5%BC%8F.jpg)

至此，准备工作就全部完成了！

注意：一定要选择正规的数据线，我开始就随便用了根数据线，驱动就是死活安不上，耽误了我那么长时间！我用的数据线和电脑连接之后，能够识别手机，但是安装驱动就是出错，后来换了根原装数据线就好了！

# Appium 测试

首先，打开 Appium 程序并启动服务器，

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/Appium%20Server.jpg)

点击右上角的放大镜，启动一个会话，然后以微信为例，配置会话，

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/WebChat%20Session.jpg)

最后，点击右下角的启动会话按钮，

![](https://dioimgstore.oss-cn-beijing.aliyuncs.com/images/start%20successfully.jpg)

出现上面画面表示启动成功！