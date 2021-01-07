# Learning HTML



## 基本结构

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>页面标签中的文档标题</title>
	</head>
	<body>
 
		<h1>内容中的一个大标题</h1>
 
		<p>一个段落。</p>
 
	</body>
</html>
```

- `<!DOCTYPE html>` 声明为 HTML5 文档
- `<html>` 元素是 HTML 页面的根元素
- `<head>` 元素包含了文档的元（meta）数据，如 `<meta charset="utf-8">` 定义网页编码格式为 **utf-8**。
- `<body>` 元素包含了可见的页面内容

`<!DOCTYPE>` 声明不区分大小写: `<!DOCTYPE html> <!DOCTYPE HTML> <!doctype html> <!Doctype Html>` .

对于中文网页需要使用 `<meta charset="utf-8">` 声明编码，否则会出现乱码。

### `head`元素

`<head>` 元素包含了所有的头部标签元素。在 `<head>`元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

可以添加在头部区域的元素标签为: `<title>`, `<style>`,` <meta>`, `<link>`, `<script>`, `<noscript>`,`<base>`.

### `<base> `元素

`<base>`标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接

### `<link>`元素

`<link>` 标签定义了文档与外部资源之间的关系。`<link> `标签通常用于链接到样式表:

```html
<link rel="stylesheet" type="text/css" href="mystyle.css">
```

### `<style>`元素

`<style> `标签定义了HTML文档的样式文件引用地址.在`<style> `元素中你也可以直接添加样式来渲染 HTML 文档:

```html
<style type="text/css">
body {background-color:yellow}
p {color:blue}
</style>
```

### `<meta>`元素

`<meta>` 标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。`<meta>` 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。`<meta> `一般放置于` <head>` 区域.

#### 示例

为搜索引擎定义关键词：`<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">`

为页面定义描述内容：`<meta name="description" content="描述内容">`

定义网页作者：`<meta name="author" content="Deslate">`

每30秒钟刷新当前页面: `<meta http-equiv="refresh" content="30">`

### `<script>`元素

详细内容请直接移步：[LearningJavaScript](LearningJavaScript.md) 

## body常用元素

### HTML标题

```html
<h1>这是一个一级标题</h1>
<h6>这是一个六级标题</h6>
```

### HTML段落

```html
<p>这是一个段落。</p>
```

### HTML链接

HTML 链接通过标签 ` <a>` 来定义.

```html
<a href="https://www.runoob.com">这是一个链接</a>
```

> **注释：** 请始终将正斜杠添加到子文件夹。假如这样书写链接：href="https://www.baidu.com"，就会向服务器产生两次 HTTP 请求。这是因为服务器会添加正斜杠到这个地址，然后创建一个新的请求，就像这样：href="https://www.baidu.com/"。

图片链接：

```html
<a href="//www.baidu.com/">
	<img  border="0" src="smiley.gif" alt="解释文字" width="32" height="32">
</a>
```

### HTML图像

```html
<img src="/images/logo.png" width="258" height="39" />
```

### 空元素

```html
<br /> 
<p>这个<br>段落<br>演示了分行的效果</p>
```

> 关于大小写：
>
> 万维网联盟（W3C）在 HTML 4 中**推荐**使用小写，而在未来 (X)HTML 版本中**强制**使用小写。

### HTML水平线

```html
<hr>
```

### HTML注释

```html
<!-- 这是一个注释 -->
```

### HTML表格

```html
<table border="1">
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td>row 2, cell 2</td>
    </tr>
</table>
```

<table border="1">     <tr>         <th>Header 1</th>         <th>Header 2</th>     </tr>     <tr>         <td>row 1, cell 1</td>         <td>row 1, cell 2</td>     </tr>     <tr>         <td>row 2, cell 1</td>         <td>row 2, cell 2</td>     </tr> </table>

### HTML列表

有序列表

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```

无序列表

```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>
```

自定义列表

```html
<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>
```

### HTML区块:`<div>`和`<span>`

块级元素`<h1>, <p>, <ul>, <table>`与内联元素` <b>, <td>, <a>, <img>`区别在于有无折行

HTML `<div> `元素是块级元素，它可用于组合其他 HTML 元素的容器。`<div> `元素没有特定的含义。除此之外，由于它属于块级元素，浏览器会在其前后显示折行。如果与 CSS 一同使用，`<div>` 元素可用于对大的内容块设置样式属性。`<div>` 元素的另一个常见的用途是文档布局。

HTML `<span> `元素是内联元素，可用作文本的容器`<span>` 元素也没有特定的含义。 当与 CSS 一同使用时，`<span> `元素可用于为部分文本设置样式属性。

使用`<div>`和`<span>`可对页面进行布局：

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>布局示例</title> 
</head>
<body>
 
<div id="container" style="width:500px">
 
<div id="header" style="background-color:#FFA500;">
<h1 style="margin-bottom:0;">主要的网页标题</h1></div>
 
<div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript</div>
 
<div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;">
内容在这里</div>
 
<div id="footer" style="background-color:#FFA500;clear:both;text-align:center;">
底部</div>
 
</div>
 
</body>
</html>
```

<!DOCTYPE html> <html> <head>  <meta charset="utf-8">  <title>布局示例</title>  </head> <body>   <div id="container" style="width:500px">   <div id="header" style="background-color:#FFA500;"> <h1 style="margin-bottom:0;">主要的网页标题</h1></div>   <div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;"> <b>菜单</b><br> HTML<br> CSS<br> JavaScript</div>   <div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;"> 内容在这里</div>   <div id="footer" style="background-color:#FFA500;clear:both;text-align:center;"> 底部</div>   </div>   </body> </html>

