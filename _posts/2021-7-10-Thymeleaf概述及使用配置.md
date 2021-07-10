---
layout:     post
title:      thymeleaf
subtitle:   这里记录每天的心情与收获，有时间就写写。
date:       1994-10-03
author:     zouhu
header-img: img/post-bg-article.jpg
catalog: true
tags:
    - 阿里云
    - thymeleaf
---

# Thymeleaf概述

  &emsp;&emsp; Thymeleaf是一个供后端人员使用的，为快速开发页面而生的Java模板引擎，能够动态地替换掉静态内容，使页面动态显示，。Thymeleaf的主要目标是为您的开发工作流程带来优雅的自然模板 - 可以正确显示在浏览器中的HTML，也可以作为静态原型工作，从而在开发团队中进行更强大的协作。 

&emsp;&emsp; 开发传统Java WEB工程时，我们可以使用JSP页面模板语言，但是在SpringBoot中已经不推荐使用了。

&emsp;&emsp;SpringBoot支持如下页面模板语言

```
Thymeleaf
FreeMarker
Velocity
Groovy
JSP
```

&emsp;&emsp;其中Thymeleaf是SpringBoot官方所推荐使用的，Thymeleaf是动静分离的，页面中的动态标签是需要传递有数据的时候才会渲染，不然就是原本默认的静态的样子。（Thymeleaf就是jsp的高端升级版。）

## 一、为什么使用模板引擎

- **Thymeleaf 在有网络和无网络的环境下皆可运行**，即它可以让美工在浏览器查看页面的静态效果，也可以让程序员在服务器查看带数据的动态页面效果。这是由于它支持 html 原型，然后在 html 标签里增加额外的属性来达到模板+数据的展示方式。浏览器解释 html 时会忽略未定义的标签属性，所以 thymeleaf 的模板可以静态地运行；当有数据返回到页面时，Thymeleaf 标签会动态地替换掉静态内容，使页面动态显示。
- Thymeleaf **开箱即用**的特性。它提供标准和spring标准两种方言，可以直接套用模板实现JSTL、 OGNL表达式效果，避免每天套模板、该jstl、改标签的困扰。同时开发人员也可以扩展和创建自定义的方言。
- Thymeleaf 提供spring标准方言和一个与 SpringMVC 完美集成的可选模块，可以快速的实现表单绑定、属性编辑器、国际化等功能。

## 二、使用Thymealeaf

（1）**引入依赖**

在pom.xml文件中加入以下依赖即可

```xml
<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

无需指定版本号，spring-boot-dependencies.pom中已指定

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070220213388.png)


（2）**在模板文件中加入解析**

&emsp;&emsp;在加入依赖后，还需要在HTML引用命名空间

```html
<html xmlns:th="http://www.thymeleaf.org">
```

&emsp;&emsp;以下代码是一个简单的thymeleaf模板文件，其作用是显示数据库（实体）中的文章标题和内容。

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title th:text="${article.title}">标题</title>
</head>
<body>
    <div th:text="${article.title}">标题</div>
    <div th:text="${article.body}">内容</div>
</body>
</html>
```

（3）**配置视图解析器**

&emsp;&emsp;在application.properties文件中，可以配置Thymealeaf模板解析器的属性

```xml
#为便于测试，在开发时需要关闭缓存
spring.thymeleaf.cache=false
```