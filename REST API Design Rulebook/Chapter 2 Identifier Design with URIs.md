## 第二章 URI的设计

###URIs
URI的设计大致有两种风格：

一种很清晰明了 _masterpiece_

+ http://api.example.restapi.org/france/paris/louvre/leonardo-da-vinci/mona-lisa

另外一种，看起来比较混沌

+ http://api.example.restapi.org/68dd0-a9d3-11e0-9f1c-0800200c9a66

### URI Format

URI = scheme "://" authority "/" path [ "?" query ] [ "#" fragment ]

**规则**

1. 使用`/`来区分不同的层次关系<br />
http://api.canvas.restapi.org/shapes/polygons/ quadrilaterals/squares

2. `/`不应该出现在URI的结尾<br />
正确做法：http://api.canvas.restapi.org/shapes <br />
错误做法：http://api.canvas.restapi.org/shapes/

3. 使用连字符`-`提高可读性<br />
http://api.example.restapi.org/blogs/mark-masse/entries/this-is-my-first-post

4. 不实用下划线`_`

5. 使用小写字母

6. 文件扩展名应该隐藏起来

### URI Authority Design

#### Rule:consistent subdomain names should be used for APIs.
Fox example:

	http://api.soccer.restapi.org

#### developer portal

For example:

	http://developer.soccer.restapi.org

### 资源原型Resource Archetypes

+ __Document__

+ __Collection__
> A collection resource is a **server**-managed directory of resource.

+ __Store__
> A store is a **client**-managed resource repository

+ __Controller__

### URI 路径设计 Path Design

	{collection-c}/{store-s}/{document-d}

**规则**

1. 文档命名使用名词的单数形式 A singular noun <br />
For example, the URI for a single player document would have the singular form:

	http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players/claudio

2. Collection的命名用复数形式 A plural noun <br />
For example, the URI for a collection of player documents uses the plural noun form
of its contained resources:

	http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players

3. Store的命名用复数形式 A plural noun <br />
The URI for a store of music playlists may use the plural noun form as follows:
	http://api.music.restapi.org/artists/mikemassedotcom/playlists

4. Controller使用动词或者动词短语的形式命名 <br />
For example:
	http://api.college.restapi.org/students/morgan/register

5. CRUD function names should not be used in URIs <br />
HTTP request methods should be used to indicate which CRUD function is performed.例如，想要删掉id为114的用户，应该如此设计：
	
	DELETE /users/1234

而下面的做法则是应该避免的：

+ GET /deleteUser?id=1234
+ GET /deleteUser/1234
+ DELETE /deleteUser/1234
+ POST /users/1234/delete

### URI Query Design

URI = scheme "://" authority "/" path [ "?" query ] [ "#" fragment ]

Consider the following example:

	1. http://api.college.restapi.org/students/morgan/send-sms
	2. http://api.college.restapi.org/students/morgan/send-sms?text=hello

1. The URI of a controller resource that sends an sms message.
2. The URI of a controller resource that sends an sms message with a text value of hello.

**规则**

+  The query component of a URI may be used to **filter** collections or stores
	
		GET /users?role=admin

+ The query component of a URI should be used to **paginate** collection or store results 

		GET /users?pageSize=25&pageStartIndex=50

---