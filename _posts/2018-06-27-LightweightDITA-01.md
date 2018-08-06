---
layout: post
title: Lightweight DITA系列（上篇）
---


## Foreword

Lightweight DITA系列共分上、中、下三篇。

本文介绍何为Lightweight DITA，以及Lightweight DITA三种基本文件格式的特点和示例。

## 何为Lightweight DITA

Lightweight DITA，简称LwDITA，故名思义，轻（shou）量（shen）级（hou）的DITA标准。

相比于DITA 1.3，LwDITA具有以下特点：

- 元素类型更少（smaller element type）
- 元素的属性值更少（smaller element attribute set）
- 内容模型更严格（stricter content models）
- 功能设置更少（reduced feature set）
- 新增多媒体元素类型

除以上基本区别外，LwDITA相较于DITA 1.3最大的一个特点：能建立XML、HTML5、Markdown文件之间的映射。换言之，**LwDITA支持建立由三种不同标记语言编写的topic文件组成的map**。

从此，你可以：

- 体验更简洁、轻量级的DITA
- 不同格式偏好的技术写作者不必顾虑文件格式的“强行一致”
- 由不同标记语言编写的源文件能轻松转换并发布

## 支持的文件格式

LwDITA支持三种文件格式：

- XDITA：基于XML
- HDITA：基于HTML5
- MDITA：基于Markdown

## XDITA

使用XML编写的LwDITA文件格式，是DITA的一个子集，包含多媒体元素类型，能与HTML5文件相互转换。

XDITA适用于想使用DITA标准写作技术信息，却无需完整的DITA标准的技术写作者。

例如：

- 使用XML 编辑器，但只想使用DITA的部分元素和属性值
- 减少开发和维护样式表（CSS）的成本
- 让已有的DITA内容兼容Markdown或者HTML5内容

### XDITA topic示例

以下为一个XDITA topic示例：

```
<topic id="install-and-setup">
  <title>Installing and Setting up Remote Lighting</title>
  <shortdesc>Installation of your lighting kit includes installing the light bulbs into  light fixtures, preparing the remote control, and programming lighting groups.
  </shortdesc>
  <prolog>
    <data name="author" value="Kevin Lewis"/>
  </prolog>
  <body>
   <section>
    <title>Steps</title>
    <ul>
      <li><p>Install light bulbs.</p></li>
      <li><p>Prepare remote control.</p></li>
      <li><p>Program lighting groups.</p></li>
    </ul>
  </section> 
  <section>
    <title>Example</title>
    <p>The following video demonstrates a recommended installation:</p>
    <video>
      <media-controls />
      <video-poster value="remote-poster.jpg" />
      <media-source value="remote.mp4" />
    </video>
  </section>
  </body>
</topic>

```

### XDITA map示例

以下为一个XDITA map示例：

```
<map id="remote-main">
    <topicmeta>
     <navtitle>Remote Lighting Network</navtitle>
    </topicmeta>
    <keydef keys="product-name">
      <topicmeta>
        <linktext>Remote Network Lighting</linktext>
      </topicmeta>
    </keydef>
    <topicref href="introduction.dita">
     <topicmeta>
      <navtitle>Introduction</navtitle>
     </topicmeta>
    </topicref>
    <topicref href="alternatives.dita">
     <topicmeta>
      <navtitle>Alternative lighting setups</navtitle>
     </topicmeta>
     <topicref href="low-power.dita">
      <topicmeta>
       <navtitle>Low power installation</navtitle>
      </topicmeta>
     </topicref>
     <topicref href="high-power.dita">
      <topicmeta>
       <navtitle>High power installation</navtitle>
      </topicmeta>
     </topicref>
    </topicref>
</map>


```

> **注意：** XDITA 要求在 <topicmeta> 必须包含<navtitle> ，声明map中topic的标题。

## HDITA

使用HTML5编写的LwDITA文件格式，包含定制的数据属性，以实现与DITA之间的相互转换。

HDITA特别适合下列群体：

- 市场文档写作者，不使用XML编辑器，但能贡献基于DITA的产品信息
- 使用HTML写作工具的开发人员
- 教师或培训师，想要为学习管理系统创建在线的课程内容
- 想使用移动端设备编辑内容的博主或内容架构师
- 只需编写内容但无需发布的文档作者
- 熟悉和偏好HTML5元素的文档写作者

### HDITA topic 示例

以下为一个HDITA topic示例：

