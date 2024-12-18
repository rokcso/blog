---
title: "个人向的中文文案排版指北"
description: "融合个人习惯的中文文案排版指南，统一中文文案、排版的相关规范。"
slug: "chinese-copywriting-guidelines"
tags: [
	"note"
]
date: "2024-10-29"
draft: false
hidden: false
---

我个人遵从的中文文案排版指北，重度参考 [sparanoid/chinese-copywriting-guidelines](https://github.com/sparanoid/chinese-copywriting-guidelines)，融合了一些个人习惯。

注意：本文所述的文案排版并非从设计、前端角度去思考的视觉风格化排版，绝大多数情况仅针对普通用户通过电子设备、互联网创作和发布的文章的排版。

## 空格

在特定类型的字符之前增加空格，以此提供适当的留白，让文字更有呼吸感。

1. **中文与英文之间增加空格**

比如：即使是 Markdown 格式下使用行内 Code 样式的 `hello` 也需要增加空格。

2. **中文与数字之间增加空格**

比如：这是 10 个苹果，数字前后都有空格。

3. **超链接前后增加空格**

比如：你可以通过访问 [Rokcso 的博客](/) 查看我的最新动态。

4. **数字与其单位之间不增加空格**

比如：这台电脑的内存是 8GB，还是不够用；运行一些简单的软件内存占用就已经达到 80% 了。

但是如果单位使用的中文表示，则需要遵循「中文与数字之间增加空格」，比如：iPhone 16 的屏幕是 6.1 英寸的 OLED 全面屏。

5. **全角标点符号与其他任何字符之间不增加空格**

比如：这个比如后面紧跟着的冒号就是一个全角标点符号，以及刚刚这个逗号也是，不管其前后是什么类型的字符，比如：English 或者数字，都不要增加空格。

6. **每段文字开头不要空两格**

## 标点符号

1. **使用直角引号**

这没啥好说的，就是「这样」的一个直角引号。

2. **使用标准省略号**

输入法在中文输入模式下通过 Shift + 6 可以输入标准省略号「……」，尤其不要使用「...」甚至是「。。。」这样的连续句点或句号。

3. **不重复使用标点符号**

比如：牛逼！！！这样重复使用三个感叹号是不合适的。

另外「？！」这样的标点符号用法也是不太符合传统规范，尽量避免使用。

## 全角 & 半角

1. **使用全角中文标点符号**

在文章主要文字是中文的情况下，标点符号都使用全角中文标点符号。

对于英文书名、报刊名等等，不要使用中文书名号，而是直接对英文书名、报刊名应用斜体样式即可。次之则是可以使用半角英文标点符号中的双引号来包括英文书名、报刊名。

比如：这本书是 *A Rose for Emily*，或者 "A Rose for Emily" 是一本不错的书。

2. **数字不要使用全角数字符号**

一般都不会有人用到全角数字符号（吧？），我甚至不知道怎么快捷的输入全角数字。

3. **完整英文原句、引用表述等使用英文半角标点符号**

比如：这里完整引用「Stay hungry, stay foolish.」这句话，那么中文直角引号中的内容的标点符号就保持原文样式和规范了。

再比如：推荐你阅读 *Hackers & Painters: Big Ideas from the Computer Age* 这本书，这里使用斜体样式表示英文书名，并且保持书名中的标点符号符合原文样式和规范。

## 专有名词

1. **中英夹杂的专有名词**

通常来说，专有名词可以按照官方定义，不受上述约束，比如「豆瓣FM」这里「瓣」和「F」之间可以不增加空格；但是当「豆瓣FM」出现在一个句子当中时，「M」和其他中文之前是否增加空格？

这时反而是直接对「豆瓣FM」前后同时增加空格更为符合留白的意义。比如：我经常使用 豆瓣FM 来听歌。

2. **专有名词中的英文的大小写**

比如：使用 GitHub 而不是 Github。

遵守专有名词官方的表述，但是有时为了页面排版的风格化，可能会使用全大写或全小写英文，这是可以接受的，日常书面表达中一般不涉及。

## 缩写

1. **不要在未说明的情况下使用缩写**

这里包括：1）不要使用非常小众、不规范、错误的缩写；2）在文章中首次使用某个缩写时特别说明下文中特定缩写的具体指代内容。

比如：将 HTML5 缩写为 h5 是不规范的，一般为 H5；将 React 缩写为 RJS 是非常小众、甚至是错误的，React 一般没有缩写。

由于一个缩写通常可以指代多个不同的具体的内容，在不同语境中同一个缩写所指代的具体内容可能千差万别，所以在一个语境中首次使用某个缩写时特别说明一下，并且在后文中不要更改该缩写所指代的具体内容。

比如我现在在说 Television（后文均用 TV 指代）相关的内容，并且我特别说明了后文都用 TV 指代 Television，那么当后文中这个 TV 缩写再次出现时它就不应该作为 Time Value 的指代。

## Markdown

1. **H1 仅用于文章标题，正文小标题从 H2 开始**

正文部分的小标题样式从 H2 开始逐级递增，注意小标题层级不要过多，一般保持在 3 层及以内，通常只用到 H2、H3、H4 即可。

## 其他

1. **谨慎使用样式**

包括但不限于加粗、高亮、斜体、删除线等样式，需要重点标注的只使用加粗，尽量不要使用任何彩色高亮，尽量不要多种样式叠加使用，中文避免使用斜体。

重点标注得太多就会失去重点。

2. **超链接文本应该能说明所链接的内容**

避免使用「点击 [这个链接](/) 去访问我的博客」这种写法；更推荐使用「点击 [Rokcso's Blog](/) 去访问我的博客」这种写法。

## 参考

- [中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines)
- [这些排版技巧可以让你的文章更美观 | Matrix Early Birds 群分享](https://sspai.com/post/36291)
- [写给大家看的中文排版指南](https://zhuanlan.zhihu.com/p/20506092)
- [少数派写作排版指南](https://sspai.com/post/37815)
- [少数派风格指南](https://manual.sspai.com/rules/style/index.html)

拓展

- [中文排版需求](https://www.w3.org/TR/clreq/)