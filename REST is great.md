#REST#

##what is REST ?

REST是英文 **Representational** State Transfer的缩写

## 设计准则

1. 网络上的所有事物都被抽象为资源（resource）
2. 每个资源对应一个唯一的资源标识符（resourceidentifier）；
3. 通过通用的连接器接口（generic connector interface）对资源进行操作；
4. 对资源的各种操作不会改变资源标识符；
5. 所有的操作都是无状态的（stateless）。

REST 基于**HTTP**协议，对任何资源的操作都是通过http协议来实现的

HTTP 对一个资源的操作限制为4个方法：

+ GET
+ POST
+ PUT
+ DELETE

刚好对应数据库**CURD**的操作。

* * *