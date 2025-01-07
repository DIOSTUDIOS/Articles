### 第三章 Chrome 分析网站

#### 3.1 Chrome 开发工具

- 开发者模式
- 爬虫分析 —— 熟练掌握 Elements 和 Network 标签，其中 Network 是核心

#### 3.2 Elements 标签

- 分为两个部分
  - 区域 1：网页的 HTML 信息
  - 区域2：
    - Styles：当前选中内容的 CSS 样式
    - Computed：当前选中内容的边距属性、边框属性，用图像显示一个整体效果
    - Event Listeners：整个网页事件触发的 JavaScript，该功能可以快速定位 JS 的位置

#### 3.3 Networ 标签

- Controls：控制 Network 的外观和功能
- Filters：控制 RequestsTable 具体显示的内容
  - All：返回当前页面全部加载的信息
  - XHR：筛选 Ajax 的请求链接信息
  - JS：筛选 JavaScript 文件
  - CSS：CSS样式内容
  - Img：网页加载的图片
  - Media：加载的媒体信息，如mp3、mp4等音频视频文件
  - Doc：Html 文件，主要用于响应当前 url 的网页内容
- Overview：显示获取到请求的时间轴信息
- Requests Table：按先后顺序显示所有捕捉到的请求信息
- Summary：显示总的请求数，数据传输量，加载时间等信息

其中，Requests Table 是合同部分，主要作用是记录每个请求信息，每条请求信息划分为 5 个标签：

- Headers：该请求的 HTTP 头信息
- Preview：根据请求类型显示预览
- Response：显示 HTTP 的 response 信息
- Cookies：显示 HTTP 的 request 和 response 过程中的 cookies 信息
- Timing：显示请求在整个生命周期中各部分花费的时间

常用的标签有 Headers、Preview 和 Response，Headers 用于获取请求链接、请求头和请求参数；Preview 和 Response 用于显示服务器返回的响应内容。

Headers 标签划分未以下四个部分：

- General：记录请求链接、请求方式和请求状态码
- Response Headers：服务器的响应头，其参数说明如下：
  - Cache-Control：指定缓存机制，优先级大于 Last-Modified
  - Connection：包含很多标签列表，常见的是 Keep-Alive（保持 TCP 链接）和 Close（断开 TCP 链接）
  - Content-Encoding：服务器的数据压缩格式
  - Content-Length：返回数据的长度
  - Content-Type：返回数据的类型
  - Date：当前时间值
  - Keep-Alive：在 Connection 未 Keep-Alive 时该字段才生效，用来说明服务器估计保留连接的时间和允许后续几个请求复用这个保持着的连接
  - Server：服务器的类型
  - Vary：明确告知缓存服务器按照 Accept-Encoding 字段的内容分别缓存不同的版本
- Request Headers：客户端的请求头，其参数说明如下：
  - Accept：客户端支持的数据类型
  - Accept-Encoding：客户端支持的数据压缩格式
  - Accept-Charset：客户端可以处理的字符集类型
  - Cache-Control：缓存控制，服务器控制客户端要不要缓存数据
  - Connection：处理完本次请求后，是断开连接还是保持连接
  - Cookie：客户端可通过 Cookie 向服务器发送数据，让服务器识别不同的客户端
  - Host：访问的服务器名
  - Referer：包含一个 url，客户端从该 url 代表的页面出发并访问当前请求的页面，当浏览器向服务器发送请求的时候，一般会带上 Referer，告诉服务器当前请求是从哪个页面 url 过来的，服务器借此可以获得一些信息用户处理
  - User-Agent：用户代理，使服务器能够识别客户端的系统及版本、CPU 类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等
- Query String Parameters：请求参数，主要是将参数按照一定的形式（GET 和 POST）传递给服务器，服务器通过接收器参数进行对应的响应，这是客户端和服务器进行数据交互的主要方式之一

在实际使用过程中，只需要关心请求链接、请求方式、请求头和请求参数的内容即可。而 Preview 和 Response 是服务器返回的结果，两者之间对不同的响应结果有不同的显示方式：

- 如果返回的是图片，则 Preview 表示可显示的图片内容，而 Response 表示无法显示
- 如果返回的是 Html 或 JSON，则两者都可显示，只是在格式上可能存在细微的差异

###  第五章 爬虫库 Urllib

#### 5.1 Urllib 简介

在 Python 3 中，Urllib是一个收集几个模块来使用 URL 的软件包，大致具备以下功能：

