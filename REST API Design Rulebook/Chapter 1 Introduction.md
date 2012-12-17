## 第一章Introduction

### web architecture

1. Client-svrver
	> 客服端-服务器模式
2. Uniform interface
	> 不管是客服端、服务器或者其他网络中间媒介都要遵守统一的标准，依靠统一的接口,四个约束：

+ Identification of resources
+ Manipulation of resource through representations
	> representation is a way to interact with the resource but it is not the resource itself.相同的内容可以在不同的终端以不同的方式表现，比如一个文档在浏览器中以**HTML**的形式表现，在自动程序中用**JSON**形式。
+ Self-descriptive message
+ Hypermedia as the engine of application state (HATEOAS)

3. Layered system
>分层系统

4. cache
	> caching response data can help to reduce client-perceived(感知) latency,increase the overall availability and reliability of an application,and control a web server'load.一句话，缓存可以为系统减负。

5. stateless

6. code-on-demand

---