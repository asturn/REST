## Interaction Design with HTTP

### 请求方法

客户端在 **Request-Line** (HTTP请求信息的一部分)中指定具体的交互方法(interaction method) [RFC 2616](http://www.rfc-editor.org/rfc/rfc2616.txt) 定义了 **Request-Line** 如下的语法：

		Request-Line   = Method SP Request-URI SP HTTP-Version CRLF

+ GET 检索资源
+ HEAD is used to retrieve the metadata associated with the resource’s state.
+ PUT 增加或者更新资源.
+ DELETE 删除资源.
+ POST 增加资源 within a col-lection and execute controllers.

**规则**

+ GET and POST must not be used to tunnel other request methods

+ GET must be used to retrieve a representation of a resource

+ HEAD should be used to retrieve response headers
响应结果和使用GET方法一样，但是body是空的

		$ curl --head http://api.example.restapi.org/greeting

+ PUT must be used to both insert and update a stored resource
> PUT 请求信息必须包含客户端想要存储的内容

+ PUT must be used to update mutable（可变的） resources

+ POST must be used to create a new resource in a collection

	下面的例子显示了客户端如何利用 *`POST`* 请求建立一个新的collection：

		POST /leagues/seattle/teams/trebuchet/players
		# Note the request message may contain a representation that suggests the initial state 
		of the player to be created.

+ POST must be used to execute controller
	
	_the POST method should not be used to get, store, or delete resources
	—HTTP already provides specific methods for each of those functions_

+ DELETE 删除资源

	客户端使用`DELETE`从它的父类（可能是`collection`或者`store`）移除一个资源。ps:翻译的都待商榷。

+ OPTIONS should be used to retrieve metadata that describes a resource’s available interactions
	
## 状态码Response Status Codes

REST APIs 使用 HTTP 响应消息中的`Status-Line`部分来通知客户端其请求结果的总体情况(overarching result)。RFC2616定义了`Status-Line`如下语法：
```
Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF
```

HTTP定义了40个标准状态码，分成5种类型：

```
 1xx：Informational
	Communicates transfer protocol-level information.

 2xx: Success
	Indicates that the client's request was accepted successfully.

 3xx: Redirection
	Indicates that the client must take some additional action in order to complete their request.

 4xx: Client Error
	This category of error status codes points the finger at clients.

 5xx: Server Error
	The server takes responsibility for these error status codes.
```

**规则**

+ `200`( **OK** ) 应该用于表征一般的成功(nonspecific success)

+ `200`( **OK** ) 坚决不能用于错误信息的交流。200 must not be used to communicate errors in the response body.

+ `201`( **Created** )用于表明资源创建成功。

+ `202`( **Accepted** )用于表征异步交互的成功开始。indicate successful start of an asynchronous action
 
+ `204`( **No Content** )用于当响应体为空的时候
 
+ `301`( **Moved Permanently** )用于资源重置的时候（relocate resources）
 
+ `302`( **Found** ) 杜绝使用

+ `303`( **See Other** )用于将客户端引导另一个URI。refer the client to a different URI.
 
+ `304`( **Not Modified** )用于保护带宽。
 
+ `307`( **Temporary Redirect** )告诉用户，嘿，你该重新提交请求到另一个URI了。

+ `400`（ **Bad Request** ）糟糕，失败了。

+ `401`( **Unauthorized** ) 用户认证失败。
 
+ `403`( **Forbidden** ) 禁止未授权的用户访问。
 
+ `404`( **NotFound** ) 当用户请求的URI无法映射到一个资源的时候。

+ `405`( **Method Not Allowed** )be used when the HTTP method is not supported.
 	例如，当一个只读类型资源只支持`GET`,`HEAD`时，用户可以使用`GET` 和 `POST`,但是不能使用 `PUT`,`DELETE`.
	
+ `406`( **Not Acceptable** )be used when the requested media type cannot be served.
 	如果API提供的数据格式仅为`application/json`，而客户端请求的格式为`application/xml`,那么它将收到`406`错误。
	
+ `409`( **Conflict** )be used to indicate a violation of resource state.
	例如，当客户端试图删掉一个非空的`store resoure`时，REST API就会返回`409`错误代码。
 	
+ `412`( **Precondition Failed** )用于支持条件操作。

+ `415`( **Unsupported Media Type** )用于当客户端的媒体处理请求无法处理的时候。
 
+ `500`( **Internal Server Error** )糟糕，这都是服务器的错。