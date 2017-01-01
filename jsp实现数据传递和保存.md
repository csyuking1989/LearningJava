### 要实现的功能

1. 实现用户登录功能
2. 保存用户状态
3. 登录时自动填写用户名
4. 登记页面访问次数 

**第1步，登录页面的html代码, 保存在userCreate.jsp： **

```
<%--
  Created by IntelliJ IDEA.
  User: chenshenyu
  Date: 12/9/16
  Time: 8:39 PM
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<form id="dataForm" name="dataForm" action="doUserCreate.jsp" method="post">
<table class="tb" border="0" cellspacing="5" cellpadding="0" align="center">
    <tr>
        <td align="center" colspan="2" style="text-align: center;"></td>
    </tr>
    <tr>
        <td class="text_tabledetail2">用户名</td>
        <td><input type="text" name="username" value=""></td>
    </tr>
    <tr>
        <td class="text_tabledetail2">密码</td>
        <td><input type="password" name="password" value=""></td>
    </tr>
    <tr>
        <td class="text_tabledetail2">确认密码</td>
        <td><input type="password" name="con_password" value=""></td>
    </tr>
    <tr>
        <td class="text_tabledetail2"> 邮箱</td>
        <td><input type="text" name="email" value=""></td>
    </tr>
    <tr>
        <td style="text-align: center;" colspan="2">
            <button type="submit" class="page-btn" name="save">注册</button>
            <button type="button" class="page-btn" name="return" onclick="">提交</button>
        </td>
    </tr>
</table>
  </form>
</body>
</html>
```

**第2步, 获取登录信息的代码,保存在doUserCreate.jsp：**

```
<%   
   String userName = request.getParameter("username");
   String password = request.getParameter("password"); 
   String email = request.getParameter("email"); 
   out.println("username:"+userName+"<br/>");
   out.println("password:"+password+"<br/>"); 
   out.println("email:"+email+"<br/>")
%>
```

然后在步骤1中，填完注册信息，就会跳到步骤2中的页面，自动显示刚才填入的注册信息。

注解：步骤1中method的方法有两种，get和post，区别是 页面跳转后，get后面有参数，安全性低，post后面无参数，安全性相对较高。

** 第三步，判断用户名是否为admin，如果是admin，那么提示用户名不符，并且跳转到原注册页面；如果非admin，则跳转到index.jsp页面 :  **

将以下代码插入到doUserCreate.jsp中：

```
if(userName.equals("admin"){ 
    //  提示用户不存在，不能注册  
    request.setAttribute("message","用户名admin已存在，不能注册!")
    request.getRequestDispatcher("userCreate.jsp").forword(request,response); // 转发
 } else{
    // 提示注册成功 ,同时提示成功 
    request.setAttribute("message","注册成功");
    response.sendRedirect("index.jsp"); // 重定向
}
```

为了在原注册页面，即userCreate.jsp中得到注册不成功的提示信息，需要加入在userCreate.jsp中加入如下代码： 

```
<%  
Object mess = request.getAttribute("message");
if(mess!=null){
    out.println(mess.toString());
}
%>
```

为了在index.jsp中，提示注册成功的信息，需要在index.jsp中加入如下代码 

```
<% 
Object mess = request.getAttribute("message");
if(mess!=null){
    out.println(mess.toString());
}
%>
```

第四部，在请求中保存属性



















