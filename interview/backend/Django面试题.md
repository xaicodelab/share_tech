# Django面试题

* 1、Django的生命周期是什么？

```text
当用户在浏览器输入url时，浏览器会生成请求头和请求体发送给服务端，url经过Django中的wsgi时请求对象创建完成，
经过Django的中间件，然后到路由系统匹配路由，匹配成功后走到相对应的views函数，视图函数执行相关的逻辑代码返回执行结果，
Django把客户端想要的数据作为一个字符串返回给客户端，客户端接收数据，渲染到页面展现给用户。
详细：
uWSGI服务器通过wsgi协议，将HttpRequest交给web框架 （Flask、Django）
首先到达request中间件，对请求对象进行校验或添加数据，例如：csrf、request.session，如果验证不通过直接跳转到response中间件
通过URL配置文件找到urls.py文件
根据浏览器发送的URL，通过视图中间件去匹配不同的视图函数或视图类，如果没有找到相对应的视图函数，就直接跳转到response中间件
在视图函数或视图类中进行业务逻辑处理，处理完返回到response中间件
模型类通过ORM获取数据库数据，并返回序列化json或渲染好的Template到response中间件
所有最后离开的响应都会到达response中间件，对响应的数据进行处理，返回HttpResponse给wsgi
wsgi经过uWSGI服务器，将响应的内容发送给浏览器。
```

* 2、Django的MTV模式是什么？
```text
MTV：Model(模型)：负责业务对象与数据库的对象(ORM)
Template(模版)：负责如何把页面展示给用户
View(视图)：负责业务逻辑，并在适当的时候调用Model和Template
```

* 3、什么是wsgi，uwsgi，uWSGI？
```text
uwsgi：是uWSGI服务器实现的独有协议，用于Nginx服务与uWSGI服务的通信规范
uWSGI：是一个Web服务器，它实现了WSGI/uwsgi/HTTP等协议，用于接收Nginx转发的动态请求，处理后发个python应用程序
WSGI：用在python web框架（Django/Flask）编写的应用程序与web服务器之间的规范
```

* 4、Django的中间件是什么并简述其作用？
```text
中间件是一个用来处理Django请求和响应的框架级钩子。
它是一个轻量、低级别的插件系统，用于在全局范围内改变Django的输入和输出。
每个中间件组件都负责做一些特定的功能。
```

* 5、Django中提供了runserver为什么不能用来部署项目(runserver与uWSGI的区别)
```text
（1）runserver方法是调试 Django 时经常用到的运行方式，它使用Django自带的
WSGI Server 运行，主要在测试和开发中使用，并且 runserver 开启的方式也是单进程 。
（2）uWSGI是一个Web服务器，它实现了WSGI协议、uwsgi、http 等协议。注意uwsgi是一种通信协议，而uWSGI是实现uwsgi协议和WSGI协议的 Web 服务器。
uWSGI具有超快的性能、低内存占用和多app管理等优点，并且搭配着Nginx就是一个生产环境了，能够将用户访问请求与应用 app 隔离开，实现真正的署。
相比来讲，支持的并发量更高，方便管理多进程，发挥多核的优势，提升性能。
```

* 6、Django中如何实现websocket？
```text
简述：Django实现websocket，之前django-websocket退出到3.0之后，被废弃。官方推荐使用channels。
配置：需要在seting.py里配置，将我们的channels加入INSTALLED_APP里。
```

* 7、model继承有几种方式，分别是什么？
```text
抽象基类（Abstract base classes）
多表继承抽象基类（Abstract base classes）
Meta inheritance  当一个子类没有声明自己的Meta类时，它会继承基类的 Meta 类，如果子类想扩展基类的 Meta 类 ，它可以继承基类的Meta类，然后再进行扩展。
```

* 8、class Meta中的原信息字段有哪些？
```text
（1）app_label 应用场景：模型类不在默认的应用程序包下的models.py文件中，这时候你需要指定你这个模型类是那个应用程序的
（2）db_table 应用场景：用于指定自定义数据库表名的
（3）db_tablespace 应用场景：通过db_tablespace来指定这个模型对应的数据库表放在哪个数据库表空间
（4）verbose_name 应用场景：给你的模型类起一个更可读的名字
（5）verbose_name_plural 应用场景： 模型的复数形式是什么
（6）ordering 应用场景：象返回的记录结果集是按照哪个字段排序的
```

* 9、对Django的认知？
```text
（1）Django是走大而全的方向，它最出名的是其全自动化的管理后台：只需要使用起ORM，做简单的对象定义，它就能自动生成数据库结构、以及全功能的管理后台。
（2）Django内置的ORM跟框架内的其他模块耦合程度高。
应用程序必须使用Django内置的ORM，否则就不能享受到框架内提供的种种基于其ORM的便利。
理论上可以切换掉其ORM模块，但这就相当于要把装修完毕的房子拆除重新装修，倒不如一开始就去毛胚房做全新的装修。
（3）Django的卖点是超高的开发效率，其性能扩展有限；采用Django的项目，在流量达到一定规模后，都需要对其进行重构，才能满足性能的要求。
（4）Django适用的是中小型的网站，或者是作为大型网站快速实现产品雏形的工具。
（5）Django模板的设计哲学是彻底的将代码、样式分离； Django从根本上杜绝在模板中进行编码、处理数据的可能。
```

* 10、Django ORM 中如何设置读写分离？
```text
手动读写分离：通过 .using(db_name) 来指定要使用的数据库
自动读写分离：
　　（1）定义类：如 Router #
　　（2）配置 Router：在 settings.py 中指定 DATABASE_ROUTERS
　　　　DATABASE_ROUTERS = ['myrouter.Router',]
```
