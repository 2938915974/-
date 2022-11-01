# $\small CSS3$ 笔记

[TOC]

**量化参数** ： 该属性的参数以百分比，数字的方式使用
**无需声明** ：该属性不需要声明属性名
**必选属性** ：该属性的上级属性必须要有该属性才能生效。
**可选属性** ：该属性的上级属性生效不需要有该属性
****

## 写法

1. CSS3 有三种写法，一种就是在 html 的对应标签之中过  `style` 属性去定义

    ```html
    <p style="color:blue;margin-left:20px;">这是一个段落。</p>
    ```

    ----
    <p style="color:blue;margin-left:20px;">这是一个段落。</p>

    ----

2. 也可以通过在HTML文档头部 `<head>` 区域使用 `<style>` 元素来包含CSS，在这里使用 CSS 样式的规范与单独列举文件一样，需要指定类名或名字。
    $~~~~~$ 指定类名的格式为 `.[类名]` ,指定名字的格式为 `#[name]` 。
    $~~~~~$ 当然也可以直接指定标签，这样所有标签都会默认采用这个格式，指定标签不需要带前缀，如

    ```html
    <head>
    <style type="text/css">
    body {background-color:yellow;}
    p {color:blue;}
    </style>
    </head>
    ```

    > 不建议指定名字，因为名字通常有其他用途，建议采用类名，即 `class= "xxx"` 中的名字。
    > 标签内嵌的权限大于其他权限，单独 CSS 文件与 `style` 标签权限一样。

3. 单独建立 CSS 文件方法为：
   1. 新建一个后缀为 CSS 的文件。
   2. 在内部书写样式，内容与在 style 标签中写的一样

        ```css
        body {background-color:yellow;}
        p {color:blue;}
        ```

   3. 使用该样式需要将该文件引用到 html 文件中，这时需要使用 `link` 标签中写的一样

        ```html
        <link rel="stylesheet" type="text/css" href="mystyle.css">
        ```

## CSS 基础标签

如果某个属性中带有多个属性，要想实现多个属性同时实现，可以通过

```CSS
{
    属性:[属性1]:[参数] [属性2]:[参数] …… ;
}
```

如图,每个属性间空一格就行。

## 通用参数（几乎通用）

### 量化单位

**绝对长度：**

- `cm` : 厘米。
- `mm` : 毫米。 试一试
- `px` : 像素 (1px = 1/96th of 1in)

**相对长度：**

- `em` : 相对于元素的字体大小（font-size）（2em 表示当前字体大小的 2 倍）
- `rem` : 相对于根元素的字体大小（font-size）
    根元素，即为 html 标签的元素，也可以通过 css 去修改，如

    ```CSS
    html {
      font-size:16px;
    }
  ```

- `vw` : 相对于视口*宽度的 1% 。
- `vh` : 相对于视口*高度的 1% 。
- `%` : 相对于父元素。

### 常用参数

大部分的属性都有以下的参数

- `inherit` : 从父元素继承该属性的值。
- `initial` : 规定属性为默认值。

### 块级元素属性

- `display` : 规定元素应该生成的框的类型。
  - `none` : 此元素不会被显示。
  - `block` : 此元素将显示为块级元素，此元素前后会带有换行符。
  - `inline` : 默认。此元素会被显示为内联元素，元素前后没有换行符。
  - `inline-block` : 行内块元素。允许在元素上设置宽度和高度，会保留边距值。
  - `list-item` : 此元素会作为列表显示。
  - `run-in` : 此元素会根据上下文作为块级元素或内联元素显示。
  - `table` : 此元素会作为块级表格来显示（类似 `<table>`），表格前后带有换行符。
  - `inline-table` : 此元素会作为内联表格来显示（类似 `<table>`），表格前后没有换行符。
  - `table-row-group` : 此元素会作为一个或多个行的分组来显示（类似 `<tbody>`）。
  - `table-header-group` : 此元素会作为一个或多个行的分组来显示（类似 `<thead>`）。
  - `table-footer-group` : 此元素会作为一个或多个行的分组来显示（类似 `<tfoot>`）。
  - `table-row` : 此元素会作为一个表格行显示（类似 `<tr>`）。
  - `table-column-group` : 此元素会作为一个或多个列的分组来显示（类似 `<colgroup>`）。
  - `table-column` : 此元素会作为一个单元格列显示（类似 `<col>`）
  - `table-cell` : 此元素会作为一个表格单元格显示（类似 `<td>` 和 `<th>`）
  - `table-caption` 此元素会作为一个表格标题显示（类似 `<caption>`）

- `width` : 定义元素宽度
  - `auto` : 自动分配
  - 量化参数
- `max-width` : 元素的最大宽度。量化参数

> 高度写法也差不多。

- `margin` : 外边距。
  - `auto` : 浏览器自动设置。
  - 量化参数

> 也可以指定单个边的外边距，见自己软件的命令提示。

- `position` : 规定元素的定位类型。
  - `absolute` : 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
  - `fixed` : 生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
  - `relative` : 生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。
  - `static` : 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。
  - `overflow` : 属性指定在元素的内容太大而无法放入指定区域时是剪裁内容还是添加滚动条。
  - `visible` : 默认。溢出没有被剪裁。内容在元素框外渲染
  - `hidden` : 溢出被剪裁，其余内容将不可见
  - `scroll` : 溢出被剪裁，同时添加滚动条以查看其余内容
  - `auto` : 与 scroll 类似，但仅在必要时添加滚动条

