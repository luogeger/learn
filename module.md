# CommonJS、AMD、CMD
> 其实，js模块化需要考虑的第一个问题就是，为什么要模块化，或者说，模块化为什么很重要。

|    | service|browser|
|:--:|   :--: |  :--: |
| 代码| 相同代码多次执行|需要从一个服务器端分发到过个客户端执行|
| 瓶颈| CPU和内存资源|带宽|
| 加载| 从磁盘加载|通过网络加载|

- 网页越来越像桌面程序，需要一个团队分工协作、进度管理、单元测试等等......开发者不得不使用软件工程的方法，管理网页的业务逻辑

- 理想情况下，开发者只需要实现核心的业务逻辑，其他都可以加载别人已经写好的模块。

- 但是，Javascript不是一种模块化编程语言，它不支持``类``（class），更甭说``模块``（module）了。同时，我们希望js代码能在服务器端运行，不仅是浏览器端。所以，有了模块化，我们可以很方便地使用别人的代码，想要什么功能，就加载什么模块。

- 但是，这样做需要一个前提，就是代码规范，不然大家各自使用自己的规范，就会乱套。

- CommonJS就是为js的表现指定的规范。
    - 在CommonJS中，有一个全局性的方法``require()``,用于加载模块。假定要加载一个数学模块
    ```javascript
        var math = require('math');
    ```
    - 然后调用模块提供的方法。
    ```javascript
        var math = require('math');
        math.add(2,3); // 5
    ```

- 假如：第二行代码在第一行之后运行，必须等待math.js加载完成，也就是说，如果加载时间很长，整个网页就会停在那里等。

> 以上代码在服务器端执行不成问题，因为，所有模块都放在本地硬盘，可以同步加载完成，等待时间就是硬盘的读取时间。但是，放在浏览器端，却是以很大的问题，因为所有的模块都在服务器端，等待时间取决于网速，可能要等待很长时间，浏览器处于**假死**状态

- 因此，浏览器端的模块，不能才用**同步加载** ``synchronous``,只能采用**异步加载**``asunchronous``。这就是AMD规范诞生的背景。

- **AMD** ``Asynchronous Module Definition 异步模块定义``, 模块的加载不会影响它后面**语句**的运行。所有依赖这个模块的语句，都定义在一个回调函数中，等到加载完成之后，这个回调函数才会执行。

- AMD也采用require()语句加载模块，但是不同CommonJS，它要求2个参数
```javascript
    require( [ ], callback);//前面是数组，成员是要加载的模块
    //改写上面加载math.js的代码
    require(['math'], function (math){
        math.add(2, 3);
    })
```

- 看以下的代码，相信都再熟悉不过了吧，缺点如下：
    - 1.加载的时候，浏览器停止网页渲染，文件越多，失去响应的时间就会越长。
    - 2.js文件之间存在依赖关系，因此，必须严格保证加载顺序。
    - 3.如果这是别人写的代码，而且注释不详，你难道就没有怼他的想法。（妹纸的话，另当别论）.
```html
<script src="1.js"></script>
<script src="2.js"></script>
<script src="3.js"></script>
<script src="4.js"></script>
<script src="5.js"></script>
<script src="6.js"></script>
```
- RequireJS的诞生，就是为了解决这2个问题：
    - 1.实现js文件的异步加载，避免网页失去响应。
    - 2.管理模块之间的依赖性，便于代码的编写和维护。

- RequireJS遵循的是AMD规范.
    - 对于依赖的模块，AMD是**提前执行** ,CMD是**延迟执行** 。不过，RequireJS从2.0开始，也改成可以延迟执行(根据写法不同，处理方式不同)。

- SeaJS遵循的是CMD规范.
    - CMD推崇 as lazy as possible. **依赖就近**，AMD推崇**依赖前置**

```javascript
    //CMD
    define(function (require, exports, module){
        var a = require('./a');
        a.doSomething();

        var b = require('./b');  //依赖可以就近书写
        b.doSomething();
    })

    //AMD
    define(['./a', './b'], function (a, b){ //依赖一开是就要写好
        a.doSomething();
        b.doSomething();
    })
```

## 模块化的演变
### 全局函数：在全局定义 add, sub, mul, div. 4个函数
    - 执行运算的时候，获取``type`` 类型，进行判断``switch``
    ```html
        <input type="text" id="t1">
        <select id="sel">
            <option value="1">+</option>
            <option value="2">-</option>
            <option value="3">*</option>
            <option value="4">/</option>
        </select>
        <input type="text" id="t2">
        <input type="button" value="计算" id="btn">
        <span id="result"></span>
    ```
    ```javascript
          window.onload = function () {
              var btn = document.getElementById("btn");
              btn.onclick = function () {
                  var n1 = document.getElementById("t1").value;
                  var n2 = document.getElementById("t2").value;
                  var type = document.getElementById("sel").value;
                  var result = document.getElementById("result");
  
                  //进行计算
                  switch (type) {
                      case "1":
                          result.innerText = add(n1, n2);
                          break;
                      
                  }
              };
          }
    ```

### 对象封装
> 全局函数造成变量污染，但是，对象封装还是无法提供私有成员
```javascript
    var obj = {
        add: function add(a, b) {
            return parseInt(a) + parseInt(b);
        },
        sub: function sub(a, b) {
            return parseInt(a) - parseInt(b);
        },
        mul: function mul(a, b) {
            return parseInt(a) * parseInt(b);
        },
        div: function div(a, b) {
            return parseInt(a) / parseInt(b);
        }
    };

```

### 隔离私有空间 
- 通过``自执行函数``
```javascript
    var obj = (function () { 
                function log() {
                    console.log("我是打酱油的");
                };// 这就是私有的成员
    
                return {
                    add: function add(a, b) {
                        log();
                        return parseInt(a) + parseInt(b);
                    },
                    sub: function sub(a, b) {
                        log();
                        return parseInt(a) - parseInt(b);
                    },
                    mul: function mul(a, b) {
                        return parseInt(a) * parseInt(b);
                    },
                    div: function div(a, b) {
                        return parseInt(a) / parseInt(b);
                    }
                };
            }())
```

#### 还可以对模块进行扩展
```javascript
    var obj = (function (o) {
        //求平方
        o.power = function (a) {
            return parseInt(a) * parseInt(a);
        }
   
        return o;
    }(obj || {}));
```

### 引用模块
```
利用sea.js的能力，``seajs.use("A","B")``;
A: 想调用的模块的地址，相对于seajs的相对地址
B: 是一个方法，
```

> 首先，定义一个模块A
```javascript
define(function (require, exports, module) {
    // -require 需要 -exports 输出 -module  模块
    exports.add = function (a, b) {
        return parseInt(a) + parseInt(b);
    }
    exports.sub = function (a, b) {
        return parseInt(a) - parseInt(b);
    }
});
```
    ```
        1.exports和module.exports使用上的区别
        2.exports  功能 输出成员，不可以导出对象
        3.module 功能 可以使用module.exports的方式输出成员， 可以导出对象
        
        4.exports和module.exports 本质的区别
        5.exports = module.exports = {},  exprots被赋值的是引用
    ```
> 然后在引用模块
```html
<script src="scripts/sea-debug.js"></script>
```
```javascript
seajs.use("module1/math.js", function (obj) {
    console.log(obj.add(5, 6));
    console.log(obj.sub(5, 6));
});
```























