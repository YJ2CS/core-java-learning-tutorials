---
title: Java学习路线
url: 0-1-java学习路线
author: YJ2CS
avatar: /custom/avatar.webp
authorLink: YJ2CS.github.io
authorAbout: 愿青年摆脱了冷气，只是向前走！
authorDesc: 愿青年摆脱了冷气，只是向前走！
comments: true
categories:
  - learn-java
tags:
  - 悦读
no-photos: 'https://random.52ecy.cn/randbg.php?size=1&rid-e7d1'
date: 2020-11-10T22:16:00.000Z
date updated: '2020-12-26T20:06:31+08:00'

---

## Java学习路线图

该路线图在保留了文章的核心架构外，也做了一些优化，包括：

1. 更详细的学习内容。
2. 更精确的学习时间。
3. 优化学习方法，避开前端知识。
4. 及时引入Jar包管理（Maven）。

下面是具体的 “Java学习路线图”：

![images/java学习路线图-images/fabc8942.png](images/fabc8942.png)

在图中，我把Java学习分成3个阶段：

```text
1. 基础知识
2. Spring
3. 应用服务
```

阶段划分的原则是“由浅入深”，利于读者层层递进的学习。
内容选编的原则是 “有用”，有利于读者理解Java原理，对实际工作有用。
下面是各个阶段的简要介绍。

## 基础知识

学习Java基础知识，可供选择的书很多，但它们大都有着一个缺点，那就是内容庞杂，有些内容脱离实际，甚至是过时。
对此，在这一阶段，我精选了Java的基础知识，核心原则就是“有用”。并调整了章节顺序，从而有利于读者循序渐进的学习。
具体的学习过程中，我建议先阅读《Java核心技术 卷I》，然后辅于上网搜索，之后要将书中所附的代码大都调通理解。

- 这里初学者需要学习一下如何使用IDE的调试功能，你们可以自行谷歌一下，锻炼一下搜索能力，这不难，毕竟我们只需要最简单的打断点

## 基础知识巩固

学习Java，光学不练肯定是不行的。一定阶段的学习后，我们就需要一个项目来进行实践。

将书中源码调通,然后尝试实现下面的一些功能

[如何使用Java多线程对单个文件进行下载](images/https://blog.csdn.net/zhzhl202/article/details/7521377)

[丐版学生信息管理系统](images/https://blog.csdn.net/)
能实现学生的“增删改查”,应用类、泛型、数组列表、链表等基础知识
实践一个学生管理系统
类

```text
学生类
老师类
成绩
```

目标

```text
排序
增加
删除
修改

泛型测试
反射略解
```

### 数据结构

```text
普通数组测试
数组列表测试
链表测试
Map测试
 Map 映射关系
通常，我们知道某些关键信息，希望查找与之关联的元素。映射(map)数据结构就是为此设计的。
映射用来存放建/值对。如果提供了键，就能出查找到值。
例如键为员工ID，值为Employee对象。
```

[java-core-learning-example](images/https://github.com/JeffLi1993/java-core-learning-example)

## Spring

目前，Spring已经成为Java开发的基础设施，是任何一个Java程序员都必须掌握的内容。因此，在掌握了Java基础知识后，接下来应转入Spring的学习。
但在正式开始学习Spring之前，还有两个问题要解决：

```text
1. Spring相关jar包的管理。
2. 测试程序的编写及管理。
```

所以，在正式接触Spring知识之前，路线图首先安排了 Maven和Junit的学习。
Maven和Junit，从实用角度看都不难理解，上网搜索就可以满足学习的需要。

Spring的学习又分为两个阶段：Spring Core和Spring MVC。

Spring MVC是建立在Spring Core之上，在Web MVC领域的具体应用。因此，在学习Spring MVC之前，除了学习Spring Core，还必须掌握与Java Web相关的知识，其中最核心的就是Servlet。

在通常的Java学习中，会建议学生要掌握一定的前端知识，从而便于对Spring MVC进行测试。但前端知识庞杂，且边界不好界定，从而就给Java学习者带来很大的负担。

为此，在本学习大纲中，借鉴与行业通用做法，我推荐学生通过junt和HttpClient组合，用单元测试来满足Spring MVC的测试需求。

这样，在Java学习中，就完全避免了对前端知识的接触，极大的提高了学习效率。

特别提醒一下，Spring是Java学习中最难的部分。但是，一旦跨过这个门槛，从此之后，你基本就踏上了Java学习的通途。因此，对Spring学习一定有决心，要敢于迎难而上，不轻言放弃。

关于Spring的学习资料，我推荐《Spring实战》，虽然我个人对它并不十分满意，但已是我读过的最好的书。阅读的过程中，真遇到不理解的东西，记着随时上网搜索。

## 应用服务

在这一部分，我列举了Java开发中最常用的“中间件”。这些中间件涵盖了各个领域，包括持久化、缓存、队列、反向代理等。
其中列举的东西，虽然涉及广泛，但内容都相对独立，难度也有限。因此通过上网搜索，就可以满足学习的需求。
在掌握了这些中间件之后，你就会成长为一个能够独立编写Java后端程序，并对架构有一定理解的初级Java软件工程师。
最后，我想说的是，该“Java学习路线图”完全来自于我的一线开发经验，学习的节奏也经过实践的检验。因此，后来者只需“按图索骥”，自会以最少的投入，取得最好的学习效果。
祝你学习顺利！

## 项目实战

java的实战练手应该放到学完Servlet、spring等之后

### 学生管理系统

“学生管理系统”依旧是个很好的练手系统。，其中数据库设计、Mybatis，Spring、SpringMVC，Servlet、Tomcat一个都不缺，绝对的练手好伴侣。作为一个练手项目，目标就是把Java的主要技能点串起来，所以自不求尽善尽美（也不可能），

还有，虽然你的学习重点在Java，因为要做一个完整的demo，前端的配合肯定少不了。因此就免少不了要学一些简单的JS、HTML知识，但因为前端本就是个很大的topic，所以一定要控制好边界，千万不要顾此失彼。就“学生管理系统”来说，在前端上，只要实现一个包含table、textbox、button，能发送REST请求到server，能实现学生的“增删改查”的简单页面即可。

### [mall：电商系统](images/https://github.com/macrozheng/mall)

包括前台商城系统及后台管理系统，基于SpringBoot+MyBatis实现。

前台商城系统包含首页门户、商品推荐、商品搜索、商品展示、购物车、订单流程、会员中心、客户服务、帮助中心等模块。

后台管理系统包含商品管理、订单管理、会员管理、促销管理、运营管理、内容管理、统计报表、财务管理、权限管理、设置等模块。

### [Spring Boot API Project Seed](images/https://github.com/lihengming/spring-boot-api-project-seed)

Spring Boot API Project Seed 是一个基于Spring Boot & MyBatis的种子项目，

用于快速构建中小型API、RESTful API项目，该种子项目已经有过多个真实项目的实践，稳定、简单、快速，使我们摆脱那些重复劳动，专注于业务代码的编写，减少加班。

### [微人事管理系统](images/https://github.com/lenve/vhr)

前后端分离的人力资源管理系统，项目采用SpringBoot+Vue开发。

### [秒杀系统设计](images/https://github.com/qiurunze123/miaosha)

关于高并发大流量如何进行秒杀架构的项目。学习之前，先快速入门MQ、SpringBoot、Redis、Dubbo、ZK、Maven,lua，效果会更好！

- 下一节: [[0-2-已经过时的一些知识]]