- `float` : 属性用于定位和格式化内容，例如让图像向左浮动到容器中的文本那里。
  - `left` : 元素浮动到其容器的左侧
  - `right` - 元素浮动在其容器的右侧
  - `none` : 元素不会浮动（将显示在文本中刚出现的位置）。默认值。

- `clear` : 规定元素的哪一侧不允许其他浮动元素。
  - `left` : 元素浮动到其容器的左侧
  - `right` : 元素浮动在其容器的右侧
  - `none` : 元素不会浮动（将显示在文本中刚出现的位置）。默认值。

  > 有关于浮动溢出问题，可以参考以下两个 CSS 代码

  ```CSS
    .clearfix::after {
      content: "";
      clear: both;
      display: table;
    }
    ```

    ```CSS
    .clearfix {
      overflow: auto;
    }
    ```

- `overflow` : 规定当内容溢出元素框时发生的事情
  - `visible` : 默认值。内容不会被修剪，会呈现在元素框之外。
  - `hidden` : 内容会被修剪，并且其余内容是不可见的。
  - `scroll` : 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。
  - `auto` : 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。

- `box-sizing` : 属性允许您以特定的方式定义匹配某个区域的特定元素。
  > 控制边框内边距。
  - `content-box` : 宽度和高度分别应用到元素的内容框。在宽度和高度之外绘制元素的内边距和边框。

  - `border-box` : 为元素设定的宽度和高度决定了元素的边框盒。
  就是说，为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。
  通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。

- `border-radius` : 定义元素角的半径。（圆角定义）量化参数。

- `background-color` : 定义背景颜色。

  ```CSS
    p{
        background-color:#b0c4de;
    }
  ```

  ----
  <p style="background-color:#b0c4de;">Hello World!</p>

  ----

- `background-image` : 属性描述了元素的背景图像。
  - `url` : 图片url地址
  - `linear-gradient(color1,color2,color3)` : 渐变颜色。

    ```css
    body{
    background-image:url('http://static.runoob.com/images/mix/paper.gif');
    }
    ```

- `background-repeat` : 指定背景图片平铺模式

  - `repeat` : 默认。背景图像将在垂直方向和水平方向重复。
  - `repeat-x` : 背景图像将在水平方向重复。
  - `repeat-y` : 背景图像将在垂直方向重复。
  - `no-repeat` : 背景图像将仅显示一次。
  - `inherit` :  从父元素继承 background-repeat 属性。

- `background-position` : 指定背景显示位置。
  - 直接属性，效果如名：
    - top left
    - top center
    - top right
    - center left
    - center center
    - center right
    - bottom left
    - bottom center
    - bottom right
  - `x% y%` : 第一个值是水平位置，第二个值是垂直位置，定义为从左往右，从上往下。

- `background` : 该属性可以不声明属性名直接使用以下几个属性
  - `border-radius`
  - `background-color`
  - `background-image`
  - `background-repeat`
  - `background-position`

  ```CSS
  body {background:#ffffff url('img_tree.png') no-repeat right top;}
  ```

- `box-sizing` : 允许我们在元素的总宽度和高度中包括内边距（填充）和边框。
  默认情况下，元素的宽度和高度是这样计算的：
  width + padding + border = 元素的实际宽度
  height + padding + border = 元素的实际高度
  添加了 `box-sizing` 标签后，元素实际高度就是 width ，height 同样。

  ```CSS
  /* CSS代码 */
  .div1 {
    width: 300px;
    height: 100px;
    border: 1px solid blue;
    box-sizing: border-box;

  }

  .div2 {
    width: 300px;
    height: 100px;  
    padding: 50px;
    border: 1px solid red;
    box-sizing: border-box;
  }
  ```

  ```html
  <!-- html代码 -->
  <div class="div1">现在，两个 div 的尺寸是一样的！</div>
  <br>
  <div class="div2">Hello！</div>
  ```

### 行内元素属性

### 懒得分的属性

- `resize` : 规定是否可由用户调整元素的尺寸。
  - `none` : 用户无法调整元素的尺寸。
  - `both` : 用户可调整元素的高度和宽度。
  - `horizontal` : 用户可调整元素的宽度。
  - `vertical` : 用户可调整元素的高度。

  ```CSS
  /* CSS代码 */
  div {
    border: 2px solid;
    padding: 20px; 
    width: 300px;
    resize: horizontal;
    overflow: auto;
  }
  ```

  ```html
  <!-- html代码 -->
  <div>
    <p>只允许用户调整 div 元素的宽度。</p>
    <p>如需调整：请点击并拖动 div 元素的右下角。</p>
  </div>
  ```

- `opacity` : 透明度，属性的取值范围为 0.0-1.0。值越低，越透明。

- `object-fit` : 规定应如何调整 `<img>` 或 `<video>` 的大小来适应其容器。
  - `fill` : 默认值。调整替换内容的大小来填充元素的内容框。如有必要，对象将被拉伸或挤压。
  - `contain` : 缩放被替换的内容以保持其宽高比，同时适合元素的内容框。
  - `cover` : 调整被替换内容的大小，以在填充元素的整个内容框时保持其长宽比。该对象将被裁剪。
  - `none` : 替换的内容不会调整大小。
  - `scale-down` : 内容的尺寸与 none 或 contain 中的一个相同，取决于它们两个之间谁得到的对象尺寸会更小一些。
  - `initial` : 将此属性设置为其默认值。

### 组合器

