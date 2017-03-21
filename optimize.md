# web前端性能优化总结

> 网站的划分一般为二：前端和后台。
- 可以把后台理解为用来实现网站功能的。比如：注册，发表评论。
- 前端其实应该是属于功能的表现。并且影响用户体验的绝大部分来自前端页面。
```
一般来说，web前端指网站业务逻辑之前的部分，浏览器加载、网站视图模型、图片服务、CSN服务。主要优化方案：浏览器访问、反向代理才、CDN等。
```
- 除了后台需要在性能上做优化以外，前端在这方面也要下功夫，才能带来更好的用户体验。

## HTML
- 缩减资源的大小
- 缩减首屏内容的大小
- 启用压缩功能
- 按视口调整内容尺寸
- 压缩HTML代码
- 避免meta设置字符集
- HTML内嵌小资源
## CSS
- 优化css发送过程
- 合并外部css
- 简化css
- css文件放在顶部
- 避免css @import
- 避免css表达式
- 优化主要css
## javaScript
- 移除阻止呈现的js
- 合并外部JavaScript
- 延迟加载JavaScript
- 延迟解析JavaScript
- 简化javaScript
- 避免document.write
## image
- 优化图片
- 使用CSS贴图合并图片
- 指定图片尺寸
## other
- 避免目标网页重定向
- 改善服务器响应时间
- 使用浏览器缓存
- 使用异步脚本
- 合并Heads
- 转换Meta标签
- 指定"Vary: Accept-Encoding"标头
- 在服务器端指定字符集
- 去除错误的请求
- 启用Keep-Alive
- 删除静态资源查询字符串
- 最小化请求体积

- [Google Yahoo](http://pagespeed.webkaka.com/docs/Server.html)

> 浏览器的访问优化
- 1. 减少http请求，合理设置http缓存
- 2. 使用浏览器缓存
- 3. 启用压缩
- 4. CSS Sprites
- 5. LazyLoad image
- 6. css文件放在顶部，JavaScript放在底部
- 7. 异步请求Callback``把一些行为样式提取出来，慢慢的加载信息内容``
- 8. 减少cookie传输
- 9. JavaScript代码优化
    - DOM
    - 字符串拼接
    - 减少作用域链查找
    - 数据访问
    - css选择符优化
- 10. CDN加速
