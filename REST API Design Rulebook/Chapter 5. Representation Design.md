## Representation Design

### 消息体格式

REST APIs 通常使用文本格式来表达响应结果。文本格式一般为`XML`，`JSON`.

**规则**

+ 应该用JSON数据格式来表现资源
> 因为JSON有良好的特性，因为它很流行。囧

+ JSON 务必组织好其结构
> JSON 命名使用 `fooBar` 的格式，避免使用类似于 `foo-bar`的命名风格。

+ XML和其他格式也应该提供选择方案

+ Additional envelopes must not be created
	**有待理解**

## 超媒体的表征

**规则**

+ A consistent form should be used to represent links
+ A consistent form should be used to represent link relations
+ A consistent form should be used to advertise links
+ Minimize the number of advertised “entry point” API URIs
+  Links should be used to advertise a resource’s available actions in a
state-sensitive manner

## 媒体类型的表征形式 Media Type Representation

**规则**

+  A consistent form should be used to represent media type formats
+ A consistent form should be used to represent media type schemas

## 错误信息的表征Error Representation

嘿，还记得HTTP 4xx和5xx系列的状态码吗？回忆下哈

+ A consistent form should be used to represent errors
> 错误信息的表现形式应该统一、一致。
+ A consistent form should be used to represent error responses
+ Consistent error types should be used for common error conditions

***

_还有好多没理解啊，coming soon_