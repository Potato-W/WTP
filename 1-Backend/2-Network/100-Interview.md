# 目录
1. [协议层次](#协议层次)
2. [应用层](#应用层)
3. [传输层](#传输层)
4. [网络层](#网络层)
5. [数据链路层](#数据链路层)
6. [物理层](#物理层)
7. [网络安全](#网络安全)

## 1. 协议层次 <a name="协议层次"></a>
- OSI 七层模型 vs TCP/IP 五层模型
  
  OSI: 应用层，表示层，会话层，传输层，网络层，数据链路层，物理层  
  TCP/IP: 应用层，传输层，网络层，数据链路层，物理层
 
## 2. 应用层 <a name="应用层"></a>
- HTTP请求格式
  
  _请求URI协议/版本：_  
  [请求方法]/[URI 地址] HTTP/1.1 e.g. GET /sample.jsp HTTP/1.1
  
  _请求头(Header):_  
  有关的客户端环境和请求正文的有用信息  
  常见：  
  HOST：  
  Content-type：  
  Content-length:  
  
  
  Ref: [http headers](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers)
  
  _请求内容(Body):_  
  请求头和请求内容之间以空行分割，表示区分。其内容是客户端向服务器的请求内容。  
  GET方法中，内容以明文形式写在Header中。
  POST方法中，表单写在Body中
  
  Ref：[HTTP请求格式和http响应格式](https://www.huaweicloud.com/articles/d634c17799428bf48c14156404f4a801.html)

- HTTP长连接和短连接  
  短连接： 每次客户端与服务端建立一次请求都会新创建一个TCP连接。客户机和服务器都需要分配TCP缓冲区和变量，给服务器带来严重负担。 适用于用户数目较多的Web网站，如淘宝。  
  
  长连接： 服务器响应后，TCP保持打开，同一个客户机和服务器之间的后续请求可以通过相同的连接继续传输。适用于客户数目少，操作频繁，点对点通讯。
  
- HTTP请求方法  
  GET POST HEAD PUT DELETE CONNECT OPTIONS TRACE PATCH
  
- HTTP vs HTTPs  
  1. HTTP数据明文传输，安全性较差；HTTPS数据传输过程加密，安全性好
  2. HTTP端口80；HTTPS端口443
  3. HTTPs 通过CA认证，需要收费
  4. HTTP页面响应快。因为HTTPS除了TCP3次握手，还需要SSL协商
  
- GET vs POST  
  1. GET 请求数据放在URL中，不安全； POST请求数据放在Body中，较安全。
  2. GET主要用于请求；POST用于修改/更新数据
  3. GET只支持URL编码，字符格式为ASCII；POST无限制
  4. GET对数据长度有限制，取决于浏览器；POST无限制  
  Ref： [MDN POST](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST) & [MDN GET](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET)
 
  
- 状态码  
  | 状态码 | 含义 |
  | ----  | --- |
  | 1XX | 接受请求，继续进程 |
  | 2XX | 成功接受 |
  | 3XX | 重定向 |
  | 4XX | 客户端错误 |
  | 5XX | 服务端错误 |

- HTTP/1.0 HTTP/1.1 HTTP/2.0 HTTP/3.0  
  HTTP/1.1 新加：  
  · Host. 一个服务器支持多个Web  
  · 长连接。 默认为Connection: keep-alive  
  · 断点续传  
  · 身份认证， 状态管理，Cache缓存
  
  
- DNS  
- 网站访问速度慢的问题排查  
- Cookie vs Session  
- 请求网站的过程，以www.baidu.com为例  

## 3. 传输层 <a name="传输层"></a>
- 三次握手和四次挥手
- 为什么要三次握手
- 为什么要四次握手
- 如果缺失一次握手呢
- CLOSE-WAIT和TIME-WAIT
- 为什么是2MSL
- TCP VS UDP
- 为什么TCP是可靠的
- 为什么UDP是不可靠的
- 滑动窗口
- TCP超时重传
- TCP拥塞控制


## 4. 网络层 <a name="网络层"></a>
- ARP协议

## 5. 数据链路层 <a name="数据链路层"></a>

## 6. 物理层 <a name="物理层"></a>

## 7. 网络安全 <a name="网络安全"></a>
- CSRF and XSS
- 中间人攻击


