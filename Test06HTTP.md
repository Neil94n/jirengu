# HTTP入门

### 什么是HTTP?

**超文本传输协议**（[英文](https://zh.wikipedia.org/wiki/%E8%8B%B1%E6%96%87)：**H**yper**T**ext **T**ransfer **P**rotocol，[缩写](https://zh.wikipedia.org/wiki/%E7%B8%AE%E5%AF%AB)：**HTTP**）是一种用于分布式、协作式和[超媒体](https://zh.wikipedia.org/wiki/%E8%B6%85%E5%AA%92%E9%AB%94)信息系统的[应用层协议](https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E5%B1%82)[[1\]](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE#cite_note-ietf2616-1)。HTTP是[万维网](https://zh.wikipedia.org/wiki/%E5%85%A8%E7%90%83%E8%B3%87%E8%A8%8A%E7%B6%B2)的数据通信的基础。

设计HTTP最初的目的是为了提供一种发布和接收[HTML](https://zh.wikipedia.org/wiki/HTML)页面的方法。通过HTTP或者HTTPS协议请求的资源由[统一资源标识符](https://zh.wikipedia.org/wiki/%E7%B5%B1%E4%B8%80%E8%B3%87%E6%BA%90%E6%A8%99%E8%AD%98%E7%AC%A6)（Uniform Resource Identifiers，URI）来标识。

HTTP的发展是由[蒂姆·伯纳斯-李](https://zh.wikipedia.org/wiki/%E6%8F%90%E5%A7%86%C2%B7%E6%9F%8F%E5%85%A7%E8%8C%B2-%E6%9D%8E)于1989年在[欧洲核子研究组织](https://zh.wikipedia.org/wiki/%E6%AD%90%E6%B4%B2%E6%A0%B8%E5%AD%90%E7%A0%94%E7%A9%B6%E7%B5%84%E7%B9%94)（CERN）所发起。HTTP的标准制定由[万维网协会](https://zh.wikipedia.org/wiki/%E5%85%A8%E7%90%83%E8%B3%87%E8%A8%8A%E7%B6%B2%E5%8D%94%E6%9C%83)（World Wide Web Consortium，W3C）和[互联网工程任务组](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E4%BB%BB%E5%8A%A1%E7%BB%84)（Internet Engineering Task Force，IETF）进行协调，最终发布了一系列的[RFC](https://zh.wikipedia.org/wiki/RFC)，其中最著名的是1999年6月公布的 [RFC 2616](https://tools.ietf.org/html/rfc2616)，定义了HTTP协议中现今广泛使用的一个版本——HTTP 1.1。

## 协议概述

HTTP是一个客户端终端（用户）和服务器端（网站）请求和应答的标准（[TCP](https://zh.wikipedia.org/wiki/TCP)）。通过使用[网页浏览器](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E7%80%8F%E8%A6%BD%E5%99%A8)、[网络爬虫](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB)或者其它的工具，客户端发起一个HTTP请求到服务器上指定端口（默认[端口](https://zh.wikipedia.org/wiki/%E7%AB%AF%E5%8F%A3)为80）。我们称这个客户端为用户代理程序（user agent）。应答的服务器上存储着一些资源，比如HTML文件和图像。我们称这个应答服务器为源服务器（origin server）。在用户代理和源服务器中间可能存在多个“中间层”，比如[代理服务器](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%90%86%E4%BC%BA%E6%9C%8D%E5%99%A8)、[网关](https://zh.wikipedia.org/wiki/%E7%BD%91%E5%85%B3)或者[隧道](https://zh.wikipedia.org/wiki/%E9%9A%A7%E9%81%93)（tunnel）。

尽管[TCP/IP](https://zh.wikipedia.org/wiki/TCP/IP)协议是互联网上最流行的应用，HTTP协议中，并没有规定必须使用它或它支持的层。事实上，HTTP可以在任何互联网协议上，或其他网络上实现。HTTP假定其下层协议提供可靠的传输。因此，任何能够提供这种保证的协议都可以被其使用。因此也就是其在TCP/IP协议族使用TCP作为其传输层。

通常，由HTTP客户端发起一个请求，创建一个到服务器指定端口（默认是80端口）的TCP连接。HTTP服务器则在那个端口监听客户端的请求。一旦收到请求，服务器会向客户端返回一个状态，比如"HTTP/1.1 200 OK"，以及返回的内容，如请求的文件、错误消息、或者其它信息。

## 请求方法

HTTP/1.1协议中共定义了八种方法（也叫“动作”）来以不同方式操作指定的资源：

- GET

  向指定的资源发出“显示”请求。使用GET方法应该只用在读取数据，而不应当被用于产生“副作用”的操作中，例如在[Web Application](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F)中。其中一个原因是GET可能会被[网络蜘蛛](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E8%9C%98%E8%9B%9B)等随意访问。参见[安全方法](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE#%E5%AE%89%E5%85%A8%E6%96%B9%E6%B3%95)

- HEAD

  与GET方法一样，都是向服务器发出指定资源的请求。只不过服务器将不传回资源的本文部分。它的好处在于，使用这个方法可以在不必传输全部内容的情况下，就可以获取其中“关于该资源的信息”（元信息或称元数据）。

- POST

  向指定资源提交数据，请求服务器进行处理（例如提交表单或者上传文件）。数据被包含在请求本文中。这个请求可能会创建新的资源或修改现有资源，或二者皆有。

- PUT

  向指定资源位置上传其最新内容。

- DELETE

  请求服务器删除Request-URI所标识的资源。

- TRACE

  回显服务器收到的请求，主要用于测试或诊断。

- OPTIONS

  这个方法可使服务器传回该资源所支持的所有HTTP请求方法。用'*'来代替资源名称，向Web服务器发送OPTIONS请求，可以测试服务器功能是否正常运作。

- CONNECT

  HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。通常用于SSL加密服务器的链接（经由非加密的HTTP代理服务器）。

方法名称是区分大小写的。当某个请求所针对的资源不支持对应的请求方法的时候，服务器应当返回[状态码405](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#405)（Method Not Allowed），当服务器不认识或者不支持对应的请求方法的时候，应当返回[状态码501](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#501)（Not Implemented）。

### 状态码

所有HTTP响应的第一行都是**状态行**，依次是当前HTTP版本号，3位数字组成的[状态代码](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81)，以及描述状态的短语，彼此由空格分隔。

状态代码的第一个数字代表当前响应的类型：

- [1xx消息](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#1xx%E6%B6%88%E6%81%AF)——请求已被服务器接收，继续处理
- [2xx成功](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#2xx%E6%88%90%E5%8A%9F)——请求已成功被服务器接收、理解、并接受
- [3xx重定向](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#3xx%E9%87%8D%E5%AE%9A%E5%90%91)——需要后续操作才能完成这一请求
- [4xx请求错误](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#4xx%E8%AF%B7%E6%B1%82%E9%94%99%E8%AF%AF)——请求含有词法错误或者无法被执行
- [5xx服务器错误](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81#5xx%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%94%99%E8%AF%AF)——服务器在处理某个正确请求时发生错误

## 请求与响应

下面是一个HTTP客户端与服务器之间会话的例子，运行于www.baidu.com，端口80。我们可以通过Chrome开发者工具查看HTTP的请求与响应内容。

### 请求

首先我们需要打开电脑的命令行工具输入：

```bash
curl -s -v -H "Neil : xxx" -- "https://www.baidu.com"
```

##### 请求的内容为：

```
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.55.1
Accept: */*
Neil: xxx
```

我们还可以通过其他的方法来发送请求：

```bash
curl -X POST -d "1234567890" -s -v -H "Neil : xxx" -- "https://www.baidu.com"
```

##### 请求的内容为：

```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.55.1
Accept: */*
Neil: xxx
Content-Length: 10
Content-Type: application/x-www-form-urlencoded

[10 bytes data]
```

##### 请求的格式：

```
1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据
```

我们可以得出结论一个完整的HTTP请求包含4个部分，分别为请求行、请求头、空行、其他的消息体，其中第四部分有时也可以为空。

#### 如何用 Chrome 查看请求内容

1. 打开 Chrome浏览器F12进入开发者工具点击Network
2. 地址栏输入网址，比如：www.baidu.com
3. 在 Network 点击，查看 request，点击「view source」
4. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到了

### 响应

请求了之后，应该都能得到一个响应，除非断网了，或者服务器宕机了。

##### 响应示例

上面两个请求的响应分别为

```
HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

[2443 bytes data]
```

```
HTTP/1.1 302 Found
Connection: Keep-Alive
Content-Length: 17931
Content-Type: text/html
Date:  Thu, 01 Nov 2018 13:08:49 GMT
Etag: "54d9749e-460b"
Server: bfe/1.0.8.18

[3824 bytes data]
```

1. GET 请求和 POST 请求对应的响应可以一样，也可以不一样
2. 响应的第四部分可以很长很长很长

##### 响应的格式

```
1 协议/版本号 状态码 状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容
```

#### 如何用 Chrome 查看响应内容

1. 打开 Chrome浏览器F12进入开发者工具点击Network

2. 地址栏输入网址，比如：www.baidu.com

3. 在 Network 点击，查看 Response Headers，点击「view source」

4. 如果有请求的第四部分，点击查看Response或者Preview就可以了