- urllib.request：用于打开和读取 URL
- urllib.error：用于接收 urllib.request 产生的异常
- urllib.parse：用于解析 URL
- urllib.robotparser：用于解析 robots.txt 文件

#### 5.2 发送请求

`urllib.request.urlopen(url, data=None, [timeout, ]*, cafile=None, capath=None, cadefault=False, context=None)`

- url：需要访问的网站的地址
- data：默认为 None，Urllib 判断参数 data 是否为 None 从而区分请求方式。若参数为 None 则代表请求方式为 GET；反之请求方式为 POST，参数 data 以字典方式存储数据，并将参数 data 由字典类型转换为字节类型才能完成 POST 请求
- timeout：超时设置，指定阻塞操作（请求时间）的超时（若未指定，则使用全局默认超时设置）
- cafile、capath 和 cadefault：使用参数指定一组 HTTPS 请求的可信 CA 证书；cafile 应指向一组 CA 证书的单个文件；capath 应指向证书文件的目录；cadefault 通常使用默认值即可
- context：描述各种 SSL 选项的实例

在实际使用中，常用的参数有 url、data 和 timeout。若遇到证书验证，则可将其直接关闭，也可以设置参数指向证书的信息和位置。

当对网站发送请求时，网站会返回响应内容，urlopen 对象提供获取网站响应内容的方法函数：

- read()/readline()/readlines()/fileno()/close()：对 HTTPResponse 类型数据操作
- info()：返回 HTTPMessage 对象，表示服务器返回的头信息
- getcode()：返回 HTTP 状态码
- geturl()：返回请求的 URL

#### 5.3 复杂的请求

声明一个 request 对象，该对象可自定义 header（请求头）等请求信息

`urllib.request.Request(url, data=None, headers={}, method=None)`

- url：完整格式的 url，与 urllib.request.urlopen() 的参数一致
- data：请求参数，与 urllib.request.urlopen() 的参数一致
- headers：设置 request 请求头信息
- method：设定请求方式，主要是 POST 和 GET

#### 5.4 代理 IP

原理：以本机先访问代理 IP，在通过代理 IP 地址访问互联网，这样服务器接收到的访问 IP 就是代理 IP 的地址。

Urllib 提供的 urilib.request.ProxyHandler() 方法可动态设置代理 IP 池，代理 IP 以字典的方式写入方法。完成代理 IP 设置后，将设置好的代理 IP 写入 urllib.request.build_opener() 方法生成 opener 对象，然后通过 open() 方法向网站发送请求。

#### 5.5 使用 Cookies

#### 5.6 证书验证

#### 5.7 数据处理

### 第六章 Requests 简介及安装

#### 6.2 请求方式

HTTP 的常用请求方式为 GET 和 POST ，Requests 对此区分两种不同的请求方式。GET 请求时需要以字典的形式设置 params 参数；POST 请求时需要以字典的形式设置 data 参数。

当客户端向服务器发送请求时，服务器会返回相应的响应（response）对象，包含服务器的响应信息：

- status_code：响应状态码
- raw：原始响应体，使用 response.raw.read() 读取
- content：字节形式的响应体，需要进行解码
- text：字符串形式的响应体，会自动根据响应头的字符编码进行解码
- headers：以字典形式存储服务器的响应头（字典键不区分大小写，若键不存在，则返回 None）
- json：Requests 中内置的 JSON 解码器
- raise_for_status：请求失败，抛出异常
- url：获取请求链接
- cookies：获取请求后的 cookies
- encoding：获取编码格式

### 第七章 Requets-Cache 爬虫缓存

#### 7.2 在 requests 中使用缓存

整个缓存机制由  install_cache() 方法实现

`install_cache(cache_name='cache', backend=None, expire_after=None, allowable_codes=(200, ), allowable_methods=('GET', ), session_factory=CachedSession, **backend_options)`

- cache_name：对缓存的存储文件命名，默认为 cache
- backend：设置缓存的存储机制，默认为 None（即 sqlite 数据库存储）
- expire_after：设置缓存的有效时间，默认为 None（即永久有效）
- allowable_codes：设置 HTTP 的状态码，默认为 200
- allowable_methods：设置请求方式，默认是只允许 GET 请求才能生成缓存
- session_factory：设置缓存的执行对象，由 CachedSession 类实现，该类由 Requests-Cache 定义
- **backend_options：设置存储配置，若缓存的存储选择 sqlite、redis 或 mongoDB 数据库，则该参数是设置数据库的连接方式

