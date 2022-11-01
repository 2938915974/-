# JQuery 笔记

## ajax请求

AJAX 是与服务器交换数据的技术，它在不重载全部页面的情况下，实现了对部分网页的更新。

### ajax发送请求

ajax的请求包含以下几个参数，有些参数不是必要的

```jq
$.ajax({
   url： '[URL 接口地址]'
   type：'[请求⽅式,如post，get]'
   contentType: 'application/[传输格式,如json，txt]',
   data: [传输的数据，什么传输格式就用什么写法],
   dataType: '[返回的数据格式，如json，txt]',
   success: 返回成功后的操作
   error: 返回失败后的操作
});
```

下面是一个使用例子

```jq
function abc(){
    $.ajax({
        url: 'http://localhost:30000/demo/get',
        type: 'POST',
        contentType: 'application/json',
        data: JSON.stringify({
            name: "zhangsan",
            age: 18
        }),
        success: function (resp) {    //请求传递回来的数据会自动赋值到这个resp对象中
            console.log('---> success resp data: ' + JSON.stringify(resp));
        },
        error: function (resp) {
            console.log('---> error resp data: ' + JSON.stringify(resp));
        }
    })
}
```

- 因为`$.ajax{}`不会直接运行，要想运行就需要把代码放在方法中，以启动方法来启动ajax请求，启动function见[function参数说明](../../入门参数/function.md)。

- **`JSON.stringify()`** ： 有时候，明明已经指定了json格式传输，但是就是转换时有问题，这时候就要用`JSON.stringify()`这个方法，把 JavaScript 对象或值转换为 JSON 字符串。
