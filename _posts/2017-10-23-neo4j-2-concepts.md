---
title: "2.Neo4j相关概念"
category: kg
layout: post
tags: [neo4j,kg]
date: '2017-10-17 21:30:24'
---


### 1.Neo4j graph database
一个简单的Neo4j数据库的样子如下所示：


<img src="/imgs/20171023-213314.png" alt="Smiley face" height="250">

它包含节点person和movie，关系ACTED_IN和DIRECTED，以及它们的属性name，born，title，released。

### 2.Node：
最简单的一个Node就像下面的样子：


<img src="/imgs/20171023-213602.png" alt="Smiley face" height="150">

它包含一个值为Forrest Gump的属性title。

下面再新建2个节点并分别添加2个属性，以及为上一个节点添加一个属性released。


<img src="/imgs/20171023-214046.png" alt="Smiley face" height="100">

### 3.Relationship

关系是图数据库的一个核心特性。关系连接2个节点，一个是源节点，一个是目标节点。正因为有了关系才使得节点构成了丰富又复杂的结构，可以是：列、树或者复合行的实体。


<img src="/imgs/20171023-215632.png" alt="Smiley face" height="250">

上图中关系类型有：```ACTED_IN```和```DIRECTED```。关系```ACTED_IN```的属性```roles```值为一个数组。

对于```ACTED_IN```关系来说，节点```Tom Hanks```是源节点，``` Forrest Gump ```是目标节点。我们可以这么形容：节点```Tom Hanks```有一个指向关系，``` Forrest Gump ```有一个被指向关系。

关系的方向在搜索的时候是等价的，也就是说是双向的。

关系还可以指向节点自身。


<img src="/imgs/20171023-220159.png" alt="Smiley face" height="150">

这表示着Tom Hanks KNOWS 他自己。

对于图：

<img src="/imgs/20171023-220311.png" alt="Smiley face" height="250">

可以得到下表：


<img src="/imgs/20171023-220358.png" alt="Smiley face" height="150">

上图展示了对于不同的查询角度来说，关系的指向是不同的。

### 4.属性

属性具有属性名和值，属性名是一个string，值的类型是：

- 数字
- 字符串
- 布尔值
- Point
- 时间类型
    - Date
    - Time
    - LocalTime
    - DateTime
    - LocalDateTime
    - Duration

下图是一个示例：

<img src="/imgs/20171023-221028.png" alt="Smiley face" height="150">

### 5.Label

Label对节点进行标记分成不同的集合或者称为类型。比如对于银行账户标记为```:Suspended```就表示这是封存的账户，对蔬菜标记```:Seasonal```就表示是当季的。
下面是一个示例：

<br>![]({{ "/imgs/20171023-221638.png" | absolute_url }})<br>

节点也可以有多个label：

<br>![]({{ "/imgs/20171023-221704.png" | absolute_url }})<br>

注意节点的label也可能是空的。

命名的时候使用驼峰命名法，比如CarOwner.


### 6.遍历

图遍历是从一个节点出发查找相邻的节点。
Cypher就是用于图查询的类SQL语言。


### 7.path


依据给定规则搜索到的子图就是一个path：

<br>![]({{ "/imgs/20171023-223723.png" | absolute_url }})<br>

也可以只是一个节点，此时长度为0

<br>![]({{ "/imgs/20171023-223755.png" | absolute_url }})<br>

或者长度为1：

<br>![]({{ "/imgs/20171023-223817.png" | absolute_url }})<br>

