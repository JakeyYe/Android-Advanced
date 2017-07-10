##HTTP协议字段

	HTTP请求和响应中的请求字段和响应字段都是又三部分组成的，请求字段是请求首部字段，请求通用字段，请求体字段，而响应字段是响
	应首部字段，响应通用字段，响应体字段。

###1，请求字段
- Cache-Control:no-cache(指定请求和响应遵循的缓存机制)
- Cookie(根据服务器发来发Set-Cookie字段后保存Cookie,并在请求中添加Cookie)
- Host(服务器域名)
- Pragma:no-cache（Pragma代表注释，附注，Pragma头域用来包含实现特定的指令，这个的含义和Cache-Control:no-cache相同）
- user-Agent(浏览器身份标识字符串)
- Last-Modified(资源最近修改时间)
- IF-Modified-Since(用于提供条件GET，只有当所请求的内容在指定的日期之后又经过修改才返回它，否则返回304 “Not Modified”)
- Range(该字段代表可以请求实体的一个或多个范围)
- If-Match(仅当客户端提供的实体与服务器上对应的实体相匹配时，才进行对应的操作)
- Referer(表示浏览器所访问的前一个页面)

###2，响应字段
- Accept-Ranges:bytes(代表服务区数据是否可以断点续传，分段传输，数据单位是bytes,这是唯一的)
- Cache-Control:max-age=0(这代表客户端不不能缓存,适用于动态资源)
- ETag:"737060cd8c284d8af7ad3082f209582d"(对于某个资源的某个版本的一个标识符，通常是一个消息散列)
- Expires(指定一个日期/时间，超过该时间则认为此回应过期，适用于静态资源)
- Last-Modified(所请求的对象的最后修改日期)
- Pragma:no-cache
- Set-Cookie(请求客户端保存Cookie的字段)
- Transfer-Encoding:chunked(用来将实体安全地传输给用户的编码方式。当前的定义的方法包括：分块（chunked）,compress,deflate,gzip和identify.)

##细分字段
### 1，通用头字段
	通用头字段可用于请求消息和响应消息，与HTTP消息实体内最终传输的数据无关，只使用于要发送的消息。这些消息头由于HTTP版本的不
	同可能会有所区别，在HTTP/1.1中，这些消息头有：
	Cache-control
	Connection
	Date
	Pragma
	Trailer(这个头部数值指示了在这一系列头部信息由由分块传输编码编码。)
	Transfer-Encoding
	Upgrade
	Via
	Wraning

### 2，请求头字段
	请求头字段仅用于请求消息。HTTP请求头为所请求的资源或请求本身，提供了更为精确的描述信息，如：
	IF-Modified-Since
	Accept-Language
	Accept-Charset
	User-Agent
	Accept_Encoding

### 3，响应头字段
	响应头字段仅用于响应消息,为响应头提供了更多信息，如：
	Location
	Server
	Content-Encoding

### 4，实体头字段
	实体头字段可以用于请求体消息或响应体消息，提供了关于消息体的描述，如：
	Content-Length：消息体的长度
	Content-Type:消息体的MIME类型

[HTTP头字段-维基百科](https://zh.wikipedia.org/wiki/HTTP%E5%A4%B4%E5%AD%97%E6%AE%B5)
[HTTP消息头](https://itbilu.com/other/relate/E1T0q4EIe.html)
[fiddler详解](http://w3cboy.com/post/2015/03/%E6%8A%93%E5%8C%85%E7%A5%9E%E5%99%A8Fiddler/index.html)