CSS 中有四种不同的组合器：

- 后代选择器 (空格)
- 子选择器 (>)
- 相邻兄弟选择器 (+)
- 通用兄弟选择器 (~)

```CSS
/* 下面的例子选择 <div> 元素内的所有 <p> 元素 */
div p {
  background-color: yellow;
}
/* 只要在<div> 中，就算是 子标签的子标签也会实现*/
```

```CSS
/* 下面的例子选择属于 <div> 元素子元素的所有 <p> 元素 */
div > p {
  background-color: yellow;
}
```

```CSS
/* 下面的例子选择紧随 <div> 元素之后的所有 <p> 元素 */
div + p {
  background-color: yellow;
}
/* 两个标签处于同一级并且挨着的 */
```

```CSS
/* 下面的例子选择属于 <div> 元素的同级元素的所有 <p> 元素 */
div ~ p {
  background-color: yellow;
}
```

## div(未完成)

## 文本

对于文本，通常会使用以下几个属性

- `color` : 规定字体颜色

  ```CSS
  /* CSS 代码 */
  .test {color:#00ff00;}
   ```

   ```html
  <!-- html代码 -->
  <a class="test"></a>
  ```

- `text-align` : 文本的水平对齐方式。
  - `left` : 左对齐
  - `right` : 右对齐
  - `center` : 居中对齐
  - `justify` : 两端对齐
- `text-decoration` : 设置文本装饰
  - `none` : 删除文本样式，通常用于删除链接下划线。
  - `underline` : 下划线
  - `overline` : 上划线
  - `line-through` : 删除线
  - `blink` : 文本闪烁

- `text-indent` : 定义首行缩进值。*量化参数*
- `letter-spacing` : 定义文本中字符的间距。*量化参数*

- `text-shadow` : 文本阴影（内容需要严格按照下方属性顺序排列）
  - `h-shadow` : 水平阴影的位置。*允许负值，必选属性，量化参数，无需声明*
  - `v-shadow` : 垂直阴影的位置。*允许负值，必选属性，量化参数，无需声明*
  - `blur` : 阴影的模糊距离。*可选参数，量化参数，无需声明*
  - `color` : 阴影的颜色。*可选参数，无需声明*

  ```CSS
  /*例*/
  text-shadow: 5px 5px 5px #FF0000;
  ```

- `font-family` : 设定文本的字体样式，如微软雅黑，宋体。
- `font-style` : 设定字体倾斜
  - `normal` : 浏览器显示一个标准的字体样式
  - `italic` : 浏览器会显示一个斜体的字体样式
  - `oblique` : 浏览器会显示一个倾斜的字体样式

- `font-size` ：设置字体大小。*量化参数*
- `font-weight` : 设置字体粗细。
  - `normal` : 定义标准粗细的字符。
  - `bold` : 定义粗体字符。
  - `bolder` : 定义更粗的字符。
  - `lighter` : 定义更细的字符。
  - `100,200,……,900` : 定义由粗到细的字符。400 等同于 normal，而 700 等同于 bold。

- `font` : 属性可不声明使用以下几个属性的参数
  - `font-size`
  - `font-weight`
  - `font-family`
  - `font-style`

- `text-overflow` : 属性规定应如何向用户呈现未显示的溢出内容。
  - `clip` : 修剪文本。
  - `ellipsis` : 显示省略符号来代表被修剪的文本。
  - `string` : 使用给定的字符串来代表被修剪的文本。

  ```CSS
  /* CSS代码 */
  .test{
    white-space:nowrap; 
    width:12em; 
    overflow:hidden; 
    border:1px solid #000000;
    text-overflow:ellipsis;
  }
  ```

  ```html
  <div class="test">This is some long text that will not fit in the box</div>
  ```

- `word-wrap` : 使长文字能够被折断并换到下一行。
  - `normal` : 只在允许的断字点换行（浏览器保持默认处理）。
  - `break-word` : 在长单词或 URL 地址内部进行换行。

  ```CSS
  /* CSS代码 */
  p.test1 {
    width: 140px; 
    border: 1px solid #000000;
    word-break: keep-all;
  }
  ```

  ```html
  <!-- html代码 -->
  <p class="test1">This paragraph contains some text. This line will-break-at-hyphens.</p>
  ```

## 列表

列表分为无序列表和有序列表

无序列表以 `<ul>` 标签为表标签，有序列表以 `<ol>` 标签为表标签，表中项目皆以 `<il>` 为标签。

```html
<!-- 无序列表 -->
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Coca Cola</li>
</ul>

<!-- 有序列表 -->
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Coca Cola</li>
</ol>
```

