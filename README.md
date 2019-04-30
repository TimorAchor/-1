# 基础知识
在写爬虫之前需要了解的一些基础知识

HTTP原理
URI：Uniform Resource Identifier 统一资源标志符
URL: Uniform Resource Locator 统一资源定位符
（UPL是URI的子集）

超文本：hypertext,如网页的源代码HTML就可以称作超文本
HTTP: Hyper Text Transfer Protocol 超文本传输协议
HTTPS: Hyper Text Transfer Protocol Secure Socket Layer  简单讲是HTTP的安全版，即HTTP下加入SSL层


请求：
请求，由客户端向服务端发出，可以分为4部分内容：请求方法(Request Method)、
请求的网址(Request URL)、请求头(Request Header)、请求体(Request Body).

请求方法：
常见的请求方法有两种:GET和POST
二者有以下区别：
1.GET请求中的参数包含在URL里面，数据可以在URL中看到，而POST请求的URL不会包含这些数据，
数据都是通过表单形势传输的，会包含在请求体中。
2.GET请求提交的数据最多只有1024个字节，而POST方法没有限制。

其他请求方法：
GET	请求指定的页面信息，并返回实体主体。
HEAD	类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头
POST	向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。
PUT	从客户端向服务器传送的数据取代指定的文档的内容。
DELETE	请求服务器删除指定的页面。
CONNECT	HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。
OPTIONS	允许客户端查看服务器的性能。
TRACE	回显服务器收到的请求，主要用于测试或诊断。

请求头：
请求头，用来说明服务器要使用的附加信息,比较重要的信息有Cookie，Referer，User—Agent等。

请求体：
请求体一般承载的内容是POST请求中的表单数据，而对GET请求，请求体则为空
！Content-Type和POST提交数据的关系！
application/x-www-form-urlencoded   表单数据
multipart/form-data                 表单文件上传
application/json                    序列化JSON数据
text/xml                            XML数据

响应：
响应，由服务器返回给客户端，可以分为三个部分：响应状态码(Response Status Code)、响应头(Response Header)、响应体(Response Body).

响应状态码：
下面是常见的HTTP状态码：
200 - 请求成功
301 - 资源（网页等）被永久转移到其它URL
404 - 请求的资源（网页等）不存在
500 - 内部服务器错误
https://www.runoob.com/http/http-status-codes.html  更多响应码访问

响应头：
响应头包含了服务器对请求的应答信息，如Content-Type、Server、Set-Cookie等。下面简要说明一些常用的头信息:
Date: 标识响应产生的时间。
Last-Modified：指定资源的最后修改时间
Content-encoding: 指定响应内容的编码
Server:包含服务器的信息，比如名称、版本号等。
Content-Type:文档类型，指定返回的数据类型是什么
Set-Cookie:设置Cookie.响应头中的Set-Cookie告诉浏览器需要将此内容放在Cookies中，下次请求携带Cookies请求
Expires:指定响应的过期时间，可以使代理服务器或浏览器将加载的内容更新到缓存中。如果再次访问时，就可以直接从缓存中加载,降低服务器负载，缩短加载时间。

响应体：
相应的正文数据都在响应体中，比如请求网页时，它的响应体就是网页的HTML代码；
请求一张图片时，它的响应体就是图片的二进制数据。我们做爬虫请求网页后，要解析的内容就是响应体。


爬虫的基本原理：
爬虫概述：简单来说，爬虫就是获取网页并提取和保存信息的自动化程序
1.获取网页
爬虫首先要做的就是获取网页的源代码，Python中有urlib、request等库帮助我们获取。

2.提取信息
最通用的方法是采用正则表达式提取，这是一个万能的方法，但是在构造正则表达式时比较复杂且容易出错。
另外，由于网页的结构有一定的规则，所以还有一些根据网页结点属性、CSS选择器或XPath来提取网页信息的库，
如Beautiful Sou、pyquery、lxml等。使用这些库，我们可以高效快速地从中提取网页信息，如节点的属性、文本值等。
提取信息是爬虫非常重要的部分，它可以使杂乱的数据变得条理清晰，以便我们后续处理和分析数据。

3.保存数据
提取信息后，我们一般会将提取到的数据保存到某处以便后续使用。这里保存形式多种多样，
如可以简单保存为TXT文本或JSON文本，也可以保存到数据库，如MySQL和MongoDB等，也可以
保存至远程服务器，如借助SFTP进行操作等。

4.自动化程序
说到自动化程序，意思是说爬虫可以代替人来完成这些操作。首先，我们手工当然可以提取这些信息，
但是当量特别大或者想快速获取大量数据的话，肯定还是要借助程序。爬虫就是代替我们完成这份工作的自动化程序，
它可以在抓取过程中进行各种异常处理、错误重试等操作，确保爬取持续高效地进行。

会话(session)和cookies
会话：
会话对象用来储存特定用户会话所需的属性及配置信息。
Cookies:
指某些网站为了辨别用户身份、进行会话跟踪而存储在用户本地终端上的数据。

代理的基本原理：
代理实际上指代理服务器，是网络信息的中转站，实现IP伪装。


























