# HTML5 CSS3
## First
### 语义化更强的标签
```HTML
<header>
     <nav>nav</nav>
</header>

<main>
    <article>article</article>
    <aside>aside</aside>
</main>

<footer>
</footer>
<!--宽度百分比布局,再浮动-->
```

### form标签的用法
- **datalist标签**：id必须和input标签的list属性值一样。input获取焦点以后才会有下拉框的效果。--类似select
- **keygen标签**：基本不用
- **output标签**：配合``type='range'``使用。
```HTML
<form>
    <fieldset>
        <legend>新form标签</legend>
        <input type="text" placeholder="请输入晚餐的食物" list="foodList">
        <!-- datalist  可以为input 标签增加选项为用户提供默认的选项 select也是可以实现类似的效果-->
        <datalist id='foodList'>
            <option value="臭豆腐盖饭">臭豆腐盖饭</option>
            <option value="榴莲肉饼汤">榴莲肉饼汤</option>
            <option value="肉夹馍">肉夹馍</option>
        </datalist>
            <br>
        <!-- 加密了解即可,实际开发中基本不用-->
        <keygen keytype="rsa"></keygen>
            <br>
        <!-- output 输出它的作用类似于span 本身没有任何功能,没有任何默认的外观,只是语义性强,可以用来放结果如果要使用一般是配合用来显示结果-->
        <output name=""></output>
            <br>
        <input type="range" oninput='changeNum(this)'>
    </fieldset>
</form>
```
```javascript
function changeNum(obj) {
    document.querySelector('output').innerText = obj.value;
}
```

### input标签的新属性
- ``autofocus``: 自动获取焦点
- ``autocomplete``:
- ``multiple``: 针对``type='file'``，添加之后可以选择多个文件
- ``name="jserAge"``: 提交之后输入框有提示，必须加``name``属性
- ``form='formTest'``: 表单之外的``input``被获取，要关联一下，form的属性必须和form标签的ID一样。
```HTML
    <form id='formTest'>
        <input type="text" value='' placeholder="请输入用户名">
        <br>
        <input type="text" placeholder="请输入电话号码" autofocus>
        <br>
        <input type="text" name='userEmail' autocomplete placeholder="请输入邮箱">
        <input type="file" multiple>
        <input type="submit" name="">
    </form>
    <input type="text" name="userAge" placeholder="请输入你的年龄" form='formTest'>
```
> **label** 标签及**for**属性：点击前面的文字，输入框也获取焦点
```HTML
<label for="textBtn">请输入你的爱好:</label>
<input type="text" id='textBtn'>
```
- for属性和input标签的ID必须一样。

### input标签的type属性
- color、date、email、month、number、range、search、tel、time、week
```HTML
<form>
    <fieldset>
        <legend>input的新type属性</legend>
        <label>color:
        <input type="color" name="" value=""></label>
        <label>date:
        <input type="date" name="" value=""></label>
    </fieldset>
</form>
```
### 表单验证
- H5的自定义验证有一定的兼容性问题。弹框和外观是无法自定义的
```HTML
<form>
    <fieldset>
        <legend>用户注册</legend>
        <label for="">用户名
            <input type="text" name="" value="" required>
        </label>
        <label for="">手机号
            <input type="tel" name="" value="" required pattern="[0-9]{11}" id='btnTel'>
        </label>
        <input type="submit" name="">
    </fieldset>
</form>
```
- 添加required属性，在提交时候会自动进行非空验证。
- pattern属性，设置正则就可以进行内容的筛选。
- oninvalis添加了变淡验证。验证失败以后会调用
```javascript
$('#btnTel').oninvalid = function (){
    if(this.value == ''){
        this.setCustomValidity('请输入内容');
    }
    else{
        this.setCustomValidity('登陆成功');
    }
};
```
> 如果pattren属性设置了正则，就不需要些oninvalid验证。


### 获取dom元素
> 在不需要导入jQuery的情况下。也能使用类似的语法获取dom元素
- **document.querySelector('li[skill]')**
- **document.querySelectorAll('li')**: 返回的是一个数组，哪怕只有一个元素也是数组。
```HTML
<ul>
    <li>榴莲</li>
    <li skill='逆风十里'>臭豆腐</li>
    <li id='greenGua'>苦瓜</li>
    <li class='innerOil'>咸蛋</li>
</ul>
```
```javascript
document.querySelector('li').style.backgroundColor = 'yellow';
// $(li[skill]) 可以使用属性选择器
document.querySelector('li[skill]').style.backgroundColor = 'pink' ;
document.querySelector('.innerOil').style.color = 'orange';
document.querySelector('#greenGua').style.backgroundColor = 'yellowgreen';

var liLists = document.querySelectorAll('li');
console.log(liLists.length);
for (var i = 0; i < liLists.length; i++) {
    liLists[i].onclick = function (event) {
        // 修改文字大小
        this.style.fontSize = '30px';
    }
}
```

### 操作class
- classList属性可以让我们像jQuery那样操作class
    - .classList.add('red');
    - .classList.remove('red');
    - .classList.toggle('blue');
    - .classList.contains('green'); 是否包含``green``这个类，返回Boolean