- `list-style-type` : 列表中项目的标记符号样式

  - 通用：
    - `none` : 无标记。

  - 无序列表使用：
    - `disc` : 默认。标记是实心圆。
    - `circle` : 标记是空心圆。
    - `square` : 标记是实心方块。
  - 有序列表使用：
    - `decimal` : 标记是数字。
    - `decimal-leading-zero` : 0开头的数字标记。(01, 02, 03, 等。)
    - `lower-roman` : 小写罗马数字(i, ii, iii, iv, v, 等。)
    - `upper-roman` : 大写罗马数字(I, II, III, IV, V, 等。)
    - `lower-alpha` : 小写英文字母The marker is lower-alpha (a, b, c, d, e, 等。)
    - `upper-alpha` : 大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。)
    - `lower-greek` : 小写希腊字母(alpha, beta, gamma, 等。)
    - `lower-latin` : 小写拉丁字母(a, b, c, d, e, 等。)
    - `upper-latin` : 大写拉丁字母(A, B, C, D, E, 等。)
    - `hebrew` 传统的希伯来编号方式
    - `armenian` 传统的亚美尼亚编号方式
    - `georgian` 传统的乔治亚编号方式(an, ban, gan, 等。)
    - `cjk-ideographic` 简单的表意数字
    - `hiragana` 标记是：a, i, u, e, o, ka, ki, 等。（日文片假名）
    - `katakana` 标记是：A, I, U, E, O, KA, KI, 等。（日文片假名）
    - `hiragana-iroha` 标记是：i, ro, ha, ni, ho, he, to, 等。（日文片假名）
    - `katakana-iroha` 标记是：I, RO, HA, NI, HO, HE, TO, 等。（日文片假名）

  ```CSS
  /* CSS 样式 */
  ul.a {
    list-style-type: circle;
  }
  ```

  ```html
  <!-- html 代码 -->
  <ul class="a">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li
  </ul>
  ```

- `list-style-image` : 定义以图像为项目序号（通常只会用在无序列表中）
  - `url` : 图片 url 地址。

  ```CSS
  /* CSS代码 */
  ul {
    list-style-image: url('/i/photo/sqpurple.gif');
  }
  ```

  ```html
  <!-- html代码 -->
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
  </ul>
  ```

- `CSS list-style-position` : 定义列表项目标记符号的位置
  - `inside` : 列表项目标记放置在文本以内，且环绕文本根据标记对齐。
  - `outside` : 默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不根据标记对齐。

```CSS
/* CSS代码 */
ul.b {
  list-style-position: inside;
}
```

```html
<!-- html代码 -->
<ul class="b">
  <li>咖啡-用烘焙过的咖啡豆制成的冲泡饮料，烘焙过的咖啡豆是来自咖啡植物的浆果的种子</li>
  <li>茶-一种芳香饮料，通常通过将热水或沸水倒在茶树的固化叶子上而制得，茶树是一种原产于亚洲的常绿灌木（灌木）</li>
  <li>可口可乐-由可口可乐公司生产的碳酸软饮料。该饮料的名称指的是其两种原始成分，即可乐果（一种咖啡因）和古柯叶。</li>
</ul>
```

- `list-style` : 该属性可以不声明使用以下几个属性的参数。
  - `list-style-type`
  - `list-style-position`
  - `list-style-image`

  ```CSS
  /* CSS代码 */
  ul {
    list-style: square inside url("sqpurple.gif");
  }
  ```

  ```html
  <!-- html代码 -->
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
  </ul>
  ```

## 表格

表格常用于后端向前端发送的数据列表，使用 `<table>` 标签进行定义

```CSS
/* CSS代码 */
table, th, td {
  border: 1px solid black;
}
/* 该样式定义了table与th，td都有边框，所以会看到表格是双边框的，如果只需要外边框，不定义th与td边框就行了。 */
```

```html
<!-- html代码 -->
<table>
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
  </tr>
  <tr>
    <td>Bill</td>
    <td>Gates</td>
  </tr>
  <tr>
    <td>Steve</td>
    <td>Jobs</td>
  </tr>
```

表格常用以下几个属性

- `border-collapse` : 属性设置是否将表格边框折叠为单一边框
  - `separate` : 默认值。边框会被分开。不会忽略 border-spacing 和 empty-cells 属性。
  - `collapse` : 如果可能，边框会合并为一个单一的边框。会忽略 border-spacing 和 empty-cells 属性。
- `:nth-child(number)` : 定义某行的样式，number有多中参数，这里主要讲常用的两个。
  - `even` : 奇数行
  - `odd` : 偶数行

## 边框与边距

下列所有元素的数据都可以放在 border 标签中去实现。

- `border-width` : 规定边框宽度。
- `border-color` : 规定边框颜色。
- `border-style` : 规定边框样式。

  下列是参数：
  - `none` : 定义无边框。
  - `hidden` : 与 "none" 相同。不过应用于表时除外，对于表，hidden 用于解决边框冲突。
  - `dotted` : 定义点状边框。在大多数浏览器中呈现为实线。
  - `dashed` : 定义虚线。在大多数浏览器中呈现为实线。
  - `solid` : 定义实线。
  - `double` : 定义双线。双线的宽度等于 border-width 的值。
  - `groove` : 定义 3D 凹槽边框。其效果取决于 border-color 的值。
  - `ridge` : 定义 3D 垄状边框。其效果取决于 border-color 的值。
  - `inset` : 定义 3D inset 边框。其效果取决于 border-color 的值。
  - `outset` : 定义 3D outset 边框。其效果取决于 border-color 的值。

以下 boder 标签需要单独设置。

- `border-radius` : 定义边框为圆角。
  - 属性支持 px，百分比，em

#### 边距

边距分为外边距和内边距。

外边距为外部其他便签与该标签的边距。
内边距，标签内部元素与标签的距离。

##### 外边距

CSS 通过 `margin` 标签来设置外边距，当只设置一个时，对四边生效，设置两个时，分别为上下和左右生效，当然，也可以使用下列代码单独设置某个边框的样式，设置 4 个时，按上左下右生效。

- `margin-top` : 设置上边距。
- `margin-right` : 设置左右边距。
- `margin-bottom` : 设置下边距。
- `margin-left` : 设置左边距。

