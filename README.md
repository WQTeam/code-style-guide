# WOQU.com 代码规范

*为 [WOQU.com](http://www.woqu.com) 前端er提供的代码规范约定，覆盖HTML、CSS、JS。*

## 目录
  1. [HTML](#html)
     - [使用语义化标签](#semantic)
     - [页面h1唯一性](#h1-unique)
     - [标签嵌套规则](#nested-rule)
  1. [CSS](#css)
     - [class命名](#class-name)
     - [id命名](#id-name)
  1. [JAVASCRIPT](#javascript)
     - [使用严格模式](#use-strict)
     - [引号](#quotation)
     - [行末分号](#semicolon)
     - [变量命名](#js-name)
     - [缩进](#indentation)


## {HTML}<a name="html"></a>

#### 使用语义化标签<a name="semantic"></a>
> 使用html5的语义化标签。针对旧版浏览器，引用html5shiv.js进行兼容调整。

```html
<!-- bad -->
<div class="header"></div>
<div class="footer"></div>

<!-- good -->
<header class="header"></header>
<footer class="footer"></footer>
```

#### 页面h1唯一性<a name="h1-unique"></a>
> 一个页面只能有一个h1标签，具体与seo有关

```html
<!-- bad -->
<h1>我是标题一</h1>
<h1>我是标题二</h1>

<!-- good -->
<h1>我是标题一</h1>
<h2>我是标题二</h2>
```

#### 标签嵌套规则<a name="nested-rule"></a>
> html标签包含块级元素、内联元素，元素的类型决定嵌套的规则

> 常见块元素：div、section、ul、li、p、h1~h6等

> 常见内联元素：span、a、i、input、label、img等

```html
<!-- 常见嵌套 -->
<!-- right：块级元素可以内嵌其他块级元素或者内联元素 -->
<div><h1><span></span></h1></div>
<!-- right：内联元素可以内嵌其他内联元素 -->
<a href=""><span></span></a>



<!-- 错误嵌套 -->
<!-- wrong：内联元素不能嵌套其他块级元素 -->
<span><div></div></span>
<!-- wrong：p元素不能内嵌块级元素，类似元素有h1、h2、h3、h4、h5、h6、p、dt -->
<p><div></div></p>
<h1><div></div></h1>
         .
         .
         .  
<h6><div></div></h6>
```


## {CSS}<a name="css"></a>

#### class命名<a name="class-name"></a>
> 全小写，使用中横线分割。单词间使用下横线。

```css
/* bad */
.header_left      { xxx }
.headerLeft       { xxx }
.HeaderLeft       { xxx }

/* good */
.header-left      { xxx }
.usa-main         { xxx }
.new_zealand-main { xxx }
```

#### id命名<a name="id-name"></a>
> 小驼峰写法，中间无中横线或者下横线。

```css
/* bad */
#Logo             { xxx }
#header_logo      { xxx }
#header-logo      { xxx }
#HeaderLogo       { xxx }

/* good */
#logo             { xxx }
#headerLogo       { xxx }
#headerLogoWrap   { xxx }

```

## {JAVASCRIPT}<a name="javascript"></a>

#### 使用严格模式<a name="use-strict"></a>
> 在代码中使用严格模式`'use strict';`，详细参考[javascript严格模式详解](#http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)

```javascript

'use strict';

arr1 = new Array();          // Error

var arr2 = new Array();      // Success

```

#### 引号<a name="quotation"></a>
> js全部使用单引号`''`，拼html模板内使用双引号`""`。

```javascript

// bad
var param = "string";
var html = head + "<div class='main' data-id='main'></div>" + footer;

// good
var param = 'string';
var html = head + '<div class="main" data-id="main"></div>' + footer;

```

#### 行末分号<a name="semicolon"></a>
> 虽然js行末的分号不是必须的，但是为了统一，以及避免打包压缩带来的不可预测问题，每行末的分号不可以省略。

```javascript

// bad
var html = head + "<div class='main' data-id='main'></div>" + footer
alert(html)

// good
var html = head + '<div class="main" data-id="main"></div>' + footer;
alert(html);

```

#### 变量命名<a name="js-name"></a>
> js变量命名使用小驼峰命名法，按照类型进行区分，需要突出属性特征、用途。

- 普通对象

```javascript
// bad
var lib-name = 'sammy.js';
var lib_name = 'sammy.js';
var LibName  = 'sammy.js';

// good
var libName  = 'sammy.js';
```

- jQuery对象：`统一添加 $ 作为命名前缀，突出为jQuery对象`

```javascript
// bad
var slider   = $('#slider');
var side-bar = $('#sideBar');
var side_bar = $('#sideBar');

// good
var $slider  = $('#slider');
var $sideBar = $('#sideBar');
```

- 函数：`小驼峰写法，中间无中横线或者下横线`

```javascript
// bad
function get_name() {}
function get-name() {}

// good
function getName() {}
```

- 类(构造函数声明)：`首字母需要大写，驼峰写法`

```javascript
// bad
function superClass() {}

// good
function SuperClass() {}
```

#### 缩进<a name="indentation"></a>
> `空格`与`tap`不能混用。如果使用`空格`，四个`空格`代替一个缩进的位置。如果使用`tap`，请设置一个`tap`代替四个`空格`的位置长度。
