---
layout: post
title: DITA-OT之自定义PDF输出
---

## Foreword

运用 dita-ot 工具进行ditamap发布时，样式总是达不到要求，特别在发布中文资源时字体问题，在输出中文时经常会出现乱码的情况。

利用 dita-ot  自由定制PDF输出，官方user guide介绍了好几种途径。详细见官网介绍
 [http://www.dita-ot.org/dev/topics/pdf-customization.html]()

本文结合个人学习过程，介绍其中一种最为推荐的方式——利用custom PDF plug-in输出较为满意的pdf。

## Step one: 自定义你的PDF plug-in

这里推荐一个好用PDF plug-in生成工具，在官网的user guide中也有提及和推荐。

[PDF Plugin Generator](http://dita-generator.elovirta.com/) 

又是一款开源工具哦，向开发者大大地致敬，嘿嘿~~

不卖关子，直接开干。

这是一款在线的、免费的可用于与dita-ot的PDF customization plug-in生成工具。自定义各元素的样式规格，自动生成plug-in压缩包。

在生成过程中，做以下设定：

*   选择要用于的dita-ot版本（现在已经是dita-ot 3.0啦~）
*   选择XSL样式发布引擎 （FOP, Antenna House Formatter 或者 RenderX XEP）
*   自定义PDF页面大小，分栏数目和页边距
*   选择页眉页脚显示的内容（比较遗憾的是，这块不能做很大的自定义，目前提供的选项有：版权信息、标题、页码、总页码数）
*   设定章节的显示
*   自定义各文档元素的样式：
    *  普通文本，即正文
    *   标题（提供四级标题）
    *   section标题和example标题
    *   表格和图表
    *  注意和示例
    *  列表（有序列表、无序列表和定义列表） 
    *   代码块和特殊格式的文本
    *   内联元素（链接、商标等）

   对每类文档元素，可进行以下样式设定：
    *  字体、字号、粗斜体样式 
    *   字体颜色和背景颜色
    *   对齐，缩进，行前行后距离等

长这样子的~~

![PDF Plugin Generator.png](https://upload-images.jianshu.io/upload_images/7998833-d7e7cf2a43b4fce4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

利用在线工具生成PDF plugin后，最后可得到一个 *custom_pdf.zip* 文件。

> **友情提示：** PDF Plugin Generator中提供的字体，对中文不甚友好，默认字体是Times New Roman。所以，如果要发布中文，需要自行修改些xsl文件中的字体部分。主要包含以下xsl文件：**

![待修改字体的xsl文件.png](http://upload-images.jianshu.io/upload_images/7998833-cd84419a3a8408c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 批量查找 `font-family` 关键字，定位到不同元素的字体值位置，然后替换成你想要的字体吧，最后压缩打包成原本的zip模样。


## Step two: 安装 Customization PDF Plugin

好啦，得到了心仪的pdf输出样式plugin，下一步，在dita-ot工具中安装该插件。
语法就很简单了。

```
dita --install custom_pdf.zip

```

可以前往dita-ot-3.0根目录下 `plugins `文件夹中看到，就已经有自定义的plug-in文件夹了，长这样的~

![成功安装后的customization plug-in.png](http://upload-images.jianshu.io/upload_images/7998833-5414066f7cd4de4d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## Step three: 调用Customization PDF Plug-in 发布PDF

激动人心的时刻要来了。

最后的最后，当然是看看我们自定义的样式如何了。

使用发布命令

```
dita -i=input file  -f=transtype

```

此处的`transtype`为利用 PDF Plugin Generator生成zip文件最后一步设置的参数。

![生成前设定transtype.png](http://upload-images.jianshu.io/upload_images/7998833-c6e2618f4a58600e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果一时忘记了，也是无关紧要的，随时到 customization plug-in文件夹目录下`plugin.xml` 文件中一看便知~~

![plugin.xml文件查看transtype.png](http://upload-images.jianshu.io/upload_images/7998833-83921fdf5518c901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后，就好好自我欣赏你的劳动成果吧~

以上，各位可以动手试试哦~

另外，推荐其他样式定制资源和工具：[http://www.ditawriter.com/dita-related-software-tools/]()
