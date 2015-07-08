# WOQU.com 代码规范

*为WOQU.com前端er提供的代码规范约定，覆盖HTML、CSS、JS。*

## 目录
  1. [HTML](#html)
     - [Semantic](#semantic)
  1. [CSS](#css)
     - [Class Name](#class-name)
     - [ID Name](#id-name)
  1. [JAVASCRIPT](#javascript)

## {HTML}<a name="html"></a>

#### Semantic
> 语义化，使用html5的语义化标签。针对旧版浏览器，引用html5shiv.js进行兼容调整。

```html
//bad
<div class="header"></div>
<div class="footer"></div>

//good
<header class="header"></header>
<footer class="footer"></footer>
```

## {CSS}<a name="css"></a>

#### Class Name<a name="class-name"></a>
> class命名，全小写，使用中横线分割。单词间使用下横线。

```css
//bad
.header_left      { xxx }
.headerLeft       { xxx }
.HeaderLeft       { xxx }

//good
.header-left      { xxx }
.usa-main         { xxx }
.new_zealand-main { xxx }
```

#### ID Name<a name="id-name"></a>
> id命名，小驼峰写法，中间无中横线或者下横线。

```css
//bad
#Logo             { xxx }
#header_logo      { xxx }
#header-logo      { xxx }
#HeaderLogo       { xxx }

//good
#logo             { xxx }
#headerLogo       { xxx }
#headerLogoWrap   { xxx }

```

## {JAVASCRIPT}<a name="javascript"></a>
