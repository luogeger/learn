
#### let、const
- let
    - 基本用法
    - 不存在变量提升：先声明，后使用
    - 暂时性死区
    - 不能重复声明
    - 块级作用域
- const
    - 6种声明变量的方法
        - `var`, `function`, `let`, `const`, `import`, `class`
    - 顶级对象的属性`window`
        - `var`声明的变量是`window`的属性，`let`不是
    - `global`对象

#### 字符串扩展
- 字符串模板
    ```javascript
    const num = 1;

    let div = `<div>${num}</div>`
    ```

#### 变量解构表达式
- 数组
- 对象
- 字符串
- 数值和布尔值
- 函数参数
- 圆括号
- 用途
    - 遍历Map解构
    ```javascript
    // 获取键名
    for (let [key] of map) {
      // ...
    }

    // 获取键值
    for (let [,value] of map) {
      // ...
    }
    ```

#### 属性名表达式
- ES6允许对象的属性名是表达式，放在**[]**内
    ```javascript
    var propKey = 'foo'
    var methodKey = 'bar'

    var obj = {
      [propKey]: true,
      ['a' + 'bc']: 123,
      [methodKey]() {
        return 'hi'
      }
    }
    ```

#### 箭头函数
- 注意点：
    - **this**, 在Node模块和ES6模块中，返回的是当前模块
    - 无法使用`arguments`, 没有`arguments`对象
    - 不能当做构造函数，不能使用**new**创建对象
- 形参默认赋值
- rest参数

#### 对象的扩展
- 获取对象的所有key
    - `Object.keys(person1)`
- values(obj)
- entries(obj)
- assign(newObj, oldObj...); 深拷贝
    - 还可以多个对象

#### 数组的扩展
- `find(callback)`: 返回元素，对数组的每个元素进行处理，
    - callback必须要有返回值，而且是Boolean
- `findIndex(callback)`: 返回索引，
- `includes(ele)`: 返回Boolean,


#### map

#### reduce(result, next)
- `result`: 上一个元素处理的结果
- `next`: 数组中的下一个元素
```
    let arr = [10, 20, 30];
    arr.reduce((a, b) => a + b);// 60
```


- set map
- symbol
- reflect
- proxy
- Promise
- Iterator, for..of
