# $\small HTML 5$ 笔记

[TOC]

$~~~~~$ 在网页中， HTML 确定内容（如有几个按钮，几个文字），CSS 确定样式（如按钮长什么样，文字用什么字体，什么大小；内容的位置怎么排），JS 确定效果（如按钮按下去该返回什么样的结果）
$~~~~~$ 不过 HTML 作为网站最核心的内容，其本身也是具有一定的样式和效果的。

大部分 html 标签都是写在 `body` 标签中的，如果不是下面会说的

## 基础元素

html5 中的基础元素主要由以下内容构成，有了这些内容，就已经算一个完整的 html5 文件了。

HTML5

```html
<!DOCTYPE html>
<html>
<head>
<title>test01</title>
</head>
<body>


</body>
</html>
```

- `<!DOCTYPE html>` ：html5 的开头标签，用于告诉浏览器这是一个需要解析的 html5 页面
- `<html></html>` : html 所有内容都在这个标签内进行编写
- `<head></head>` : html 的头部便签，用于存放引用，页面属性设置，页面标题等
- `<title>test01</title>` : 页面的标题
- `<body></body>` : html 的主体标签，所有在页面上显示

## 基本标签

### 标题

html 用 `h1,h2,……,h6` 来表达标签

```html
<h1>这是标题 1</h1>
<h2>这是标题 2</h2>
<h3>这是标题 3</h3>
<h4>这是标题 4</h4>
<h5>这是标题 5</h5>
<h6>这是标题 6</h6>
```

从 `h1` 到 `h6` 标题等级依次降低，文字大小也是。

### 段落

HTML 段落是通过标签 `<p>` 来定义的。

```html
<p>段落1</p>
<p>段落1</p>
```

### 不分段标签

`<a>` 标签可以用于设置不分段的内容

```html
<a>这是一个链接</a>
<a>这是一个链接</a>
```

### 超链接

超链接通过 `<a>` 标签的 `href` 属性设置，点击标签内设置的文字就可以跳转到 `href` 设置的地址。

```html
<a href="https://www.baidu.com">这是一个链接</a>
```

超链接同样也可以作为书签使用，跳转到本页面的某段文字，实现方法是通过超链接指定文字所在标签的 id 。

```html
<p>
<a href="#C4">查看章节 4</a>
</p>

<h2>章节 1</h2>
<p>这边显示该章节的内容……</p>

<h2>章节 2</h2>
<p>这边显示该章节的内容……</p>

<h2>章节 3</h2>
<p>这边显示该章节的内容……</p>

<h2 id="C4">章节 4</h2>
<p>这边显示该章节的内容……</p>

<h2>章节 5</h2>
<p>这边显示该章节的内容……</p>

<h2>章节 6</h2>
<p>这边显示该章节的内容……</p>

<h2>章节 7</h2>
<p>这边显示该章节的内容……</p>
```

> 指定标签 id 的方式为：`#`+`id名` 。

### 图像

图像通过 `<img>` 标签来定义，通过 `src` 属性来指定图片路径。
图片路径可以使用绝对路径和相对路径。

```html
<img src="/images/logo.png" width="258" height="39" />
```

主要有以下几个属性：

- `alt="XXXX"` : 当图片无法加载出来的话，就显示 alt 定义的文字
- `width="XXX" height="XXX"` ：指定高度与宽度

### 音频

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
  您的浏览器不支持 audio 元素。
</audio>
```

浏览器会依次从上向下执行，当第一个音频文件格式不支持就会使用第二个。
当浏览器不支持 `<audio>` 标签时就会显示标签中的文本。

该标签主要有以下几个属性：

- `autoplay` : 无值属性，出现该属性，则音频在就绪后马上播放。
- `controls` : 无值属性，出现该属性，则向用户显示音频控件（比如播放/暂停按钮）。
- `loop` : 无值属性，出现该属性，则每当音频结束时重新开始播放。
- `muted` : 无值属性，出现该属性，则音频输出默认为静音。
- `src` : 音频文件的 url 。

### 视频

```html
<video width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.ogg" type="video/ogg">
    您的浏览器不支持 video 标签。
