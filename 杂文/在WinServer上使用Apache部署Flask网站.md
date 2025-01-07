> 之前在github上部署了一个博客，但是太不稳定了；后来部署在Coding Pages服务上，然后又不让用了；没办法自己买了云服务器和域名，这样再也不用看别人的脸色了。

# 在WinServer上使用Apache部署Flask网站

## 系统环境

我使用的是阿里云的 ECS 服务器，系统是 Windows Server 2016 64位数据中心版

## 部署工具

- Python
- Sublime Text
- Git
- Apache
- mod_wsgi

## 下载地址

- Apache：<https://www.apachehaus.com/cgi-bin/download.plx#APACHELEVS16>

- mod_wsgi：<https://www.lfd.uci.edu/~gohlke/pythonlibs/#mod_wsgi>

**这里要注意 mod_wsgi 的版本必须与 Python 的版本一致，还要注意是否与操作系统的位数是否一致。**

## 部署流程

### 安装工具

- 安装 Python
- 安装 Git
- 安装 Sublime Text

### 部署 Apache 服务

将下载好的 Apache 压缩包解压之后，将里面的 Apache24 文件夹复制的 C 盘中，然后在 C:\Apache24\bin 路径下启动 httpd.exe 程序，使用浏览器访问 localhost 看 Apache 是否正常运行，如看到以下页面，即表示 Apache 已经正常运行了。

目前，Apache 的示例网页只能在本机访问，我们还需要设置一下服务器安全组规则，以便可以在其他电脑访问我们的网站。

登陆阿里云，进入控制台选择服务器，选择安全组，点击配置规则。因为 Apache 默认使用 80 端口，所以我们需要将其加入的【入规则】中，如下图所示：

现在，我们在其他电脑中访问服务器，即可看到 Apache 的示例页面了。此时，也算是完成了一个小小的里程碑。

### 配置 Flask Web 运行环境

使用 git bash 和 pip 工具安装 python flask 包。

将你的 Flask Web 程序复制到服务器 C 盘中，删除不必要的文件，只保留 python 文件，template 文件夹，static 文件夹即可。

新建一个 wsgi.py 文件，代码如下：

```python
import sys


sys.path.insert(0, "C:/DIOSTUDIO")

from app import app as application
```

保存到你的 Web 程序文件夹里，与其他 py 文件放在一起即可。

### 修改 Apache 配置

- 将之前下载的 mod_wsgi 文件使用解压缩程序打开，进入 mod_wsgi\server 文件夹中，将 pyd 文件复制到 Apache 的 module 文件夹中，可以修改名称位 mod_wsgi.pyd
- 进入 conf 文件夹，打开 httpd.conf 文件，找到 LoadModule 选项，添加以下内容：

```
LoadModule wsgi_module modules/mod_wsgi.pyd
```

- 将 LoadModule vhost_alias_module modules/mod_vhost_alias.so 选项生效（即将前面的 # 删除），此选项是位之后的虚拟主机启用做准备
- 配置虚拟主机，在 httpd.conf 文件的最后输入以下内容：

```
Listen 5050
<VirtualHost *:5050>
    WSGIScriptAlias / C:\DIOSTUDIO\wsgi.py
    <Directory 'C:\DIOSTUDIO'>
        Require all granted
        Require host ip
    </Directory>
</VirtualHost>
```

端口需要改为你自己的端口；Web 文件位置也要修改为你自己的文件位置。

我这里设置的端口是 5050，所以使用 IP 访问的时候需要加上 5050 的端口号；无论是哪个端口都需要加到加到服务器安全组配置里，切记！！！

至此，整个的部署过程已经结束了！

下面可以使用浏览器访问我们的 Web 网站，看是否成功？如果未成功，可以在 Apache 的 logs 文件夹中查看日志，从而找出问题所在！

## 设置域名解析

如果有域名的话可以设置域名解析。

登陆阿里云控制台，到域名页面设置解析，将解析地址设置到我们的服务器即可。当然了，如果是国内的服务器还需要备案，自己操作一下即可。

------

## 参考文章

[Windows+Apache+mod_wsgi+Flask完全配置攻略](https://www.jianshu.com/p/0aa1c7097976)

