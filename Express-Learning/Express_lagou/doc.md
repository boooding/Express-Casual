#  RESTful 接口设计规范

协议
API 与用户的通信协议，尽量使用 HTTPS 协议。

域名
应该尽量将API部署在专用域名之下。

版本
应该将APl的版本号放入URL。

路径
路径又称"终点"（endpoint)，表示 API 的具体网址。

在 RESTful 架构中，每个网址代表一种资源（resource），所以网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表格名对应。一般来说，数据库中的表都是同种记录的"集合"(collection），所以API中的名词也应该使用复数。

HTTP 动词
对于资源的具体操作类型，由HTTP动词表示。

常用的HTTP动词有下面五个（括号里是对应的SQL命令）。
GET（读取）：从服务器取出资源（一项或多项)。
POST（创建）：在服务器新建一个资源。
PUT（完整更新）：在服务器更新资源（客户端提供改变后的完整资源)。
PATCH(部分更新）：在服务器更新资源（客户端提供改变的属性）。
DELETE（删除）：从服务器删除资源。

还有两个不常用的HTTP动词。
HEAD：获取资源的元数据。
OPTIONS：获取信息，关于资源的哪些属性是客户 端可以改变的。

过滤信息
如果记录数量很多，服务器不可能都将它们返回给用户。API应该提供参数，过滤返回结果。

?limit=10：指定返回记录的数量
?offset=10：指定返回记录的开始位置。
?page=2&per_page=100：指定第几页，以及每页的记录数。

参数的设计允许存在冗余，即允许APl路径和URL参数偶尔有重复。比如，GET /zoo/ID/animals 与 GET /animals?zoo_id=ID 的含义是相同的。

针对不同操作，服务器向用户返回的结果应该符合以下规范。
GET /collection：返回资源对象的列表（数组）
GET /collection/resource：返回单个资源对象
POST /collection：返回新生成的资源对象
PUT /collection/resource：返回完整的资源对象
PATCH /collection/resource：返回完整的资源对象
DELETE /collection/resource：返回一个空文档 {}

错误处理

正确的做法是，状态码反映发生了错误，具体的错误信息放在数据体里面返回。

身份认证
基于 JWT 的接口权限认证：
•字段名：Authorization
• 字段值：Bearer token数据

跨域处理
可以在服务端设置 CORS 允许客户端跨域资源请求。
