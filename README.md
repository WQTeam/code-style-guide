# WOQU.com 代码规范

*为 [WOQU.com](http://www.woqu.com) 前端er提供的代码规范约定，覆盖HTML、CSS、JS。*

## 目录
  1. [HTML](#html)
     - [使用语义化标签](#semantic)
     - [编码](#html-encode)
     - [title的声明](#html-title)
     - [页面&lt;h1&gt;标签唯一性](#h1-unique)
     - [标签嵌套规则](#nested-rule)
  1. [CSS](#css)
     - [class命名](#class-name)
     - [id命名](#id-name)
     - [禁止使用无样式class来hook脚本](#class-hook-js)
  1. [JAVASCRIPT](#javascript)
     - [使用严格模式](#use-strict)
     - [避免全局变量](#avoid-global-variable)
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
<div class="nav"></div>
<div class="section"></div>
<div class="article"></div>
<div class="footer"></div>

<!-- good -->
<header class="header"></header>
<nav class="nav"></nav>
<section class="content-section"></section>
<article class="article"></article>
<footer class="footer"></footer>
```

#### 编码<a name="html-encode"></a>
> 使用`utf-8`编码方式，指定字符编码的`meta`必须是`head`的第一个子元素，[原因详解](http://www.qianduan.net/html5-charset-can-it/)。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        ...
    </hed>
    <body>
        ...
    </body>
</html>
```

#### title的声明<a name="html-title"></a>
> `title`必须作为`head`的直接子元素，并紧随`charset`声明之后。`title`中如果包含`ascii`之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>我趣旅行</title>
        ...
    </hed>
    <body>
        ...
    </body>
</html>
```

#### 页面&lt;h1&gt;标签唯一性<a name="h1-unique"></a>
> 一个页面只能有一个h1标签，具体与seo有关。

```html
<!-- bad -->
<h1>我是标题一</h1>
<h1>我是标题二</h1>

<!-- good -->
<h1>我是标题一</h1>
<h2>我是标题二</h2>
...
<h6>我是标题六</h6>
```

#### 标签嵌套规则<a name="nested-rule"></a>
> html标签包含块级元素、内联元素，元素的类型决定嵌套的规则。

> 常见块元素：div、section、ul、li、p、h1~h6等。

> 常见内联元素：span、a、i、input、label、img等。

- 常见嵌套

```html
<!-- right：块级元素可以内嵌其他块级元素或者内联元素 -->
<div><h1><span></span></h1></div>

<!-- right：内联元素可以内嵌其他内联元素 -->
<a href=""><span></span></a>
```



- 错误嵌套

```html
<!-- wrong：内联元素不能嵌套其他块级元素 -->
<span><div></div></span>

<!-- wrong：p元素不能内嵌块级元素，类似元素有h1、h2、h3、h4、h5、h6、p、dt -->
<p><div></div></p>
<h1><div></div></h1>
...
<h6><div></div></h6>

<!-- wrong：a标签不能内嵌a标签，这个错误会经常发生，值得重视 -->
<a href="a.html"><a href="a.html"></a></a>
```


- 回退

```html
<!-- right：内联元素内嵌块级元素 -->
<a style="display: block;" href=""><div></div></a>
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

#### 禁止使用无样式class来hook脚本<a name="class-hook-js"></a>
> 禁止为元素定义无样式的class，而作为调用脚本使用。这样会造成页面class定义冗余以及增加维护难度。请使用元素自带属性或自定义属性实现。

```css
// bad
<div class="click-alert"></div>
$('.click-alert').click(function() {});

// good
<div data-action="clickAlert"></div>
$('div[data-action="clickAlert"]').click(function() {});
```

## {JAVASCRIPT}<a name="javascript"></a>

#### 使用严格模式<a name="use-strict"></a>

> 在代码中使用严格模式`'use strict';`，详细参考[javascript严格模式详解](http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)。

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
> 虽然js行末的分号不是必须的，但是为了代码风格统一，以及避免打包压缩带来的不可预测问题（真正会导致上下行解析出问题的token有5个：括号，方括号，正则开头的斜杠，加号，减号。一行开头是括号或者方括号的时候不添加分号会报错。），每行末的分号不可以省略。

> js分号工具[semi](https://github.com/yyx990803/semi)

```javascript

// bad
var html = head + "<div class='main' data-id='main'></div>" + footer
alert(html)

// error
var num = 1
(function() {
    console.log(num)
})
var str = 'error message'

// good
var html = head + '<div class="main" data-id="main"></div>' + footer;
alert(html);

```

#### 变量命名<a name="js-name"></a>
> js变量命名使用小驼峰命名法，按照类型进行区分，需要突出属性特征、用途，不要使用不能清晰表达意义的缩略词。

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

- 缩写词需要准确表明意义

```javascript
// bad
var comm = document.getElementById('#comment');

// good
var comment = document.getElementById('#comment');
```

#### 缩进<a name="indentation"></a>
> `空格`与`tap`不能混用。如果使用`空格`，四个`空格`代替一个缩进的位置。如果使用`tap`，请设置一个`tap`代替四个`空格`的位置长度。
