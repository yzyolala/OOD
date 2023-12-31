## URL

![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2002.13.41.png?raw=true)

这幅图展示了当你在浏览器中输入一个URL（统一资源定位符）时会发生什么。流程如下：

用户输入URL：

用户（在图中称为Bob）在浏览器地址栏中输入一个URL。例如：http://example.com/product/electric/phone。
URL由不同部分组成，包括协议（http://），域名（example.com），路径（/product/electric）和资源（/phone）。
DNS解析：

浏览器首先在本地DNS缓存中查找URL对应的IP地址。
如果没有找到，浏览器会发起递归DNS查询。浏览器会请求配置的DNS解析器（DNS Resolver）去找出域名对应的IP地址。
DNS解析器会向一系列DNS服务器查询，直到找到域名对应的IP地址。
建立TCP连接：

一旦浏览器获取到IP地址，它会与目标服务器建立一个TCP连接。这通常涉及到一个TCP三次握手过程。
与服务器交互：

TCP连接建立后，浏览器可以向服务器发送HTTP请求，并接收服务器返回的HTTP响应。这个HTTP响应通常是请求的网页数据，浏览器会渲染这些数据，展示给用户看。
这个图还展示了"零拷贝"读取的概念，即在这个过程中没有不必要的数据复制，直接从磁盘读取数据到网络接口，但这个部分在图中不是很明显。

整体来看，这幅图说明了从用户输入URL到页面显示在用户面前的整个过程，涵盖了DNS解析和与服务器建立连接的关键步骤。

## TCP三次握手（Three-way Handshake）

是一个网络协议中的术语，用来描述在TCP/IP网络中建立一个可靠的连接过程。这个过程确保了双方都准备好接收和发送数据。以下是三次握手的具体步骤：

SYN：

客户端发送一个SYN（同步序列编号）包到服务器，以开启一个新的连接。
这个包里包含一个随机序列号A，用来作为数据传输的起始点。
SYN-ACK：

服务器接收到客户端的SYN包后，如果同意建立连接，则会返回一个SYN-ACK（同步确认）包。
服务器的SYN-ACK包中也包含一个随机序列号B，同时对客户端的序列号A进行确认（ACK），确认号为A+1。
ACK：

客户端收到服务器的SYN-ACK包后，会发送一个ACK（确认）包作为响应。
客户端的ACK包中的确认号是B+1，同时序列号是A+1，确认了服务器的初始序列号。
在三次握手之后，TCP连接就建立了，客户端和服务器就可以开始双向通信了。这个过程保证了两端都知道对方已经准备好接收数据，并且交换了初始序列号用于后续的数据传输中确保数据的顺序和完整性。三次握手也是为了防止已经失效的连接请求突然又传送到了服务器端，造成资源的浪费。

## https

![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2000.22.11.png?raw=true)


这幅图展示了 HTTPS（超文本传输安全协议）连接的建立过程，它是一个加密的通信协议，用于在客户端和服务器之间安全地传输数据。图中详细阐述了一个典型的 HTTPS 握手流程，包括以下几个关键步骤：

TCP 握手：这是建立网络连接的第一步，使用 TCP 协议完成。客户端和服务器交换 SYN（同步）和 ACK（确认）消息来建立连接。

证书检查：服务器向客户端发送其 SSL/TLS 证书。客户端验证证书的有效性，这包括检查证书是否由受信任的证书颁发机构签发，证书是否没有过期，并且证书上的域名是否与服务器的域名匹配。

密钥交换：

客户端创建一个随机的会话密钥（session key），用于后续的对称加密。
使用服务器的公钥加密会话密钥，并发送给服务器。
服务器使用其私钥解密会话密钥。
数据传输：

通信双方现在拥有了相同的会话密钥，可以用于对称加密。
客户端和服务器使用会话密钥加密通信数据，保证数据的机密性和完整性。
图中展示了两种加密方法：

非对称加密（Asymmetric Encryption）：在握手过程中使用，主要用于安全地交换会话密钥。
对称加密（Symmetric Encryption）：在会话密钥交换完成后用于加密通信的数据。
非对称加密使用一对密钥：公钥和私钥。公钥可公开，用于加密数据，而私钥保密，用于解密数据。对称加密使用相同的密钥进行加密和解密，因此比非对称加密更快，适合加密大量数据。

整个过程确保了数据在客户端和服务器之间传输的安全性，防止了中间人攻击，并确保了数据的完整性和机密性。
