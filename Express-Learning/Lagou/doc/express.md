### Express Intro.

Express 是一个 Node.js web 应用开发框架。通过它，可以构建各种 web 应用。例如:

- 接口服务
- 传统的 web 网站
- 开发工具集成等

- ...



集成了许许多多的外部插件来处理 HTTP 请求:

- Body-parser: 解析 HTTP 请求体
- compression：压缩 HTTP 响应
- cookie-parser：解析 cookie 数据
- cors: 处理跨域资源请求
- morgan: HTTP 请求日志记录

- ...



Express 不对 Nodejs 已有的特性进行二次抽象，只是在它之上扩展了 web 应用所需的基本功能。

- 内部使用的还是 http 模块
- 请求对象继承自: http.IncomingMessage
- 响应对象继承自：http.ServerResponse
- ...



### Express Router