> 当两个都具有外边距的元素在一起时，它们相邻两个边的外边距只会存在一个，最大的那个。

##### 内边距

内边距标签为 `padding` ，内边距的参数与外边距相同，但属性有些不同，内边距不会合并。
内边距也可以单独指定每个边的属性：

- `padding-top` : 设置上边内边距
- `padding-right` : 设置右边内边距
- `padding-bottom` : 设置下边内边距
- `padding-left` : 设置左边内边距。

bottom : 向下距离

bottom 属性规定了标签与上一个标签的距离。

##### box-shadow ：框阴影

box-shadow 属性向框添加一个或多个阴影。

- `h-shadow` ：必需。水平阴影的位置。
- `v-shadow` : 必需。垂直阴影的位置。允许负值。
- `blur` : 可选。模糊距离。 测试
- `spread` : 可选。阴影的尺寸。
- `color` : 可选。阴影的颜色。
- `inset` : 可选。将外部阴影 (outset) 改为内部阴影。

##### 边距

- `clear` : 禁止浮动元素
- ``

## 伪类

伪类用于定义元素的特殊状态。

例如，它可以用于：

- 设置鼠标悬停在元素上时的样式
- 为已访问和未访问链接设置不同的样式
- 设置元素获得焦点时的样式

伪类的使用规则如下：`[类名]:[伪类]`
伪类常用的有以下几个

$\small\color{DarkBlue}{\boldsymbol{link}}$

定义标签中链接的样式

```CSS
/* CSS代码 */
a:link {
  color: red;
}
```

```html
<!-- html代码 -->
<p><a href="/index.html" target="_blank">这是一个链接</a></p>
```

$\small\color{DarkBlue}{\boldsymbol{visited}}$

定义链接被访问后的样式

```CSS
/* CSS 代码*/
a:visited {
  color: green;
}
```

```html
<!-- html代码 -->
<p><a href="/index.html" target="_blank">这是一个链接</a></p>
```

$\small\color{DarkBlue}{\boldsymbol{hover}}$

定义鼠标悬停在标签上时的样式

```CSS
/* CSS 代码 */
a:hover {
  color: hotpink;
}
```

```html
<!-- html代码 -->
<p><a href="/index.html" target="_blank">这是一个链接</a></p>
```

$\small\color{DarkBlue}{\boldsymbol{active}}$

定义标签被点击后的样式(鼠标按下了，但是还没有松开)

```CSS
/* CSS 代码 */
a:active {
  color: blue;
}
```

```html
<!-- html代码 -->
<p><a href="/index.html" target="_blank">这是一个链接</a></p>
```

## 伪元素（未完成）

## 动画

- `transition-delay` : 属性规定过渡效果何时开始。量化参数。
- `transition-duration` : 属性规定完成过渡效果需要花费的时间（以秒或毫秒计）。量化参数。
- `transition-property` : 属性规定应用过渡效果的 CSS 属性的名称。
- `transition-timing-function` :
  - `linear` : 规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
  - `ease` : 规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
  - `ease-in` : 规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
  - `ease-out` : 规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
  - `ease-in-out` : 规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
  - `cubic-bezier(n,n,n,n)` : 在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。

  ```CSS
  /* CSS代码 */
  div
  {
    width:100px;
    height:50px;
    background:red;
    color:white;
    font-weight:bold;
    transition:width 2s;
    -moz-transition:width 2s; /* Firefox 4 */
    -webkit-transition:width 2s; /* Safari and Chrome */
    -o-transition:width 2s; /* Opera */
  }

  #div1 {transition-timing-function: linear;}
  #div2 {transition-timing-function: ease;}
  #div3 {transition-timing-function: ease-in;}
  #div4 {transition-timing-function: ease-out;}
  #div5 {transition-timing-function: ease-in-out;}

  /* Firefox 4: */
  #div1 {-moz-transition-timing-function: linear;}
  #div2 {-moz-transition-timing-function: ease;}
  #div3 {-moz-transition-timing-function: ease-in;}
  #div4 {-moz-transition-timing-function: ease-out;}
  #div5 {-moz-transition-timing-function: ease-in-out;}

  /* Safari and Chrome: */
  #div1 {-webkit-transition-timing-function: linear;}
  #div2 {-webkit-transition-timing-function: ease;}
  #div3 {-webkit-transition-timing-function: ease-in;}
  #div4 {-webkit-transition-timing-function: ease-out;}
  #div5 {-webkit-transition-timing-function: ease-in-out;}

  /* Opera: */
  #div1 {-o-transition-timing-function: linear;}
  #div2 {-o-transition-timing-function: ease;}
  #div3 {-o-transition-timing-function: ease-in;}
  #div4 {-o-transition-timing-function: ease-out;}
  #div5 {-o-transition-timing-function: ease-in-out;}

  div:hover
  {
    width:300px;
  }
  ```

  ```html
  <!-- html代码 -->
  <div id="div1" style="top:100px">linear</div>
  <div id="div2" style="top:150px">ease</div>
  <div id="div3" style="top:200px">ease-in</div>
  <div id="div4" style="top:250px">ease-out</div>
  <div id="div5" style="top:300px">ease-in-out</div>
  ```

  - `transform` : 该属性可以定义元素的移动和旋转。

  - `translate(x,y)` : 定义 2D 转换，即沿 x,y 轴移动
  - `translate3d(x,y,z)` : 定义 3D 转换。
  - `scale(x,y)` : 定义 2D 缩放转换。
  - `scale3d(x,y,z)` : 定义 3D 缩放转换。
  - `rotate(angle)` : 定义 2D 旋转，在参数中规定角度。
  - `rotate3d(x,y,z,angle)` : 定义 3D 旋转。
  - `rotateX(angle)` : 定义沿着 X 轴的 3D 旋转。
  - `rotateY(angle)` : 定义沿着 Y 轴的 3D 旋转。
  - `rotateZ(angle)` : 定义沿着 Z 轴的 3D 旋转。

