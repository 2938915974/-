# 网页样式与JS模块记录(用于复制粘贴)

[TOC]

## 样式

### 下拉菜单

```CSS
/* CSS代码 */
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a, .dropbtn {
  display: inline-block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover, .dropdown:hover .dropbtn {
  background-color: red;
}

li.dropdown {
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  text-align: left;
}

.dropdown-content a:hover {background-color: #f1f1f1;}

.dropdown:hover .dropdown-content {
  display: block;
}
```

```html
<!-- html代码 -->
<ul>
  <li><a href="#home">Home</a></li>
  <li><a href="#news">News</a></li>
  <li class="dropdown">
    <a href="#" class="dropbtn">Dropdown</a>
    <div class="dropdown-content">
      <a href="#">Link 1</a>
      <a href="#">Link 2</a>
      <a href="#">Link 3</a>
    </div>
  </li>
</ul>
```

### 一张图片多个标签使用（整合图像）

```CSS
/* CSS代码 */
#home {
  width: 46px;
  height: 44px;
  background: url(/i/css/navsprites.gif) 0 0;
}

#next {
  width: 43px;
  height: 44px;
  background: url(/i/css/navsprites.gif) -91px 0;
}
```

```html
<!-- html代码 -->
<img id="home" src="/i/css/trans.gif" width="1" height="1">
<img id="next" src="/i/css/trans.gif" width="1" height="1">
```

### 工具提示窗口

该代码可以在鼠标指向标签时于标签上方生成一个提示窗口。

```CSS
/* CSS代码 */
.tooltip {
  position: relative;
  display: inline-block;
  border-bottom: 1px dotted black;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 120px;
  background-color: black;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 5px 0;
  position: absolute;
  z-index: 1;
  bottom: 150%;
  left: 50%;
  margin-left: -60px;
}

.tooltip .tooltiptext::after {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: black transparent transparent transparent;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
}
```

```html
<!-- html代码 -->
<div class="tooltip">Hover over me
  <span class="tooltiptext">Tooltip text</span>
</div>
```

### 分页标签

该内容用于创建一个分页的页码组标签

```CSS
/* CSS代码 */
.pagination {
  display: inline-block;
}

.pagination a {
  color: black;
  float: left;
  padding: 8px 16px;
  text-decoration: none;
  border: 1px solid #ddd;
}

.pagination a.active {
  background-color: #4CAF50;
  color: white;
  border: 1px solid #4CAF50;
}

.pagination a:hover:not(.active) {background-color: #ddd;}

.pagination a:first-child {
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}

.pagination a:last-child {
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
```

```html
<!-- html代码 -->
<div class="pagination">
  <a href="#">«</a>
  <a href="#">1</a>
  <a class="active" href="#">2</a>
  <a href="#">3</a>
  <a href="#">4</a>
  <a href="#">5</a>
  <a href="#">6</a>
  <a href="#">»</a>
</div>
```

## JS
