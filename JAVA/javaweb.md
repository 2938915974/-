# jsp 考试应对

在jsp 中通过 `<% %>` 来嵌入 java 代码。

```jsp
<%
out.println("Your IP address is " + request.getRemoteAddr());
%>
```

jsp 通过 `<jsp:scriptlet>` 来嵌入 xml 代码。

```jsp
<jsp:scriptlet>
   代码片段
</jsp:scriptlet>
```

jsp 通过 `<%@ %>` 来指定头部标签。

```java
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

jsp 通过 `<%-- 注释 --%>` 来设置注释。

`<%@ page ... %>` : 定义网页依赖属性，比如脚本语言、error页面、缓存需求等等
`<%@ include ... %>` : 包含其他文件
`<%@ taglib ... %>` : 引入标签库的定义

## servlet

servlet 大部分数据都是在  web.xml 中进行配置。

### 后端方法访问

servlet 要想实现就 jsp 访问后端，需要先将类进行 web 接口注册，注册方式有两个

1. xml

    ```xml
    ```

2. 注解

   ```java
   @WebServlet(name = String ,urlPatterns = String[])
   ```

请求进入后台时，会调用 `init()` 方法
每次请求时，会调用 `service()` 方法
当服务器关闭时，会调用 `destory()` 方法
