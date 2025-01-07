> Cannot locate a 64-bit Oracle Client library: "The specified module could not be found".

# Cannot locate a 64-bit Oracle Client library 解决方案

使用 cx_Oracle 模块操作 Oracle 数据时，报了一个**“无法定位64位Oracle客户端库”**的错误，由于我一直使用 DataGrip 操作数据库，没有安装 Oracle 的客户端，而且我也不想安装。

在网上参考了很多解决方案，基本都是安装 Oracle 客户端解决方式。因为，我只是用 python 写个小脚本简化一下工作，实在是没有必要与理由这么做，而且这些脚本也不是我自己使用，总不能其他人都要安装 Oracle 客户端吧？

后来，看到另一个解决方案：可以下载轻量化的 Oracle 客户端，然后配置环境变量来解决此问题，还是麻烦！因为，你不能指望所有人都会设置环境变量。

研究了半天，找到了一个解决方式：

首先，去 Oracle 官网下载对应版本的轻量化客户端，网址如下：

[Oracle Instant Client Downloads](https://www.oracle.com/database/technologies/instant-client/downloads.html)

然后，将压缩包中的所有 dll 文件复制到 python.exe 所在的目录中。例如，我是用 PyCharm 开发的程序，我的 python.exe 程序在 \venv\Scripts 目录下，复制到此即可。

此时，在 IDE 中调试程序就没有问题了！

后来，当我把程序放到其他电脑上运行的时候，又报了这个问题！

这时，就需要修改代码了！

在链接 Oracle 数据库之前，使用 cx_Oracle 中的 init_oracle_client 设置一下 Oralce 客户端即可：

```
cx_Oracle.init_oracle_client(os.getcwd() + r'\venv\Scripts')
```

此目录即之前放 dll 文件的目录。

至此，这个问题得到解决，希望能真正解决！