</video>
```

视频文件的主要属性与音频一样，并多了高度和宽度属性。

### 页面

通过 `<iframe>` 标签，可以嵌入 html 页面。

```html
<iframe src="http://www.runoob.com">
  <p>您的浏览器不支持  iframe 标签。</p>
</iframe>
```

- `width="200" height="200"` : 指定高度宽度。
- `src` : 文件的 url 。

### 空元素

无法镶嵌内容的标签叫做空标签，也叫做空元素。
事实上，所有的标签都可以叫做元素。

- `<br/>` : 换行标签

### 文本格式化

文本格式化最常使用的有以下几种基础方式：加粗，斜体，上标，下标，高亮，强调

```html
<b>加粗文本</b><br><br>
<i>斜体文本</i><br><br>
这是 <sub> 下标</sub> 和 <sup> 上标</sup><br><br>
<mark>高亮字体</mark>
<strong>强调文本</strong>
```

## form

form 表单标签，通常和 input 和 button 一起使用，表单中的属性可以视为一组数组。

一般表单长这样

```html
<form name="" action="" method="">
    <input type="text" id="" name="">
    <input type="text" id="" name="">
    <button type="submit">提交按钮</button>
</form>
```

form 的 `action=""` , 设置的是提交地址，如果在 spring 项目里，这一般是一个后端映射地址，即 `@RequestMapping(value = "")` 里的 value ，也可以是整体的 url ，这时候就是跨域访问的事了， **[springboot的请求映射](../../../JAVA/springboot/springboot基础/请求映射.md)** 。

form 的 `name=""` , name 不只作为 web 的一个识别属性，也是一个后端的识别属性，必须一一对应。
form 的 `method=""` , 用于设置发送请求的方法，是 get 还是 post 。
当点击 submit 定制的按钮时，就会将表单内的数据提交到对应的地址上。

form 如果需要提交文件，就要把 `enctype` 属性改为 `multipart/form-data` 。

```html
<form action="http://localhost:8081/thingsparse/addorupdthingsparse" method="post" enctype="multipart/form-data">
     <input type="file" name="file" value="选择jar包"/>
     <input id="submit_form" type="submit" class="btn btn-success save" value="保存"/>
</form>
```

### input

input 是一个多功能标签，其既可以用作文本输入，又可以用作按钮，其功能设定主要通过 `type` 属性，该属性常用的有以下几个值。

```html
<input type="text" name="usrname">
<input type="password" name="usrname">
<input type="radio" name="usrname">
<input type="reset" name="usrname">
<input type="file" name="usrname">
<input type="image" name="usrname">
<input type="submit" name="usrname">
```

- `text` : 文本模式
- `password` : 密码模式，输入的数据会被隐藏
- `radio` : 单选按钮
- `reset` : 清除按钮，会清除表单内的输入数据
- `file` : 文件上传选项
- `image` : 定义提交按钮样式为图片，需要与 src 属性配合使用
- `submit` : 提交按钮。

此外，input 还有一些常用的属性：

- `name="XXXX"` : 规定 input 元素的名称，当向 url 提交时，这个就是提交的数据的名称。
- `value` : 指定该属性的值，通常用在选择按钮上。

## 表格

通过以下方式来表现， table 定义表，tr 定义排 ，td 定义列。

```html
<table border="1">
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

$~~~~~$ 为了更清楚的注明表头表中表尾，与避免类似分页无表头等错误，需使用以下代码来规范表格。

```html
<table>
  <thead>
    <tr>
      <th>存款时间</th>
      <th>存款利率</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td colspan="2">注：数据来源于中国工商银行</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>1年</td>
      <td>1.75</td>
    </tr>
    <tr>
      <td>2年</td>
      <td>2.25</td>
    </tr>
    <tr>
      <td>3年</td>
      <td rowspan="2">2.75</td>
    </tr>
    <tr>
      <td>5年</td>
    </tr>
  </tbody>
</table>
```

