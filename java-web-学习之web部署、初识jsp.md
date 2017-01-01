### 目标

1. 掌握在idea中部署tomcat  \(先略过，以后有时间再写，网上教程很多\)
2. 初步认识jsp，会一些基本简单的操作  

> _JSP定义：运行在服务器端的Java页面，使用HTML嵌套Java代码实现 , Java代码用&lt;%  %&gt;包起来。   _

在JSP页面中实现换行输出内容：

```
<%
    out.println("this is test<br>"); // 这里要用<br> 而不能用\n 
    out.println("this is a test2");
%>
```

另外一个例子，结果会输出 a的内容 ：

```
<%   
    String a = "Hello World"; 
%> 

<%=a %>  
<% i =10 %>   <%! j=10 %> // 前者是局部变量 后者是全局变量
```



