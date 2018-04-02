## HTTP协议字段

	HTTP请求和响应中的请求字段和响应字段都是由三部分组成的，请求字段是请求首部字段，请求通用字段，请求体字段，而响应字段是响
	应首部字段，响应通用字段，响应体字段。
	
协议：指计算机通信网络中两台计算机之间进行通信所必须共同遵守的规定或规则；

HTTP协议：超文本传输协议（HTTP）是一种通信协议，它允许将超文本标记语言（HTML）文档从Web服务器传送到客户端的浏览器上；

URI:用来唯一的标识一个资源，表示的事一个资源；

URL：也是一种URI,一种具体的URI,多在网络中表示一个地址 ；URL由三个组成部分：协议、存有该资源的主机IP地址、主机资源的具体地址；  

### 1，请求字段
- Cache-Control:no-cache(指定请求和响应遵循的缓存机制)
- Cookie(根据服务器发来发Set-Cookie字段后保存Cookie,并在请求中添加Cookie)
- Host(服务器域名)
- Pragma:no-cache（Pragma代表注释，附注，Pragma头域用来包含实现特定的指令，这个的含义和Cache-Control:no-cache相同）
- user-Agent(浏览器身份标识字符串)
- Last-Modified(资源最近修改时间)
- If-Modified-Since(用于提供条件GET，只有当所请求的内容在指定的日期之后又经过修改才返回它，否则返回304 “Not Modified（未修改，缓存有效）”)
- If-Unmodified-Since(仅当该实体自某个特定时间以来未被修改过的情况下，才发送回应)
- Range(该字段代表可以请求实体的一个或多个范围)
- If-Match(仅当客户端提供的实体与服务器上对应的实体相匹配时，才进行对应的操作)
- Referer(表示浏览器所访问的前一个页面)
- ETag和If-None-Match的典型用法：

	在典型用法中，当一个URL被请求，Web服务器会返回资源和其相应的ETag值（标识符），它会被放置在HTTP的"ETag"字段中：

	`ETag: "686897696a7c876b7e"`
	
	然后客户端可以决定是否缓存这个资源和它的ETag。以后，如果客户端想再次请求相同的URL,将会发送一个包含已保存的ETag和"If-None-Match"字段的请求。

	`If-None-Match:"686897696a7c876b7e"`

	如果服务端发现ETag值匹配，就会发送一个极短的响应，包含HTTP "304(未修改)"的状态，若不匹配，会发送一个完整的响应。
- Last-Modified和If-Modified-Since的典型使用：


### 2，响应字段
- Accept-Ranges:bytes(代表服务区数据是否可以断点续传，分段传输，数据单位是bytes,这是唯一的)
- Cache-Control:max-age=0(这代表客户端不能缓存,适用于动态资源)
- ETag:"737060cd8c284d8af7ad3082f209582d"(对于某个资源的某个版本的一个标识符，通常是一个消息散列)
- Expires(指定一个日期/时间，超过该时间则认为此回应过期，适用于静态资源)
- Last-Modified(所请求的对象的最后修改日期)
- Pragma:no-cache
- Set-Cookie(请求客户端保存Cookie的字段)
- Transfer-Encoding:chunked(用来将实体安全地传输给用户的编码方式。当前的定义的方法包括：分块（chunked）,compress,deflate,gzip和identify.)

## 细分字段
### 1，通用首部字段
	通用头字段可用于请求消息和响应消息，与HTTP消息实体内最终传输的数据无关，只使用于要发送的消息。这些消息头由于HTTP版本的不
	同可能会有所区别，在HTTP/1.1中，这些消息头有：
	Cache-control（该字段使用no-cache指令的目的是为了防止从缓存中返回过期的资源；客户端发送的请求中如果包含no-cache指令，
	则表示客户端将不会接收缓存过的响应。于是，“中间”的缓存服务器必须把客户端请求转发给源服务器；如果服务器返回的响应中包含
	no-cache指令，那么缓存服务器不能对资源进行缓存。no-store指令才是真正地不进行缓存的。而no-cache指令是指不要缓存的资源，
	要从源服务器获取最新的资源。）
	Connection（该字段具备两个功能：控制不再转发给代理的首部字段；管理持久连接）
	Date
	Pragma（报文指令,为什么要同时使用Cache-Control:no-cache和Pragma:no-cache,因为Cache-Control是HTTP/1.1的首部字段，
	Pragma是HTTP/1.1之前版本的历史遗留字段，仅作为与HTTP/1.0的向后兼容而定义的，而传输路径上的中间服务器的HTTP协议版本不一
	定全是1.1，故为了兼容所有，所有同时声明两个）
	Trailer(该首部字段会实现说明在报文主体后记录了那些首部字段。该首部字段可应用在HTTP/1.1版本分块传输编码时)
	Transfer-Encoding
	Upgrade（要求服务器升级到另一个HTTP协议）
	Via（代理服务器的相关信息，各个服务器会往Via首部添加自身服务器的信息）
	Wraning（错误通知）

### 2，请求首部字段
	请求头字段仅用于请求消息。HTTP请求头为所请求的资源或请求本身，提供了更为精确的描述信息，如：
	Accept-Language
	Accept-Charset
	User-Agent
	Accept_Encoding
	Range
	If-Match
	If-Modified-Since
	If-None-Modified
	Host
	Cookie(服务器接收到的Cookie信息)

### 3，响应首部字段
	响应头字段仅用于响应消息,为响应头提供了更多信息，如：
	Location（另客户端重定向至指定的URL）
	Server
	Content-Encoding
	Accept-Ranges(这个服务器支持那些种类的部分内容范围，就是是否支持分段传输)
	ETag(资源匹配标识符，又为分为强ETag值（只要发生一点改变就会认为不相同）和弱ETag值（只用于提示资源是否相同，只有当资源发
	生了根本改变，产生差异时才会改变ETag值，这时会在字段值最开始
	处附加W/,就像这样ETag:W/"usagi-134"）)
	Age(该字段能告知客户端，源服务器在多久前创建了响应，字段值的单位为秒)
	Set-Cookie(开始状态管理所使用的Cookie信息)

### 4，实体首部字段
	实体头字段可以用于请求体消息或响应体消息，提供了关于消息体的描述，如：
	Content-Length：消息体的长度
	Content-Type:消息体的MIME类型
	Allow(资源可支持的HTTP方法)
	Content-Range(实体主体的位置范围)
	Expires(实体主体过期的日期时间)
	Last-Modified(资源最后修改时间)

### End-to-end首部和Hop-by-hop首部
	HTTP首部字段将定义为缓存代理和非缓存代理的行为，分为两种类型：端到端首部（End-to-end Header）和逐跳首部（Hop-by-hop Header）。
	除了下面这8个首部字段之外，其他所有字段都属于端到端首部字段：
	Connection
	Keep-Alive
	Proxy-Authorization
	Proxy-Authenticate
	Trailer
	TE
	Transfer-Encoding
	Upgrade
    参考《图解HTTP》6.2.6章节

[HTTP头字段-维基百科](https://zh.wikipedia.org/wiki/HTTP%E5%A4%B4%E5%AD%97%E6%AE%B5)
[HTTP消息头](https://itbilu.com/other/relate/E1T0q4EIe.html)
[fiddler详解](http://w3cboy.com/post/2015/03/%E6%8A%93%E5%8C%85%E7%A5%9E%E5%99%A8Fiddler/index.html)