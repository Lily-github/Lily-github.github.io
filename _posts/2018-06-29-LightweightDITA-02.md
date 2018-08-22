---
layout: post
title: Lightweight DITA系列（中篇）
---

## Foreword

Lightweight DITA系列共分上、中、下三篇。

在上篇中，介绍了Lightweight DITA是什么，三种基本文件类型及其内容写作示例。

本文通过一个虚拟团队写作任务，介绍如何使用LwDITA实现不同格式文件间协作和共享。

## 背景

LwDITA支持不同格式（XML、HTML5、Markdown）文件之间内容协作和共享。这意味着，**可以使用XDITA，HDITA，MDITA，或者DITA 1.3写作topics，然后通过content referencing或者key referencing，将所有topics集合到一个map中进行发布**。

现在，邀请您进入一个照明产品的文档开发团队，让我们一起来看看如何使用LwDITA共同写作并发布文档。

团队工作现状：

- 利用 @conref 和@keyref 机制实现重用。
- 拥有XDITA map文件，引用的topic文件包括XDITA，HDITA，MDITA和DITA 1.3格式。同时，使用key值定义了产品名称（product name）。
- TW写作的XDITA topic，重用了来自MDITA topic中的内容。
- 市场专家写作的HDITA topic，重用了来自XDITA topic中的内容。
- 开发人员写作的MDITA topic（extended-profile），重用了来自HDITA topic中的内容。
- 以上每个LwDITA topic都使用key reference重用产品名称（product name）。

接下来，就请领取你的写作任务，开启团队协作之旅吧~

## XDITA map

组织一个XDITA map，用于串起所有的topics。内容包括：

- XDITA topic，HDITA topic，MDITA topic 和 DITA 1.3 topic 的链接
- 为产品名称（product name）定义的 key 值

```
<map>
<topicmeta>
  <navtitle>Remote Lighting Setup</navtitle>
</topicmeta>
  
   <keydef keys="product-name">
      <topicmeta>
        <linktext>Remote Network Lighting</linktext>
      </topicmeta>
    </keydef>
  
  <topicref href="xdita-topics/bulbs-to-groups.dita" format="dita"/>
  <topicref href="hdita-topics/low-power.html" format="hdita"/>
  <topicref href="mdita-topics/basic-concepts.md" format="mdita"/>
  <topicref href="external/dita-topics/contact-info.dita" format="dita"/>
</map>

```

### XDITA topic

写作一个XDITA topic，完成主题，并且使用重用机制引用公共内容，包括：

- key reference重用产品名称（product name）
- content reference重用来自一个MDITA topic中的段落

```
<topic id="bulbs-to-groups">
   <title>Programming Light Bulbs to a Lighting Group</title>
   <shortdesc>You can program one or more light bulbs to a lighting group to operate that group with your remote control.</shortdesc>
   <body>
   <section id="context">
   <p>Your <ph keyref="product-name"/> remote control can manage up to 250 network light bulbs on the same lighting network. When you add a light bulb to the network, you can program it to one or more lighting groups.</p>
   <p id="assign-disclaimer">You must assign a light bulb to at least one lighting group to operate that light bulb.</p>
   </section>
   <section id="steps">
    <ol>
    <li><p conref="basic-concepts.md#basic-concepts/power-off" /></li>
    <li><p>Remove any existing light bulb from the light fixture.</p></li>
    <li><p>Install the network light bulb into the light fixture as you would any standard light bulb.</p></li>
    <li><p>Turn power to the light fixture on.</p></li>
   </ol>
   </section>
  </body>
  </topic>

```

## HDITA topic

写作一个HDITA topic，完成主题，并且使用重用机制引用公共内容，包括：

- key reference重用产品名称（product name）
- content reference重用来自一个XDITA topic中的段落

```
<!DOCTYPE html>
<html>
  <title>Low-Power Networking</title>   
  <article id="low-power">
    <h1>Low-Power Networking</h1> 
    <p>Your <span data-keyref="product-name"></span> operates at a low level of networking power but can successfully connect at long distances because they can send information from light bulb to light bulb.</p>
<p data-conref="bulbs-to-groups.dita#bulbs-to-groups/assign-disclaimer"></p>
    <p id="disconnect-warning" class="note">Even in low power networks, be sure to disconnect all devices before performing maintenance tasks.</p>
  </article>
</html>

```

### MDITA topic

写作一个MDITA extended-profile topic，完成主题，并且使用重用机制引用公共内容，包括：

- key reference 重用产品名称（product name）
- content reference重用来自一个HDITA topic中的段落

```
---
id: basic-concepts 
---
You can network LED light bulbs together to operate wirelessly from a remote control using the RemotaLux app.

# Basic Concepts of Network Lighting
   
Network light bulbs from your [product-name] work with your light fixtures the same way as standard light bulbs. They are different, however, in a couple of ways:
  
   - The lighting element in the light bulb uses energy-efficient LED technology.
   - The light bulb includes wireless technology that allows the light bulb to connect to a network and be managed remotely using the RemotaLux app.
   
<p id="power-off">Make sure power to the fixture where you are installing the light bulb is turned OFF.</p>
   
<p conref="low-power.html#low-power/disconnect-warning"></p>
   
```

## 发布团队内容

利用支持LwDITA的发布工具发布 .ditamap 文件，转换输出目标文件样式。

推荐尝试的工具有：

- DITA-OT 3.0及以上版本
- Oxygen XML Editor 20.0及以上版本

LwDITA最大的特点在于其轻量性，不同格式的兼容性和转换性，很是适合小规模文档开发团队之间的协作。

**相关阅读**

- [Lightweight DITA系列（上篇）](https://lily-github.github.io/LightweightDITA-01/)
- [Lightweight DITA系列（下篇）](https://lily-github.github.io/LightweightDITA-03/)
- [Lightweight DITA: An Introduction Version 1.0 ](<http://docs.oasis-open.org/dita/LwDITA/v1.0/LwDITA-v1.0.html>)

