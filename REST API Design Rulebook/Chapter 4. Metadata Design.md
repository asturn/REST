## 第四章Metadata Design

### HTTP Headers

_entity headers_包含在HTTP的请求和响应消息中，各种形式的`metadata`应该通过她来传递。

**规则**

+ **Content-Type**必须使用
> Content-Type 表明了请求或者响应消息体中数据的类型，客户端和服务器依靠这一头信息来处理 the sequence of bytes in a mes-sage’s body

+ **Content-Length**应该被使用

+ **Last-Modified** 用于响应体中
> Last-Modified也仅仅用于响应消息中，她是一个时间戳，表明请求资源的最后修改时间。

+ **ETag** should be used in responses
> 请求变量的实体标签当前值The value of ETag is an opaque string that identifies a specific “version” of the repre-sentational state contained in the response’s entity

+ Stores must support conditional PUT requests

+ **Location** must be used to specify the URI of a newly created resource

+ **Cache-Control, Expires, and Date response headers** should be used to
encourage caching

+ **Cache-Control, Expires, and Pragma response headers** may be used
to discourage caching

+ **Caching** 应该鼓励使用

+ **Expiration caching** headers should be used with `200` (“OK”) responses

+ **Expiration caching** headers may optionally be used with `3xx` and `4xx`
responses

+ **Custom HTTP headers** must not be used to change the behavior of
HTTP methods

### 介质类型 Media Types

在 HTTP `Content-Type`中需指明介质的类型

#### 语法
```
type "/" subtype *( ";" parameter )
```

type的值有一下几个：
```
application audio image message
model multipart text video
```

举个例子：
```
Content-type: text/html; charset=ISO-8859-4
Content-type: text/plain; charset="us-ascii"
```

当然，你也可以向IANA注册新的媒介类型，填下[这张表](http://www.iana.org/cgi-bin/mediatypes.pl)。

### Media Type Design
_这一节有待日后理解，搁置。_

**规则**

+ Application-specific media types should be used

+ Media type negotiation should be supported when multiple
representations are available

+ Media type selection using a query parameter may be supported
