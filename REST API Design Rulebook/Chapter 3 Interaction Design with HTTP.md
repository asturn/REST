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
	
