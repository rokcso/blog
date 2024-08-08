+++
title = "dofollow & nofollow"
description = "介绍什么是 dofollow 和 nofollow，以及如何正确的使用。"
slug = "dofollow-and-nofollow"
tags = ["SEO", "note"]
date = "2024-05-27"
draft = false
+++

## 什么是 dofollow 和 nofollow 链接？

dofollow 和 nofollow 是两个 HTML 属性，用于指示搜索引擎爬虫如何处理网页上面 link 的链接。

dofollow 意味着搜索引擎会跟随这个链接，并且当前页面会传递一定的权重给被链接的页面，即增加被链接页面在搜索引擎中的权重，增加权重的多少根据当前页面在搜索引擎中的权重不同而不同。

也就是说如果网站 A 使用 dofollow 链接了网站 B 的链接，网站 B 在搜索引擎中的权重会得到提升，提升的多少由网站 A 在搜索引擎中的权重决定，即网站 A 在搜索引擎中权重越大，网站 B 得到的权重提升也越大。

nofollow 是由 Google 引入的属性，目的是帮助网站管理员减少网站的垃圾链接，当页面中的一个链接被标记为 nofollow 时，搜索引擎爬虫将不会跟随这个链接去发现新的内容、建立新的索引，同时也也不会从当前页面传递任何权重到被链接页面。**搜索引擎的爬虫甚至不会进一步爬取 nofollow 链接。**

一般网站的广告链接、用户评论内容中的链接会使用 nofollow 属性来标记。

HTML 中 <a> 标签默认的属性是 dofollow，如果要标记为 nofollow 可以如下编写：

```html
<a href="https://rokcso.com" rel="nofollow">Rokcso's Landing Page</a>
```

## 如何正确应用 dofollow 和 nofollow 链接？

上面提到的权重本质上就是 [PageRank](craftdocs://open?blockId=CD09006B-0CCF-4E35-BF90-34650282AA0C&spaceId=e9983e66-9ce7-993a-ad36-dd817783b2b8)（也被称为 PR 值），是搜索引擎排名的重要指标之一。PR 值只能通过 dofollow 链接传递，不能通过 nofollow 链接传递。

并且 PR 值的分配是根据页面上搜索链接来平均分配的，不论这个链接是否允许 follow，比如当前页面的 PR 值为 10，页面中有 10 个链接（5 个 dofollow 和 5 个 nofollow），那么每个 dofollow 链接将分别获得 1 PR 值传递，而不是 2；该页面的 10 PR 值被平均分给了该页面中的所有 10 个链接，只是其中标记为 nofollow 的链接不会获得对应的 PR 值传递。

由于搜索引擎爬虫不会爬取 nofollow 链接，所有我们可以将不希望搜索引擎爬取或者没有必要让搜索引擎爬取的页面（比如注册、登陆等等）的链接标记为 nofollow，以帮助搜索引擎爬虫更有效的抓取到更值得被索引的页面。

通过付费买卖 dofollow 链接（可以买卖链接，但必须是 nofollow 链接）来传递 PR 值的行为是被搜索引擎明令禁止的，搜索引擎更希望网站通过其优质的内容来获得被链接，这有助于提升搜索引擎整体的内容质量。

没人清楚搜索引擎如何识别网站是否付费买卖链接，但是至少 Google 提供了对应的 [付费链接举报工具](https://www.google.com/webmasters/tools/paidlinks)，被举报后 Google 将进行检查，一旦查实必定得到惩罚。

通常情况下我们都认为 nofollow 链接不会影响搜索引擎排名，但是有的说法表示 nofollow 链接可能也会影响被链接网页在搜索引擎中的排名，这无从得知，搜索引擎的算法时不可能完全公开的。但是同一个页面中的 dofollow 链接会比 nofollow 链接向被链接网页传递更多的权重这基本是可以确定的。

不必追求自己网站获得的所有外链都是 dofollow 链接，一定比例的 nofollow 链接是正常的（甚至比 100% 是 dofollow 更为异常）。

并且 nofollow 链接也不是一无是处的，毕竟只要是链接都能增加被曝光的机会，即任何链接都有可能带来流量，而流量则可以提供产生 dofollow 链接的机会。

建设外链最核心的三步转化：1）你的网站被看见、2）你的网站被喜欢、3）你的网站被分享。

---

参考：
- [https://ahrefs.com/blog/zh/nofollow-links/](https://ahrefs.com/blog/zh/nofollow-links/)