- 通过 `<th></th>` 来指定表格表头内容
  > 这个标签最大的作用就是编码便利性。
- `<thead></thead>` : 在内部定义的表格内容必定会显示在表格第一栏，分页也是一样。
- `<tbody></tbody>` : 在内部定义表格主体内容。
  > 这个标签主要用在帮助后端返回的表单数据定位。
- `<tfoot></tfoot>` : 在内部定义的表格内容必定会显示在表格最后一栏，分页也是一样。
- `colspan="2"` : 横向跨格数量
- `rowspan="2"` : 纵向跨格数量

### 下拉菜单

$~~~~~$ html5 使用 `<select>` 标签来实现下拉选项，使用 `<option>` 来表示其中的选项。

```html
<select>
  <option value ="volvo">Volvo</option>
  <option value ="saab">Saab</option>
  <option value="opel">Opel</option>
  <option value="audi">Audi</option>
</select>
```

## head 标签内部元素

head 标签内部有许多元素，下面介绍几种常用的元素。

### base

base 标签为全局跳转标签，只要你页面超链接标签中没有指定地址，就会自动跳转到这个地址。

```html
<base href="http://www.baidu.com" target="_blank">
```

### link

link 标签用于指定文档与外部资源之间的关系，常用于连接 CSS 样式文件。

```html
<link rel="stylesheet" type="text/css" href="mystyle.css">
```

### style

`<style>` 标签定义了HTML文档的样式文件引用地址.
`<style>` 经常会用来写渲染样式，可以理解为内置的 CSS 样式。

```html
<head>
<style type="text/css">
body {
    background-color:yellow;
}
p {
    color:blue
}
</style>
</head>
```

> 如果想要在 style 中写 css ，需要指定 type 属性为 text/css 。

### meta

`<meta>` 标签描述了一些基本的元数据，元数据也不显示在页面上，但会被浏览器解析。

通常来说，常用的是以下的内容

```html
<!-- 为搜索引擎定义关键词: -->
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">

<!-- 为网页定义描述内容: -->
<meta name="description" content="免费 Web & 编程 教程">

<!-- 定义网页作者: -->
<meta name="author" content="Runoob">

<!-- 每30秒钟刷新当前页面: -->
<meta http-equiv="refresh" content="30">

<!-- 指定网页字符编码格式 --->
<meta charset="UTF-8">
```

## 列表

列表又分有序列表和无序列表

### 有序列表

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```

### 无序列表

```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>
```

## 块： div 与 span

$~~~~~$ HTML `<div>` 元素是块级元素，它可用于组合其他 HTML 元素的容器。
$~~~~~$ `<div>` 元素没有特定的含义。除此之外，由于它属于块级元素，浏览器会在其前后显示折行。
$~~~~~$ 如果与 CSS 一同使用，`<div>` 元素可用于对大的内容块设置样式属性。
$~~~~~$ `div` 内部的元素都无法超过 div 的大小，如你在 div 中放入了一张超过 div 大小的图片，那么图片就会有显示不全。

```html
<div>
<p>aaaaaaaaa</p>
<p>aaaaaaaaa</p>
<p>aaaaaaaaa</p>
</div>
```

> 单纯使用 div 意义不大， div 需要与 CSS 样式配合使用，可以做到修改大小，修改布局等。

### span

$~~~~~$ span 是内联元素，即存在其他标签或者某段文字中的标签，不会换行。

```html
<p>我的母亲有 <span style="color:blue">蓝色</span> 的眼睛。</p>
```

## 输入框

输入框有两种，一种是 `input` 标签，一种是 `textarea` 标签。

input 请点击 [input](#form) 阅读。

`<textarea>` : 标签定义多行的文本输入控件。

```html
<textarea rows="10" cols="30">
我是一个文本框。
</textarea>
```

- 文本区中可容纳无限数量的文本，其中的文本的默认字体是等宽字体（通常是 Courier）。
- 可以通过 cols 和 rows 属性来规定 textarea 的尺寸，不过更好的办法是使用 CSS 的 height 和 width 属性。
