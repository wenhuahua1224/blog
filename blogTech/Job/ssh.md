## Struts2

> Struts是流行和成熟的基于MVC设计模式的Web应用程序框架。

## Struts2工作原理

1. *设计目标*

    Struts设计的第一目标就是使MVC模式应用于web程序设计。在这儿MVC模式的好处就不在提了。
2. 技术优势
    Struts2有两方面的技术优势，一是所有的Struts2应用程序都是基于client/server HTTP交换协议，The Java Servlet API揭示了Java Servlet只是Java API的一个很小子集，这样我们可以在业务逻辑部分使用功能强大的Java语言进行程序设计。
    二是提供了对MVC的一个清晰的实现，这一实现包含了很多参与对所以请求进行处理的关键组件，如：拦截器、OGNL表达式语言、堆栈。

    因为struts2有这样目标，并且有这样的优势，所以，这是我们学习struts2的理由，下面，我们在深入剖析一下struts的工作原理。
工作原理
    Suruts2的工作原理可以用下面这张图来描述

![如图所示][struts2-fw-01]



## Struts2工作流程
在struts2的应用中，从用户请求到服务器返回相应响应给用户端的过程中，包含了许多组件，他们是怎么在一起工作的：

 ![如图所示][struts2-fw-02]

1. 客户端（Client）向Action发用一个请求（Request）
2. Container通过web.xml映射请求，并获得控制器（Controller）的名字
3. 容器（Container）调用控制器（StrutsPrepareAndExecuteFilter或FilterDispatcher）。在Struts2.1以前调用FilterDispatcher，Struts2.1以后调用StrutsPrepareAndExecuteFilter
4. 控制器（Controller）通过ActionMapper获得Action的信息
5. 控制器（Controller）调用ActionProxy
6. ActionProxy读取struts.xml文件获取action和interceptor stack的信息。
7. ActionProxy把request请求传递给ActionInvocation
8. ActionInvocation依次调用action和interceptor
9. 根据action的配置信息，产生result
10. Result信息返回给ActionInvocation
11. 产生一个HttpServletResponse响应
12. 产生的响应行为发送给客服端。

























[struts2-fw-01]:./img/struts2-fw-01.png "struts2工作流程01"
[struts2-fw-02]:./img/struts2-fw-02.png "struts2工作流程02"