```html
<div></div>

<input type="button" value='添加class' id='btnAdd'>
<input type="button" value='移除class' id='btnRemove'>
<input type="button" value='切换class' id='btnToggle'>
<input type="button" value='判断是否包含' id='btnContains'>
```
```css
div {
    width: 100px;
    height: 100px;
    border: 1px solid #0094ff;
}
.gray {
    background-color: gray;
}

.red {
    background-color: red;
}
```
```javascript
    var div = document.querySelector('div');
    document.querySelector('#btnAdd').onclick = function (e) {
        div.classList.add('red');
    };
    document.querySelector('#btnRemove').onclick = function (e) {
        div.classList.remove('red');
    };
    document.querySelector('#btnToggle').onclick = function (e) {
        div.classList.toggle('gray');
    };
    document.querySelector('#btnContains').onclick = function (e) {
        alert(div.classList.contains('gray'));
    };
```
> 注意：css样式中的类名，前后的顺序会影响``add``和``toggle``的样式是否有效。

### 两种进度条
- **progress**标签、**meter**标签
    - progress：value当前值；max最大值。
```HTML
	<progress value="50" max="100"></progress>
	<progress value="50" max="200"></progress>
		<br>
	<meter value="" min="0" low="30" high="60" max="100"></meter>
		<br>
	<input type="range" id='rangeBtn'>
	<span id='result'></span>
```
```javascript
document.querySelector('#rangeBtn').oninput = function(){
	console.log(this.value);
	document.querySelector('#result').innerText = this.value;
	document.querySelector('progress').value=this.value;
	document.querySelector('meter').value=this.value;
}
```
> 注意： oninput = function (){ }

### 自定义进度条
```html
<div class='container'>
    <div class="progress"></div>
</div>

<input type="range">
```
```css
.container {
    width: 300px;
    height: 30px;
    border: 1px solid #0094ff;
}

.progress {
    height: 100%;
    width: 0%;
    background-color: pink;
}
```
```javascript
document.querySelector('input').oninput = function (e) {
    // 找到 progress 修改 宽度即可
    document.querySelector('.progress').style.width = this.value + '%';
    if (this.value > 50) {
        document.querySelector('.progress').style.backgroundColor = 'green';
    } else {
        document.querySelector('.progress').style.backgroundColor = 'red';
    }
}
```

### **data—** 获取自定义属性
- ``data-path='img/wbq.jpg' ``: ``alert(this.dataset['path'])``
```HTML
<div class="imgBox"></div>
	<div class='infoBox'></div>
	<div class='btnBox'>
		<input type="button" value='王宝强' data-path='img/wbq.jpg' data-info='宝宝不哭,站起来'>
		<input type="button" value='宋仲基' data-path='img/szj.jpg' data-info='专业撩妹,大众老公'>
		<input type="button" value='贾玲' data-path='img/jl.jpg' data-info='贾玲，原名贾裕玲。1982年4月29日出生于湖北襄阳，毕业于中央戏剧学院。'>
	</div>
```
```javascript
var btnLists = document.querySelectorAll('input');
for (var i = 0; i < btnLists.length; i++) {
    btnLists[i].onclick = function (argument) {
    // dataset 传入key (键)
    console.log(this.dataset['path']);
    console.log(this.dataset['info'])
    document.querySelector('.imgBox').style.background = "url("+this.dataset['path']+")";
    document.querySelector('.infoBox').innerText = this.dataset['info'];
    }
}
```
- ``data-``: 后面设置多个属性。
    - 设置的时候'data-'后面的字母不能大写。
    - 获取的时候要采用驼峰命名法。
```HTML
<input type="button" value='王思聪' data-dog='可可' data-dog-friend='黄毛' data-father='王健林'>
```
```javascript
var inputLists = document.querySelectorAll('input');
for (var i = 0; i < inputLists.length; i++) {
    inputLists[i].onclick = function (e) {
        alert(this.dataset['dog']);
        alert(this.dataset['father']);
        alert(this.dataset['dogFriend']);
    }
}
```

### Video标签
- **poster**: 封面``如果自动播放，封面就没有意义``
- **loop**：循环播放
- **autoplay**: 自动播放
- **controls**: 控制栏

```HTML
<video controls loop  poster="img/wbq.jpg" width="300px" height="300px">
    <!--source 可以指定多个同的视频格式,想要 自定义播放器的控制栏需要自己使用html代码-->
    <source src="movie/rabbit.ogg" >
    <source src="movie/movie01.mp4">
</video>
```

### Audio标签
- 如果没有controls属性，就属于隐藏状态
```HTML
<audio  controls autoplay loop>
    <!-- 从上往下解析 找到 可以播放的 即开始播放 -->
    <source src="music/music.ogg" type="" media="">
    <source src="music/music.mp3" type="" media="">
    <!-- 当视频 都无法播放 可以 通过提示信息 来告诉用户解决方案 -->
    亲爱的用户,您的浏览器版本过低,可以点击下载<a href="#">360急速全家桶</a>
</audio>
```

