# JavaScript 笔记

[TOC]

## 基本内容

### var

javascript 用 var 创建变量，这个变量可以储存值，集合，数组，方法

如：

```html
<body>
<p id="demo"></p>
</body>

<script>
// 创建对象：
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id     : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
// 显示来自对象的数据：
document.getElementById("demo").innerHTML = person.fullName();
</script>
```

使用 var 的值，也需要在 `<script></script>` 标签中用方法把值放到页面中或者提到到后端，此处用了 innerHTML 把值赋给了页面上的 `<p id="demo"></p>` 标签

不带 var 也行，语法没问题就行,但是最好有 var ，保证语法规范

```js
person = {
  firstName: "Bill",
  lastName : "Gates",
  id     : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
```

在创建多个对象时，可以只写一个 `var` ，然后不同的变量用,隔开，如 ：

```js
var a=0,b="hello world"，c='c';
//这样等同于
var a=0;
var b="hello world";
var c="c";
```

字符需要用 `' '` 声明，不然会被系统识别为对象。
字符串要用 `" "` 声明，不然也一样。

### if

#### 基本语法

基本语法与 c，java 一样：

```js
if(判断条件)
{
    为真执行内容
}else
{
    为假执行内容
}
```

### for

#### 基本语法 for(i=0;i<a;i++)

javascript 的 for 循环与 c 和 java 的语法一样，定义一个 i ，设置 i 的最大值或者最小值，然后每次循环，加或者减多少 。
所以 for 循环会设置三个属性 ： `for(1.设置初始值;2.设置极限值;3.设置循环后的初始值变化)` 。

```js
cars=["BMW","Volvo","Saab","Ford"];
for (var i=0;i<cars.length;i++){
 document.write(cars[i] + "<br>");
}
```

此处循环是初始化的加载内容，循环没有结束，页面就不能算加载完成，所以 `document.write` 没有覆盖。

for 循环不要求全部属性在循环条件内，如已定义了i值，那么第一个属性就可以不用填，但是 `;` 不能省，如 ：

```js
var i=2,len=cars.length;
for (; i<len; i++)
{ 
    document.write(cars[i] + "<br>");
}
```

如果在循环内部设置了 i 自增的话，第三个属性就能省 ：

```js
var len=cars.length;
for (i=0; i<len; )
{ 
    document.write(cars[i] + "<br>");
    i++;
}
```

#### for-in

for-in 的循环表达式为：`for(a in b)` ，意思是每次循环是，把 b 的值赋给 a ，此时若 b 没有了数据，就停止循环。

所以 `for-in` 被称作遍历循环，遍历 b 赋值给 a 。

```js
var x;
var txt="";
var person={fname:"Bill",lname:"Gates",age:56};
for (x in person){
  txt=txt + person[x];
}
```

### function

#### 方法介绍

JavaScript 函数 ( `function` ) 是被设计为执行特定任务的代码块, JavaScript 函数会在某代码调用它时被执行,我喜欢将其称为工具方法，**所以后面我可能会用方法来代表这个参数**，代码的格式为：

```js
    function name(变量){
        方法内容
    }
```

name 指定方法名，便于方法调用，参数为传入数据使用。

#### 方法使用

注意:

- `function` 无法改变 `var` 定义的参数，但是可以使用这些参数。

- `function` 方法体中定义的变量、对象、参数、方法都只会在这个方法中使用，无法被外界调用，方法结束参数随销毁。但是可以在方法中对页面元素进行修改
  
通过这个例子就能看出：

```html
<body>
    <p id="test1"></p>
    <p id="test2"></p>
    <p id="test3"></p>
</body>

<script>
    var a=1;
    function name(){
        a = 2 ;
        var aa=2;
        document.getElementById("test3").innerHTML = a;
    }
    document.getElementById("test1").innerHTML = a;
    document.getElementById("test2").innerHTML = a;
</script>
```

你会发现a的值还是 1 而不是 2 ，因为 `function` 无法改变任何数据的值，`<p id="test2"></p>` 是空的，没有数据 `<p id="test3"></p>` 也还是1 。

**但是 `function` 可以做到的事也很多，如：**

当成一个计算方法：

```html
<body>
    <!--通过button标签的onclick方法设置 function 的触发机制 -->
    <input type="number" id="a"><br>
    <input type="number" id="b"><br>
    <button id="aaa">点击此处</button>
    <p id="test01"></p>
</body>

<script>
    //注意，设置 onclick 相应事件建议document.getElementById("name").onclick=
    //这样设置不容易出错，直接在button标签中设置 onclick=  很容易出错
    document.getElementById("aaa").onclick = function () {
        var aa=document.getElementById("a").value; //获取input的值
        var bb=document.getElementById("b").value;
        document.getElementById("test01").innerHTML=name(parseInt(aa),parseInt(bb));
    }//parseInt 转换为int类型，因为哪怕设置了 input type="number"  但获取的value仍然是算字符串
    function name(a, b) {
        return a + b;
    }
</script>   
```

也可以替换掉列表，添加图片，设置方法使用的触发等许多的设置，在下面的例子中将体现出这些作用：

```html
 <body>
<button id="btn1">insert1</button>
<ul id="list">
 <li><img src="images/1.jpg"></li>
 <li><img src="images/2.jpg"></li>
 <li><img src="images/3.jpg"></li>
</ul>
</body>

<script>
var oList=document.getElementById('list');

 document.getElementById('btn1').onclick=function(){x
   //创建li和img
   //Document.createElement() 方法用于创建一个由标签名称 tagName 指定的 HTML 元素。
   //如果用户代理无法识别 tagName，则会生成一个未知 HTML 元素 HTMLUnknownElement。
   var oLi=document.createElement('li');
   var oImg=document.createElement('img');
   //设置oImg的图片路径为'images/4.jpg'
   oImg.src='images/4.jpg';
   //将img插入li中
   //appendChild() 方法向节点添加最后一个子节点。
   oLi.appendChild(oImg);
   //将li插入到ul中
   oList.appendChild(oLi);
 };
 // Document.createElement 创建标签对象，然后通过对象名称对对象的值进行修改
 // appendChild 把 oImg 添加到列表的后面
</script>
```

