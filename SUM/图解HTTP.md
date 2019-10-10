# 第一章
## 三次握手
	握手过程使用了TCP 的标志(flag)--SYN(synchronize)和ACK(acknowledgement)
	1、发送端首先发送一个带SYN标志的数据包给对方。
	2、接收端收到后，回传一个带有SYN/ACK标志的数据包以示传达确认信息。
	3、最后，发送端再回传一个带有ACK标志的数据包，代表"握手"结束
![](https://github.com/GreatWei/Book/blob/master/IMG/http/1-1.jpg)

# 第二章
## HTTP是不保存状态的协议
## 告知服务器意图的HTTP方法
	*GET: 获取资源
	*POST: 传输实体主体
	*PUT: 传输文件
	*HEAD:获取报文首部
		HEAD方法和GET方法一样，只是不返回报文主体部分。用于确认URI的有效性及资源跟新的日期时间等
	*DELETE:删除文件
	*OPTIONS:询问支持的方法
	*TRACE:追踪路劲
	*CONNECT: 要求用隧道协议连接代理
		CONNECT方法要求在与代理服务器通信时建立隧道，实现隧道协议进行TCP通信。
		主要使用SSL(安全套接层)和TLS(传输层安全)协议把通信内容加密后经网络隧道传输。
![](https://github.com/GreatWei/Book/blob/master/IMG/http/2-1.jpg)
	
## 持久链接
	持久连接旨在建立1次TCP连接后进行多次请求和响应的交互
## 管线化
	持久连接使得多数请求以管线化(pipelining)方式发送成为可能。从前发送请求后需要等待并接受响应，才能
	发送下一个请求。管线化出现后，不用等待响应亦可以直接发送下一个请求。

# 第三章
	压缩传输的内容编码，常用的内容编码：
		gzip、compress、deflate(zlib)、identity(不进行编码)
	压缩后的实体，最后一块会使用"0(CR+LF)"来标记
	
	获取部分内容的范围请求：
		Range：bytes=50001-10000 
		Range：bytes=50001-
		Range：bytes=-3000,5000-7000 (从一开始到3000字节和5000-7000字节的多重范围)
	