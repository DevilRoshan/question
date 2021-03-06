# cors-brief

> 出自小程序前端面试星球
>
> 参考链接：https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS

### 题目

简述CORS的简单请求和复杂请求的区别



### 解题

#### 思路

* CORS是跨域资源共享机制，它新增了一组HTTP首部字段，来约定限制请求的权限，对于部分请求与要放松额外的请求
* 比如，如果你发送的请求添加了额外的首部字段，浏览器就会首先使用`OPTIONS`发送一个预检请求`preflight request`，询问服务器是否允许这个请求。如果允许才会发送实际的HTTP请求
* 所以简单请求和复杂请求的实际区别是，是否会发送额外的`OPTION`区别
* 而简单请求的定义就是，不会出发CORS预检请求的这一类请求。
  * 使用了`GET`，`HEAD`，`POST`
  * 使用允许人为设置的字段，Fetch规范定义的对CORS安全的首部字段集合
  * `Content-Type`为`text/plain`，`multipart/form-data`，`application/x-www-form-urlencoded`
  * 请求中没有使用`ReadableStream`对象
  * 请求中的任意`XMLHttpRequestUpload` 对象均没有注册任何事件监听器；】
* 除了简单请求就是复杂请求了，一般常见的复杂请求就是，请求头中携带token

#### 代码





### 思考

