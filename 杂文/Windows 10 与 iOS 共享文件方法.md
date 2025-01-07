> 苹果和微软的浪漫

# Windows 10 与 iphone 共享文件方法

​	iPhone 和 Mac 之间可以共享剪切板、传送文件等，华为电脑和手机之间除了可以共享剪切板、传送文件以外，更是可以多屏协同！那么，iPhone和PC之间是否可以共享剪切板、传送文件么？而不是通过微信的文件传输助手。

## 准备工作

### 环境参数

- 电脑端系统：Windows 10
- 手机端系统：iOS 18.1.1

### 内容准备

​	获取电脑在局域网中的 IPv4 地址，按 Windows + R 键打开运行窗口，输入 cmd 打开命令行工具。在命令行工具中输入 ipconfig 以获取电脑的 IPv4 地址，如下图所示：

![image-20241203145640601](https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/image-20241203145640601.png)

​	电脑还需要设置开机密码，如果是使用微软账号登录的，密码就是设置的 PIN 码；如果是本地用户登录的，在账户里设置一个开机密码即可。

​	除了以上内容，还需要知道当前登录的账号，可以在命令行工具中输入 whoami 命令获取，如下图所示：

![image-20241203131858583](https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/image-20241203131858583.png)

​	知道了电脑的 IPv4 地址和账号，并设置了密码就可以实现了！

## 实现方法

​	以下只能在同一个局域网内生效，即电脑和手机连接在同一个网络中。

- 在电脑端创建一个文件夹，右键打开属性，在共享页点击“共享”按钮，弹出的对话框中下拉选择添加 Everyone，权限级别选择“读取/写入”，如下图所示：

  ![image-20241203111716424](https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/image-20241203111716424.png)

- iPhone 端需要安装**文件**应用，打开**文件**应用，点击右上角的三个点，选择“连接服务器”，如下图所示：

  <img src="https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/%E8%BF%9E%E6%8E%A5%E5%85%B1%E4%BA%AB.png" style="zoom:25%;" />

- 服务器地址输入电脑的 IPv4 地址，然后输入登录信息，如下图所示：

  <img src="https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/%E7%99%BB%E5%BD%95%E4%BF%A1%E6%81%AF.png" style="zoom:25%;" />

- 点击下一步即可完成，效果如下图所示：

  <img src="https://diopicstore.oss-cn-wulanchabu.aliyuncs.com/pictures/%E6%95%88%E6%9E%9C%E5%B1%95%E7%A4%BA.png" style="zoom:25%;" />

  ## 写在最后

  ​	这样，我们就可以不通过微信或者连接数据线在两个设备之间共享图片、文档等文件了！
