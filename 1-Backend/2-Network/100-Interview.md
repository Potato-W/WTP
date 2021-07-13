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
  HTTP/1.1 vs HTTP/1.0：  
  · Host. 一个服务器支持多个Web  
  · 长连接。 默认为Connection: keep-alive  
  · 断点续传  
  · 身份认证， 状态管理，Cache缓存
  
  HTTP/2.0  
  · HTTP/2.0 采用二进制传输。数据分为帧，帧组成了数据流  
  · HTTP/2.0 支持多路复用  
  · HTTP/2.0 头部压缩  
  · HTTP/2.0 支持服务器推送  
  
  
- DNS  
- 网站访问速度慢的问题排查  
- Cookie vs Session  
  Cookie存于客户端，跟踪会话，存储用户偏好/用户密码等信息，不安全    
  Session存于服务端，跟踪会话，相对安全  
  
- **请求网站的过程，以www.baidu.com为例**  
  URL解析 -> DNS查询 -> TCP/IP连接 -> HTTP请求 -> 响应请求 -> 页面渲染 -> TCP断开连接  
  这一过程贯穿的知识点几乎可以撑起整个网络部分  
  
  | 过程 | 延展 |
  | --- | --- |
  | URL解析 | URL的格式、RESTful架构 |
  | DNS查询 | 递归查询、迭代查询 |
  | TCP/IP连接 | 三次握手以及相关问题 |
  | HTTP请求 | HTTP报文及相关问题 |
  | 响应请求 | 状态码，Web server |
  | 页面渲染 | HTML/CSS/JS，DOM树 |
  | TCP断开连接 | 四次挥手及相关问题 |
  
  
  Ref: [浅析从URL输入到页面展现到底发生什么](https://juejin.cn/post/6982405024630439973)
 
- URL的格式  
  https://www.test.com:443/path/index.html?key1=value1#pos  
  协议 - 域名 - 端口 - 路径 - 查询参数 - 锚点

- RESTful架构  
- Web server
  

## 3. 传输层 <a name="传输层"></a>
- 三次握手和四次挥手  
  _三次握手_  
  1. 客户端向服务端发送标识SYN，seq=x，进入SYN_SENT  
  2. 服务端收到请求，发送标识SYN/ACK，seq=y，ack=x+1, 进入SYN_RECV  
  3. 客户端收到响应，发送标识ACK，seq=x+1, ack=y+1, 进入ESTABLISHED  
  SYN: Synchronize Sequence Numbers  
  
  _四次挥手_  
  1. 客户端发送释放连接报文，标识FIN,seq=u，进入FIN_WAIT_1
  2. 服务端收到请求，发送标识ACK，seq=v，ack=u+1,进入CLOSE_WAIT(半关闭)  
  3. 客户端进入FIN_WAIT_2，等待服务端发送完毕所有数据  
  4. 服务端发送完毕所有数据，发送释放报文，标识FIN，seq=w，ack=u+1, 进入LAST-ACK  
  5. 客户端收到报文，发送确认，标识ACK，seq=u+1，ack=w+1，进入TIME_WAIT。等待2MSL后，进入CLOSE  
  6. 服务端收到报文，立即进入CLOSE   
- 为什么要三次握手  
  全双工。 双向确认服务端和客户端的发送和接受都是正常的  
  
- 为什么要四次挥手  
  全双工。 双向确认服务端和客户端都以结束传输数据额且准备关闭  
- 如果缺失一次握手呢  
  第一次握手服务器未收到，则不会进行任何相应操作。客户端会重传，当超过最大次数后，系统调用返回-1  
  第二次握手客户端未收到，会重复第一次未收到的动作，服务器阻塞于accept等待client ACK报文
  第三次未收到，会重传，超出限制后没有回应，则accept系统调用返回-1，服务端连接失败。
  
- CLOSE-WAIT和TIME-WAIT
- 为什么是2MSL
- TCP VS UDP
- 为什么TCP是可靠的
- 为什么UDP是不可靠的
- 滑动窗口
- TCP超时重传
- TCP拥塞控制
- Ping命令以及用到的协议
- 网络通信的多路复用
- ack的意义，延迟ack的意义
- 拥塞窗口要不要把自己的大小发给接收方，意义何在


## 4. 网络层 <a name="网络层"></a>
- ARP协议


## 5. 数据链路层 <a name="数据链路层"></a>

## 6. 物理层 <a name="物理层"></a>

## 7. 网络安全 <a name="网络安全"></a>
- CSRF and XSS
- 中间人攻击


