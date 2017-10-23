# 图解HTTP

### TCP/IP协议族
- 应用层：为用户提供应用服务时通信的活动，该层包括FTP,DNS(域名系统)
- 传输层：提供处于网络连接中的两台计算机之间的数据传输，包括TCP（）Transmission Control Protocol传输控制协议/UDP（User Data Protocol用户数据报协议）两个协议；
- 网络层：用来处理在网络上流动的数据包，数据包是网络传输的最小数据单位；
- 链路层：用来处理连接网络的硬件部分。

### 确保可靠的TCP协议
- 可靠的传输协议是指能够讲数据准确可靠地传给对方；TCP提供字节流服务，就是讲大块数据分割成报文段为单位的数据报进行管理。
- TCP的标识：SYN和ACK,三次握手四次松手，确认和超时重传，首部和数据检验和，流量控制等手段来保证可靠传输；

### DNS
DNS(Domain Name System域名系统)负责域名解析的服务，它提供域名和IP地址之间的解析服务。

### HTTP协议
- HTTP协议方法：GET,POST（用来传输实体主体，GET也是可以用来传输实体主体的）,PUT（传输文件）,HEAD（获取报文首部）,DELETE（删除文件）;
- 响应码，200(ok),204（No Content）301(永久重定向),302(临时重定向),304（No Modified），400(Bad Request)，401(Unauthorized未授权，需要登录验证之类的),403(Forbidden)，404（No Found），500（Internal Server Error服务器在执行请求时发生错误,也就是内部服务器错误），503（Service Unavailable服务器暂时处于超负载或正在停机维护，也就是无法提供服务）