### HTML表单

表单元素是允许用户在表单中输入内容,比如：文本域(textarea)、下拉列表、单选框(radio-buttons)、复选框(checkboxes)等等。

```html
<form>
.
input 元素
.
</form>
```

表单中的input元素包括：

#### 文本域

```html
<input type="text" name="firstname"><br>
```

#### 密码字段

```html
Password: <input type="password" name="pwd">
```

#### 单选按钮（Radio Buttons）

```
<form>
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
</form>
```

<form>
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
</form>

#### 复选框（Checkboxes）

```
<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car 
</form>
```

<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car 
</form>

#### 提交按钮(Submit Button)

```
<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>
```

<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>

### HTML框架

```
<iframe src="./References/html/GitTutorial.html" frameborder="0"></iframe>
```

<iframe src="./References/html/GitTutorial.html" frameborder="0"></iframe>

下面示例是点击链接加载iframe页面：

```
<iframe src="" name="iframe_a"></iframe>
<p><a href="./References/html/GitTutorial.html" target="iframe_a">Load Content</a></p>
```

（此处无法演示）

### HTML文本格式化

#### 文本格式化标签

| 标签       | 描述                          |
| :--------- | :---------------------------- |
| `<b>`      | 定义<b>粗体文本</b>           |
| `<em>`     | 定义<em>着重文字</em>         |
| `<i>`      | 定义<i>斜体字</i>             |
| `<small>`  | 定义<small>小号字</small>     |
| `<strong>` | 定义<strong>加重语气</strong> |
| `<sub>`    | 定义<sub>下标字</sub>         |
| `<sup>`    | 定义<sup>上标字</sup>         |
| `<ins>`    | 定义<ins>插入字(下划线)</ins> |
| `<del>`    | 定义<del>删除字(删除线)</del> |

#### HTML "计算机输出" 标签

| 标签     | 描述                                      |
| :------- | :---------------------------------------- |
| `<code>` | 定义计算机代码 <code>computer code</code> |
| `<kbd>`  | 定义键盘码 <kbd>keyboard input</kbd>      |
| `<samp>` | 定义计算机代码样本 （示例如下）           |
| `<var>`  | 定义变量 <var>variable</var>              |
| `<pre>`  | 定义预格式文本(示例如下)                  |

<samp> code sample </samp>

<pre>pre-formatted text</pre>

#### HTML 引文, 引用, 及标签定义

| 标签           | 描述                          |
| :------------- | :---------------------------- |
| `<abbr>`       | 定义<abbr>缩写</abbr>         |
| `<address>`    | 定义<address>地址</address>   |
| `<bdo>`        | 定义<bdo>文字方向</bdo>       |
| `<blockquote>` | 定义长的引用(示例如下)        |
| `<q>`          | 定义<q>短的引用语</q>         |
| `<cite>`       | 定义<cite>引用、引证</cite>   |
| `<dfn>`        | 定义<dfn>一个定义项目。</dfn> |

<blockquote>长的引用</blockquote>

## HTML属性

属性一般描述于**开始标签**，属性总是以名称/值对的形式出现，比如 `name="value"` .

基本属性：

| **属性** | **描述**                                                     |
| -------- | ------------------------------------------------------------ |
| class    | 为html元素定义一个或多个类名（classname）(类名从样式文件引入) |
| id       | 定义元素的唯一id                                             |
| style    | 规定元素的行内样式（inline style）                           |
| title    | 描述了元素的额外信息 (作为工具条使用)                        |

1. class 属性可以多用 **class=" "** （引号里面可以填入多个class属性）
2. id 属性只能单独设置 **id=" "**（只能填写一个，多个无效）

### HTML链接target属性

定义在新窗口中打开链接

```
<a href="https://..." target="_blank">链接文本</a>
```

### HTML链接id属性

id属性可用于创建在一个HTML文档书签标记。书签是不以任何特殊的方式显示，在HTML文档中是不显示的，所以对于读者来说是隐藏的。

设置一个标签

```
<a id="emm">一个锚</a>
```

在本页访问它

```
<a href="#emm">访问它</a>
```

跨页访问它

```
<a href="https://balabala.html#emm"> 跨页访问 </a>
```

### HTML 图像设置高度与宽度

```
<img src="pulpit.jpg" alt="Pulpit rock" width="304" height="228">
```

### HTML图像使用map

```
<img src="planets.gif" width="145" height="126" alt="Planets" usemap="#planetmap">

<map name="planetmap">
  <area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.htm">
  <area shape="circle" coords="90,58,3" alt="Mercury" href="mercur.htm">
  <area shape="circle" coords="124,58,8" alt="Venus" href="venus.htm">
</map>
```



## CSS样式

CSS 是在 HTML 4 开始使用的,是为了更好的渲染HTML元素而引入的.

CSS 可以通过以下方式添加到HTML中:

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 `<head>` 区域使用 `<style>` **元素** 来包含CSS
- 外部引用 - 使用外部 CSS **文件**

最好的方式是通过外部引用CSS文件.

### 三种方式

#### 内联样式

当特殊的样式需要应用到个别元素时，就可以使用内联样式。 使用内联样式的方法是在相关的标签中使用样式属性。样式属性可以包含任何 CSS 属性。以下实例显示出如何改变段落的颜色和左外边距：

```
<p style="color:blue;margin-left:20px;">这是一个段落。</p>
```

#### 内部样式表

```
<head>
<style type="text/css">
body {background-color:yellow;}
p {color:blue;}
</style>
</head>
```

#### 外部样式表

```
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```