- `@keyframes` : 通过 @keyframes 规则，能够创建动画。
  > 代码规定的动画不需要触发器能够自主运行。
  语法规则：
  `@keyframes animationname {keyframes-selector {css-styles;}}`

  - `animationname` : 定义动画的名称。必选参数。
  - `keyframes-selector` : 动画时长的百分比。必选参数。
  - `css-styles` : 一个或多个合法的 CSS 样式属性。必选参数。

  ```CSS
  /* CSS代码 */
  div {
    width: 100px;
    height: 100px;
    background-color: red;
    animation-name: example;
    animation-duration: 4s;
  }

  @keyframes example {
    0%   {background-color: red;}
    25%  {background-color: yellow;}
    50%  {background-color: blue;}
    100% {background-color: green;}
  }
  ```

  ```html
  <!-- html代码 -->
  <div></div>
  ```

- `animation` ：动画播放属性，可以不带属性名使用以下几个属性的参数。
  -`animation-name`
  - `animation-duration`
  - `animation-timing-function`
  - `animation-delay`
  - `animation-iteration-count`
  - `animation-direction`

- `animation-name` : 指定动画名
- `animation-duration` : 指定动画完成时间。
- `animation-timing-function` : 规定动画的速度曲线。
  - `linear` : 动画从头到尾的速度是相同的。
  - `ease` : 默认。动画以低速开始，然后加快，在结束前变慢。
  - `ease-in` : 动画以低速开始。
  - `ease-out` : 动画以低速结束。
  - `ease-in-out` : 动画以低速开始，然后低速结束（加速然后再减速）
- `animation-delay` : 动画开始延迟时间。
- `animation-iteration-count` : 动画循环播放次数
  - 自定义字数。
  - `infinite` : 无限。

- `animation-direction` : 定义是否应该轮流反向播放动画。
    > 如果 animation-direction 值是 "alternate"，则动画会在奇数次数（1、3、5 等等）正常播放，而在偶数次数（2、4、6 等等）向后播放。
  - `normal` : 默认值。动画应该正常播放。
  - `alternate` : 动画应该轮流反向播放。

- `animation-timing-function` : 规定目标元素的样式。
  - `none` : 默认值。动画在执行前后不会对元素应用任何样式。
  - `forwards` : 元素将保留由最后一个关键帧设置的样式值（依赖 animation-direction 和 animation-iteration-count）。
  - `backwards` : 元素将获取由第一个关键帧设置的样式值（取决于 animation-direction），并在动画延迟期间保留该值。
  - `both` : - 动画会同时遵循向前和向后的规则，从而在两个方向上扩展动画属性。
- `animation` : 该属性可以不声明属性名直接使用以下几个属性的参数
  - `animation-name`
  - `animation-duration`
  - `animation-delay`
  - `animation-iteration-count`
  - `animation-direction`
  - `animation-timing-function`
  - `animation-fill-mode`

## 变量

$~~~~~$ var() 函数用于插入 CSS 变量的值。

$~~~~~$ CSS 变量可以访问 DOM，这意味着您可以创建具有局部或全局范围的变量，使用 JavaScript 来修改变量，以及基于媒体查询来修改变量。

语法如下：

```CSS
var(name, value)
```

- `name` : 必需。变量名（以两条破折号开头）。
- `value` : 可选。回退值（在未找到变量时使用）。

变量的使用非常简单，如下例子：

```CSS
/* CSS代码 */
:root {
  --blue: #6495ed;
  --white: #faf0e6; 
}

body {
  background-color: var(--blue);
}

h2 {
  border-bottom: 2px solid var(--blue);
}

.container {
  color: var(--blue);
  background-color: var(--white);
  padding: 15px;
}

button {
  background-color: var(--white);
  color: var(--blue);
  border: 1px solid var(--blue);
  padding: 5px;
}
```

```html
<!-- html代码 -->
<h1>使用 var() 函数</h1>

<div class="container">
  <h2>Welcome to Shanghai!</h2>
  <p>Shanghai is one of the four direct-administered municipalities of the People's Republic of China.</p>
  <p>Shanghai is one of the four direct-administered municipalities of the People's Republic of China.</p>
  <p>
    <button>Yes</button>
    <button>No</button>
  </p>
</div>
```

$~~~~~$ 要想让属性的内容变化，只需要设置一个触发器，点击修改属性就行了。
$~~~~~$ 但是这需要 JS 才能实现。

```CSS
/* CSS代码 */
:root {
  --blue: #1e90ff;
  --white: #ffffff; 
}

body {
  background-color: var(--blue);
}

h2 {
  border-bottom: 2px solid var(--blue);
}

.container {
  color: var(--blue);
  background-color: var(--white);
  padding: 15px;
}

.container button  {
  background-color: var(--white);
  color: var(--blue);
  border: 1px solid var(--blue);
  padding: 5px;
}
```

