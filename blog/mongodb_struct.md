<!--
author: Jack.Spanrrows
date: 2018-02-12 
title: Ubuntu下MongoDB的安装和使用
tags: MongoDB
category: MongoDB
status: publish
summary: Ubuntu下MongoDB的安装和使用
-->
##### MongoDB简介
```
MongoDB 是一个是一个基于分布式文件存储的数据库，介于关系数据库和非关系数据库之间，是非关系数据库当中功能最丰富，最像关系数据库的。他支持的数据结构非常松散，是类似json的bson格式，因此可以存储比较复杂的数据类型。Mongo最大的特点是他支持的查询语言非常强大，其语法有点类似于面向对象的查询语言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。
```

##### 安装MongoDB
```
MongoDB安装很简单，无需下载源文件，可以直接用apt-get命令进行安装。 
打开终端，输入以下命令：
sudo apt-get install mongodb

```
![avatar](./mongodb1.png)
```
安装完成后，在终端输入以下命令查看MongoDB版本：

mongo -version
```

#####启动和关闭mongodb命令如下：

```
service mongodb start

service mongodb stop
```