### input

input 是一个很有意思的标签，可以通过设置 `type` 把它转换为很多种标签，但是最主要的还是它的键入数据标签，通常情况下我们设置 `type` 为 text 来键入字符串，为 number 来键入数字。

```html
<input type="number" id="a">
<input type="text" id="a">
```

但是光这样没用啊，数据确实收到了，咋用？
我们将通过 js 对数据进行处理，这是一个获取 `input` 的数据然后计算并返回计算结果到页面的html程序。

```html
<body>
    <!--通过 button 标签的 onclick 方法设置 function 的触发机制 -->
    <input type="number" id="a"><br>
    <input type="number" id="b"><br>
    <button id="aaa">点击此处</button>
    <p id="test01"></p>
</body>

<script>
    function name(a, b) {
        return a + b;
    }

    document.getElementById("aaa").onclick = function () {
        var aa=document.getElementById("a").value; //获取input的值
        var bb=document.getElementById("b").value;
        document.getElementById("test01").innerHTML=name(parseInt(aa),parseInt(bb));
    }//parseInt 转换为 int 类型，因为哪怕设置了 input type="number"  但获取的 value 仍然是算字符串
</script>
```

`aa=document.getElementById("a").value` : 指定标签id ，获取标签属性（即获取标签类容），这是获取 input 键入的数据的方法。

### 输出

JavaScript 能够以不同方式“显示”数据：

- 使用 window.alert()
- 使用 document.write() 写入 HTML 输出
- 使用 innerHTML 写入 HTML 元素
- 使用 console.log() 写入浏览器控制台

#### window.alert()

`alert()` 本来就能发弹窗，`window.alert()` 应该是用了window属性，保证代码在哪都能发弹窗

#### innerHTML

innerHTML 无法直接去使用，需要一个与页面元素的媒介，如使用 `document.getElementById(id)` 方法。
`id` 属性定义 HTML 元素。`innerHTML` 属性定义 HTML 内容

**例子：**

```html
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = 5 + 6;
</script>

</body>
</html>
```

通过获取元素 id 名，然后用 innerHTML 对元素值进行修改，但是这个元素得是 html 页面元素，毕竟这个属性就是改这个的。

#### document.write()

`document.write()` ,可以直接放在页面上，放在哪就在哪显示

**例子：**

```html
<!DOCTYPE html>
<html>
<body>

<h2>hello world</h2>

<script>
document.write(5 + 6);
</script>

</body>
</html>
```

**注意**    ：在 HTML 文档完全加载后使用 `document.write()` 将删除所有已有的 HTML ，所以 `document.write()` 别和 `onclick` 之类的后触发元素使用。

例子：

```html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript 能做什么</h2>
<p id="demo">JavaScript 能够改变 HTML 内容。</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Hello JavaScript!"'>点击我！</button>

</body>
</html>
```

**提示** : document.write() 方法仅用于测试。

#### console.log()

在 console 中输出日志，控制台中可以点击 console 看到输出,作用自然是日志输出。

```html
<!DOCTYPE html>
<html>
<body>

<h2>按 F12 启动</h2>

<p>在 debugger 中选择 "Console"。然后再次点击运行按钮。</p>

<script>
console.log(5 + 6);
</script>

</body>
</html>
```

## Document

每个载入浏览器的 HTML 文档都会成为 Document 对象。
Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。
**提示** ：Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。

#### Document对象集合

|   集合   |              描述                 |
| :------: | :-------------------------------: |
| `all[]` | 提供对文档中所有 HTML 元素的访问。|
| `anchors[]` | 返回对文档中所有 Anchor 对象的引用0。 |
| `applets` |返回对文档中所有 Applet 对象的引用。|
| `forms[]` | 返回对文档中所有 Form 对象引用。 |
| `images[]` | 返回对文档中所有 Image 对象引用。|
| `links[]` | 返回对文档中所有 Area 和 Link 对象引用。 |

#### Document 对象属性

|   属性   |               描述                 |
| :------: |   :---------------------------:    |
| `body` |提供对 `<body>` 元素的直接访问,对于定义了框架集的文档，该属性引用最外层的 `<frameset>`。|
| `cookie` | 设置或返回与当前文档有关的所有 `cookie`。 |
| `domain` | 返回当前文档的域名。 |
| `lastModified` | 返回文档被最后修改的日期和时间。 |
| `referrer` | 返回载入当前文档的文档的 URL。 |
| `title` | 返回当前文档的标题。 |
| `URL` | 返回当前文档的 URL。 |

#### Document 对象方法

| 方法 | 描述 |
| :---: |   :----:   |
| `close()` | 关闭用 `document.open()` 方法打开的输出流，并显示选定的数据。 |
| `getElementById()` | 返回对拥有指定 id 的第一个对象的引用。 |
| `getElementsByName()` | 返回带有指定名称的对象集合。|
| `getElementsByTagName()` | 返回带有指定标签名的对象集合。 |
| `open()` | 打开一个流，以收集来自任何 `document.write()` 或 `document.writeln()` 方法的输出。|
| `write()` | 向文档写 HTML 表达式 或 JavaScript 代码。 |
| `writeln()` | 等同于 write() 方法，不同的是在每个表达式之后写一个换行符。|