```
<!DOCTYPE html>
<html>
<head>
  <title>Installing and Setting up Remote Lighting</title>
</head>
<body>
  <article id="install-and-setup">
    <h1>Installing and Setting up Remote Lighting</h1>
    <p>Installation of your lighting kit includes installing the light bulbs into light fixtures, preparing the remote control, and programming lighting groups.</p>
    <h2>Steps</h2>
    <ul>
      <li>
        <p>Install light bulbs.</p>
      </li>
      <li>
        <p>Prepare remote control.</p>
      </li>
      <li>
        <p>Program lighting groups.</p>
      </li>
    </ul>
    <h2>Example</h2>
    <p>The following video demonstrates a recommended installation:</p>
    <video src="remote.mp4" controls poster="remote.png"></video>
    <p data-conref="bulbs-to-groups.dita#bulbs-to-groups/assign-disclaimer"></p>
  </article>
</body>
</html>


```

### HDITA map示例

以下为一个HDITA map示例：

```
<nav>
    <h1>Remote Lighting Network</h1>
    <div class="keydef">
    <span class="linktext" data-keys="product-name">Remote Lighting Network</span>
    </div>
    <ul>
     <li><p><a href="introduction.html">Introduction</a><p></li>
     <li><p><a href="alternatives.html">Alternative lighting setups</a></p>
      <ul>
       <li><p><a href="low-power.html">Low power installation</a></p></li>
       <li><p><a href="high-power.html">High power installation</a></p></li>
       </ul>
      </li>
     </ul>
   </nav>
   
```

## MDITA

使用Markdown编写的LwDITA文件格式。包含两种类型：

- 核心类型（core profile）对应Github Flavored Markdown。
- 扩展类型（extended profile）适用于特殊的Markdown Flavor，提供DITA-like的体验

MDITA特别适合下列群体：

- 市场文档写作者，不使用XML编辑器，但能贡献基于DITA的产品信息
- 贡献产品文档的开发人员，但希望自由选择标记语言文档编辑工具
- 负责API文档应用的开发或者技术写作者，需要将内容与其他技术文档应用共享
- 想要使用移动端（但不支持XML编辑器）编辑的写作者
- 希望内容后期能快速地转换为结构化的内容
- 希望利用DITA重用和发布机制，但不依赖于XML标签的写作者

### MDITA topic_core profile示例

包含Markdown业已支持的元素：

- Title
- Paragraph
- Section title
- Unordered list
- Table
- Code block

MDITA core profile对应Github Flavored Markdown Spec.

以下为一个MDITA core-profile topic示例：

```
# Installing and Setting up Remote Lighting

Installation of your lighting kit includes installing the light bulbs into light fixtures, preparing the remote control, and programming lighting groups.

## Steps

  1. Install light bulbs.
  2. Prepare remote control.
  3. Program lighting groups.

## Example

 ![Image](remote.png)

```

### MDITA topic_extended profile示例

MDITA extended profile支持以下两类情况，与其他LwDITA文件格式或DITA1.3转换性更好。

- YAML front matter header 。

   可用于提供 @id 属性，同时也可以包含prolog metadata信息。

   若topic需要添加YAML front matter header，务必将其放在MDITA文件的文件头位置，且必须用两行 三短线之间。

- 其他HDITA支持的属性和元素类型。

以下是一个MDITA extended-profile topic示例。

```
---
id: install-and-setup
author: Kevin Lewis
---

# Installing and Setting up Remote Lighting

Installation of your lighting kit includes installing the light bulbs into light fixtures, preparing the remote control, and programming lighting groups.

Before you attempt to install your lighting kit, please turn off the power in your electrical circuit panel,

## Steps

  1. Install light bulbs.
  2. Prepare remote control.
  3. Program lighting groups.

## Example

The following video demonstrates a recommended installation:

<video src="remote.mp4" controls poster="remote.png"></video>

```

### MDITA map示例

以下是一个MDITA map的示例：

```
# Remote Lighting Network
   
   - [Introduction](introduction.md)
   - [Alternative lighting setups](alternatives.md)
       - [Low power installation](low-power.md)
       - [High power installation](high-power.md)

```


**相关阅读**

- [Lightweight DITA系列（中篇）](2018-06-29-LightweightDITA-03.md)
- [Lightweight DITA系列（下篇）](2018-07-04-LightweightDITA-03.md)
- [Lightweight DITA: An Introduction Version 1.0 ](<http://docs.oasis-open.org/dita/LwDITA/v1.0/LwDITA-v1.0.html>)