```JS
// JS 代码
// 获取根元素
var r = document.querySelector(':root');

// 创建获取变量值的函数
function myFunction_get() {
  // 获取根的样式（属性和值）
  var rs = getComputedStyle(r);
  // 弹出 --blue 变量的值
  alert("The value of --blue is: " + rs.getPropertyValue('--blue'));
}

// 创建设置变量值的函数
function myFunction_set() {
  // 把变量 --blue 的值设置为另一个值（在这里是 "lightblue"）
  r.style.setProperty('--blue', 'lightblue');
}
```

```html
<!-- html代码 -->
<h1>使用 JavaScript 获取和更改 CSS 变量</h1>

<div class="container">
  <h2>Welcome to Shanghai!</h2>
  <p>Shanghai is one of the four direct-administered municipalities of the People's Republic of China.</p>
  <p>Shanghai is one of the four direct-administered municipalities of the People's Republic of China.</p>
  <p>
    <button>Yes</button>
    <button>No</button>
  </p>
</div>
<br>

<button type="button" onclick="myFunction_get()">使用 JavaScript 来获取 CSS 变量</button>
<button type="button" onclick="myFunction_set()">使用 JavaScript 来更改 CSS 变量</button>
```

## Flexbox

$~~~~~$ 弹性框布局模块，可以更轻松地设计灵活的响应式布局结构，而无需使用浮动或定位。

$~~~~~$ 如果要使用弹性布局，则父元素必须将 display 属性设置为 flex ，弹性容器的直接子元素会自动成为弹性项目

```CSS
/* CSS代码 */
.flex-container {
  display: flex;
  background-color: DodgerBlue;
}

.flex-container > div {
  background-color: #f1f1f1;
  margin: 10px;
  padding: 20px;
  font-size: 30px;
}
```

```html
<!-- html代码 -->
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div>3</div>  
</div>
```

弹性布局有以下几个属性

- `flex-grow` : 属性规定在相同的容器中，项目相对于其余弹性项目的增长量。
  - `number` : 数字值，规定该项目相对于其余弹性项目的增长量。默认为 0。

- `flex-shrink` : 固定在相同的容器中，项目相对于其余弹性项目的收缩量。
  - `number` : 数字，规定项目相对于其余弹性项目的收缩量。默认值为 1。

    ```CSS
    /* CSS代码 */
    #main {
      width: 350px;
      height: 100px;
      border: 1px solid #c3c3c3;
      display: flex;
    }

    #main div {
      flex-grow: 1;
      flex-shrink: 3;
      flex-basis: 100px;
    }

    #main div:nth-of-type(2) {
      flex-shrink: 3;
    }
    ```

    ```html
    <!-- html代码 -->
    <div id="main">
        <div style="background-color:coral;"></div>
        <div style="background-color:lightblue;"></div>
        <div style="background-color:khaki;"></div>
        <div style="background-color:pink;"></div>
        <div style="background-color:lightgrey;"></div>
    </div>
    ```

- `flex-basis` : 规定弹性项目的初始长度。
  - `number` : 长度单位或百分百，规定弹性项目的初始长度。

  ```CSS
  /* CSS代码 */
  #main {
    width: 300px;
    height: 100px;
    border: 1px solid #c3c3c3;
    display: flex;
  }

  #main div {
    flex-grow: 0;
    flex-shrink: 0;
    flex-basis: 50px;
  }

  #main div:nth-of-type(2) {
    flex-basis: 100px;
  }
  ```

  ```html
  <!-- html代码 -->
  <div id="main">
    <div style="background-color:coral;">50px</div>
    <div style="background-color:lightblue;">100px</div>
    <div style="background-color:khaki;">50px</div>
    <div style="background-color:pink;">50px</div>
    <div style="background-color:lightgrey;">50px</div>
  </div>
  ```

- `flex` : 该属性可以不声明属性名直接使用以下几个属性。
  - `flex-grow`
  - `flex-shrink`
  - `flex-basis`

- `flex-direction` : 规定弹性项目的方向。
  - `row` : 默认值。作为一行，水平地显示弹性项目。
  - `row-reverse` : 等同行，但方向相反。
  - `column` : 作为列，垂直地显示弹性项目。
  - `column-reverse` : 等同列，但方向相反。

