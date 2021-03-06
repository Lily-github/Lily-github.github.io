---
layout: post
title: 如何写好short description
---

## Foreword

最近正在学习DITA标准的结构化文档写作，在练习这种新型写作理念时发现，DITA各元素中最灵活但也最具挑战性的元素可能就是<shortdesc>，因为它能做的比仅仅充当一个主题的第一段还要多。简短描述（short description）文本会出现在链接中，在某些情况下也回出现在搜索引擎结果中。
因此，当把内容转换为DITA或者开始创作首个DITA主题时，创作有效的简短描述成为重中之重。

那么，今天就来一起聊聊如何写好简短描述（short description）。

## 简短描述在文中的位置

简短描述，元素标签<shortdesc>，是一个topic的第一个段落，其有效位置有：
- concept、task和reference主题的<title>元素和topic body之间。
- <abstract>元素内，位置也位于<title>元素和body主体之间。
- DITA map文件中的<topicref>元素内。

## 简短描述在文中的作用

简短描述常有以下几种用途：
- 一个topic的第一个段落
- 相关链接或子topic链接的链接预览（相关链接的悬停文本或者子主题链接下方的文本）
- 作为搜索引擎搜索结果的摘要

## 如何写好简短描述

如何简洁、高效写好简短描述？简短描述应该要描述整个主题的目的和中心点，通常可以关注两个问题：

- 该主题是关于什么的？
- 为什么用户需要关注该主题，或者用户需要从中获得什么信息？

**Tips**：

- 请在每个topic中都包含short description，且保持连续、一致。
- 为确保所有主题都包含short description，建议将<shortdesc>的属性规定成required，并且增加发布规则，在该元素缺失时提醒错误。
- 确保简短描述使用的是完整的句子，语法正确，标点恰当，并且符合风格指南。
- 不要在简短描述中引入列表、图片或者表格。
- 请确保简短描述的简洁性！一般字数控制在35字以内，极少数情况下，50字为上限。
- 若简短描述太长，请考虑将部分信息转移至body中呈现。
- 避免“自解释”式的简短描述，徒增无效字数而无有效信息。避免诸如以下的句式：
   +  this topic describes....
   +  this concept covers....
   + this information is about....
   + the following chapter explains...
- 简短描述不要简单的重复topic title！
- 不要在简短描述中使用交叉引用<xref>元素！


说了这么多，辣么，在不同主题中，究竟该如何开始简短描述的写作呢？下面，就一起来看看有没有什么具体的技巧。

## Task topic中的简短描述

task topic的简短描述写作指导。可回答以下一个或多个问题：

- 该task能帮助用户完成什么？
- 进行此项task的好处是什么？或者为什么task重要？
- 用户在何时该执行task？
- 执行task需要用到什么？
- 为什么用户需要完成task？
- task是如何与其他相关task联系的？

**请记得：**

- 关注task的益处或重要性
- 提供task步骤的概览
- 关注实际目标，而不是产品功能
- 提供简短的概念性信息
- 说明各个task是如何关联的

## Concept topic中的简短描述

concept topic简短描述写作指导：
- 对象、概念是什么？
- 为什么用户需要关心这一对象、概念？

**请记得：**
- 简要给对象或概念下定义
- 解释为什么用户需要理解这一概念

## Reference topic中的简短描述
reference topic 简短描述写作指导：
- 这一对象是做什么的？
- 这一对象是如何工作的？
- 这一对象用于什么或者为什么它有用？

**请记得：**
- 给对象下定义或者解释该对象是用于做什么
- 说明用户为什么使用这一对象
