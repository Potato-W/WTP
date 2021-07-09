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
  [请求方法]/[URI 地址] HTTP/1.1 e.g. GET/sample.jsp HTTP/1.1
  
  _请求头:_  
  有关的客户端环境和请求正文的有用信息  
  ref: [http headers](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers)
  
  _请求内容:_  
  
  
  
  参考：[HTTP请求格式和http响应格式](https://www.huaweicloud.com/articles/d634c17799428bf48c14156404f4a801.html)
- HTTP长连接
- HTTP请求方法
- HTTP vs HTTPs
- GET vs POST
- 状态码
- HTTP/1.0 HTTP/1.1 HTTP/2.0 HTTP/3.0
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


