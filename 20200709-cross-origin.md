# cross-origin

### 题目

如何进行跨域



### 解题

#### 思路

- 首先说明，跨域其实是一种不安全的方式，本身同源策略是为了阻止用户读取其他域名下的东西，这是一种安全的考虑，而绕过这种检查，有时后其实是一种危险的操作
- JSONP
  - 利用script不会被同源策略影响的特性，请求一个JSON格式的数据
  - 只能发送get请求，而且可能会遭受XSS攻击
  - 实现方式，就是动态创建一个script标签，src属性为`url?params=params&callback=callback`，在window上添加一个callback属性对应的方法，在数据下载完之后会执行callback标识的方法
- CORS
  - 服务器配置http请求头`Access-Control-Allow-Origin`这个字段，设置允许通过的域
  - 大多数处理跨域问题的方式。
  - 如果header中添加了其他字段，浏览器会发一个`preflight`请求，type是option，是用来检测服务器是否允许这个字段。无法完全避免，可以通过设置时间来减少这个预检请求，但这是浏览器一种安全策略不建议去掉。
-  Node 中间件代理还是 nginx 反向代理
  - 同源策略对服务器不加限制，进行跨域
  - 在使用node请求转发请求，服务器对服务器是没有同源策略的，所以相当于转发一次
  - nginx也是一样的原理，都是转发请求
- websocket
  - 一直以来，服务器只能被动的被请求，不能主动向浏览器发送信息，而websocket就是用来解决这个问题的。
  - websocket一般不是专门处理跨域的方式，只是它是跨域不限制的一种与服务器交互的一种方式

#### 代码



### 思考

- CORS 支持所有类型的 HTTP 请求，是跨域 HTTP 请求的根本解决方案

- JSONP 只支持 GET 请求，一般不建议使用，它的优势在于支持老式浏览器，以及可以向不支持 CORS 的网站请求数据。

  