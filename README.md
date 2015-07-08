# WOQU.com 代码规范

*为WOQU.com前端er提供的代码规范约定，覆盖HTML、CSS、JS。*

## 目录
  1. [HTML](#html)
     - [语义化标签](#semantic)
  1. [CSS](#css)
     - [class命名](#class-name)
     - [id命名](#id-name)
  1. [JAVASCRIPT](#javascript)
     - [引号](#quotation)
     - [变量命名](#js-name)

## {HTML}<a name="html"></a>

#### 语义化标签
> 使用html5的语义化标签。针对旧版浏览器，引用html5shiv.js进行兼容调整。

```html
<!-- bad -->
<div class="header"></div>
<div class="footer"></div>

<!-- good -->
<header class="header"></header>
<footer class="footer"></footer>
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

#### 变量命名<a name="js-name"></a>
> js变量命名按照类型进行区分，需要突出属性特征、用途。