- `flex-wrap` : 规定弹性项目是否应换行。
  - `nowrap` : 默认值。规定弹性项目不会换行。
  - `wrap` : 规定弹性项目会在需要时换行。
  - `wrap-reverse` : 规定弹性项目会在需要时换行，以反方向。`

- `flex-flow` : 该属性可以不声明属性名直接使用以下几个属性
  - `flex-direction`
  - `flex-wrap`

- `justify-content` : 规定项目的位置，当项目不占用主轴上所有可用空间时。
  - `flex-start` : 默认值。项目位于容器的开头。
  - `flex-end` : 项目位于容器的结尾。
  - `center` : 项目位于容器中央。
  - `space-between` : 项目在行与行之间留有间隔。
  - `space-around` : 项目在行之前、行之间和行之后留有空间。

- `align-items` : 弹性容器内的项目指定默认对齐方式
  - `stretch` : 默认。项目被拉伸以适合容器。
  - `center` : 项目位于容器的中央。
  - `flex-start` : 项目位于容器的开头。
  - `flex-end` : 项目位于容器的末端。
  - `baseline` : 项目被定位到容器的基线。

- `align-content` : 属性修改 flex-wrap 属性的行为。它与 align-items 相似，但是它不对齐弹性项目，而是对齐弹性线。
  - `stretch` : 默认值。行拉伸以占据剩余空间。
  - `center` : 朝着弹性容器的中央对行打包。
  - `flex-start` : 朝着弹性容器的开头对行打包。
  - `flex-end` : 朝着弹性容器的结尾对行打包。
  - `space-between` : 行均匀分布在弹性容器中。
  - `space-around` : 行均匀分布在弹性容器中，两端各占一半。

- `order` : 设置弹性项目的顺序
  - `number` : 默认值为 0。规定弹性项目的顺序。

  ```CSS
  /* CSS 代码 */
  #main {
    width: 400px;
    height: 150px;
    border: 1px solid #c3c3c3;
    display: -webkit-flex; /* Safari */
    display: flex;
  }

  #main div {
    width: 70px;
    height: 70px;
  }

  div#myRedDIV   {order: 2;}
  div#myBlueDIV  {order: 4;}
  div#myGreenDIV {order: 3;}
  div#myPinkDIV  {order: 1;}
  ```

  ```html
  <!-- html代码 -->
  <div id="main">
    <div style="background-color:coral;" id="myRedDIV"></div>
    <div style="background-color:lightblue;" id="myBlueDIV"></div>
    <div style="background-color:lightgreen;" id="myGreenDIV"></div>
    <div style="background-color:pink;" id="myPinkDIV"></div>
  </div>
  ```

- `align-self` :  属性指定弹性容器内所选项目的对齐方式，将覆盖弹性容器的 align-items 属性。
  - `auto` : 默认。元素继承其父容器的 align-items 属性，如果没有父容器，则为 "stretch"。
  - `stretch` : 定位元素以适合容器。
  - `center` : 元素位于容器的中央。
  - `flex-start` : 元素位于容器的开头。
  - `flex-end` : 元素位于容器的末端。
  - `baseline` : 元素被定位到容器的基线。

  ```CSS
  /* CSS代码 */
  #main {
    width: 220px;
    height: 300px;
    border: 1px solid black;
    display: flex;
    align-items: flex-start;
  }

  #main div {
    flex: 1;
  }

  #myBlueDiv {
    align-self: center;
  }
  ```

  ```html
  <!-- html代码 -->
  <div id="main">
    <div style="background-color:coral;">红色</div>
    <div style="background-color:lightblue;" id="myBlueDiv">蓝色</div>  
    <div style="background-color:lightgreen;">有更多内容的绿色 div</div>
  </div>
  ```

## 设备适应方案

- `@media` : 规则在媒体查询中用于为不同的媒体类型/设备应用不同的样式。

  语法如下

  ```CSS
  @media not|only mediatype and ([媒体类型] and|or|not [媒体类型]) {
    CSS-Code;
  }
  ```

  - `not` ： 非

  - `only` ：可防止旧版浏览器应用指定的样式，这些浏览器不支持带媒体特性的媒体查询。它对现代浏览器没有影响。

  - `and`： 将媒体特性与媒体类型或其他媒体特性组合在一起。

  通过 `media` 关键字可以防止让不同的设备使用不同的 CSS 样式。

  ```html
  <link rel="stylesheet" media="screen and (min-width: 900px)" href="widescreen.css">
  <link rel="stylesheet" media="screen and (max-width: 600px)" href="smallscreen.css">
  ```

  媒体类型有以下几个

  - `all` : 默认。用于所有媒体类型设备。
  - `print` : 用于打印机。
  - `screen` : 用于计算机屏幕、平板电脑、智能手机等。
  - `speech` : 用于朗读页面的屏幕阅读器。

## web 响应式布局

$~~~~~$ 响应式布局用以确保页面在所有设备上都能有不错的表现，浏览器会根据页面上的设置调整不同设备的表现。

$\small\color{DarkBlue}{\boldsymbol{meta}}$

$~~~~~$ 该属性是响应式布局中非常重要的一个属性，该声明页面基础数据的方式能够让页面对不同设备做出反应，如下面的代码能够让页面自动适配设备大小。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

$~~~~~$ 当然，如果我们强制规定了内部元素的宽高，那么也会出现溢出屏幕的情况。因此，响应式布局需要注意以下几个规则：

1. 请勿使用较大的固定宽度元素
2. 不要让内容依赖于特定的视口宽度来呈现好的效果
3. 使用 CSS 媒体查询为小屏幕和大屏幕应用不同的样式

  > 即不同的设备使用不同的 CSS 样式。

$\small\color{DarkBlue}{\boldsymbol{网格视图}}$

$~~~~~$ 网格视图就是将网页分层一格一格的长条矩形，然后根据页面要求按矩形进行布局设置。
$~~~~~$ 网格视图通常将页面划分成 12 个矩形，当然如果定位要求更加精细，可以划分24个，要实现划分需要使用 CSS 变量，如下代码我们创建12个变量，指定 12个区间

```CSS
/* CSS代码 */
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}
```

然后所有属性高宽都基于这些变量进行使用

$\small\color{DarkBlue}{\boldsymbol{媒体查询}}$

媒体查询实际上就是查询使用设备的宽高，然后定义布局，媒体查询使用 `@media` 属性，如下代码，使用媒体查询，如果设备边框宽度等于或小于 600 ，则为浅蓝色，否则为绿色。

```CSS
/* CSS代码 */
body {
  background-color: lightgreen;
}

@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

```html
<!-- html代码 -->
<p>请调整浏览器窗口的大小。如果此文档的宽度为 600 像素或更小，背景颜色为“浅蓝色”，否则为“浅绿色”。</p>
```
