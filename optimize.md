# web前端性能优化总结

> 网站的划分一般为二：前端和后台。
- 可以把后台理解为用来实现网站功能的。比如：注册，发表评论。
- 前端其实应该是属于功能的表现。并且影响用户体验的绝大部分来自前端页面。
> 一般来说，web前端指网站业务逻辑之前的部分，浏览器加载、网站视图模型、图片服务、CSN服务。主要优化方案：浏览器访问、反向代理才、CDN等。

- [Google Yahoo](http://pagespeed.webkaka.com/docs/Server.html)
- [一次完整的http请求都干了些什么事](http://www.jianshu.com/p/c1d6a294d3c0?from=jiantop.com)

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

> 浏览器的访问优化
- (1) 减少http请求，合理设置http缓存
    - 精灵图，base64
    - 合并文件``css，js，图片``
    - 设置缓存：缓存越多越好，越久越好。
        - 很少变化的资源：通过HTTP Header中的``Expires``设置一个很长的过期头
        - 变化不平凡又有可能变化的资源：使用``Last-Modifed``来做请求验证，尽可能让资源在缓存中待得更久。
- (2) 使用浏览器缓存
    > 当浏览器缓存之后，F5刷新，请求的次数是一样，但是缓存资源的请求服务是304响应，只有Header,没有Body,可以节省带宽。
- (3) 启用压缩
    - 在服务端压缩文件，浏览器解压文件，可有效减少通信传输的数据量。尽可能的把外部的js，css进行合并，多个合并为一个。但是压缩对服务器和浏览器产生一定得压力，在通信带宽良好，但是服务器资源不足的情况下要权衡考虑。
- (4) CSS Sprites
- (5) LazyLoad image
    - 本质上并不会减少http请求次数，但是却能在页面刚加载的时候减少次数。
- (6) css文件放在顶部，JavaScript放在底部
    - 无CSS状态跳转到CSS状态，用户体验糟糕
    - 浏览器加载js会立即执行，有可能阻塞整个页面。所以放在最下面
- (7) 异步请求Callback``把一些行为样式提取出来，慢慢的加载信息内容``
- (8) 减少cookie传输
- (9) JavaScript代码优化
    - DOM
    - 字符串拼接
    - 减少作用域链查找
    - css选择符优化
    - 数据访问
- (10) CDN加速
