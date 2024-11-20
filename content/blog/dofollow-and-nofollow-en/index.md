+++
title = "How to Use Dofollow and Nofollow Links"
description = "Introduction to what dofollow and nofollow are, as well as how to use them correctly."
slug = "dofollow-and-nofollow-en"
tags = ["SEO", "note"]
date = "2024-05-27"
draft = false
+++

🔄 [简体中文](/p/dofollow-and-nofollow/)

## What are Dofollow and Nofollow Links?

Dofollow and nofollow are two HTML attributes that indicate how search engine crawlers should handle links on a webpage.

Dofollow means that search engines will follow the link, and the current page will pass some weight to the linked page, thereby increasing the linked page's weight in search engines. The amount of weight transferred depends on the current page's weight in the search engine.

In other words, if website A uses a dofollow link to link to website B, website B's weight in search engines will be boosted. The extent of this boost is determined by website A's weight in the search engine; the greater website A's weight, the greater the boost for website B.

Nofollow is an attribute introduced by Google to help webmasters reduce spam links on their sites. When a link on a page is marked as nofollow, search engine crawlers will not follow that link to discover new content or build new indexes, and they will not pass any weight from the current page to the linked page. **Search engine crawlers will not further crawl nofollow links**.

Typically, ad links on websites and links in user comments are marked with the nofollow attribute.

The default attribute for the <a> tag in HTML is dofollow. To mark a link as nofollow, you can write it as follows:

```html
<a href="https://rokcso.com" rel="nofollow">Rokcso's Landing Page</a>
```

## How to Properly Use Dofollow and Nofollow Links?

The weight mentioned above essentially refers to PageRank (also known as PR value), which is one of the important metrics for search engine ranking. PR value can only be passed through dofollow links and cannot be passed through nofollow links.

Moreover, the distribution of PR value is averaged based on the links on the page, regardless of whether the link is allowed to be followed. For example, if the current page has a PR value of 10 and contains 10 links (5 dofollow and 5 nofollow), each dofollow link will receive 1 PR value transfer, not 2. The 10 PR value of the page is distributed evenly among all 10 links, but the links marked as nofollow will not receive the corresponding PR value transfer.

Since search engine crawlers do not crawl nofollow links, we can mark links to pages that we do not want search engines to crawl or do not need them to crawl (such as registration, login pages, etc.) as nofollow. This helps search engine crawlers more effectively index the pages that are worth indexing.

Buying and selling dofollow links (while selling links must be nofollow) to transfer PR value is strictly prohibited by search engines. They prefer that websites earn links through high-quality content, which helps improve the overall content quality of search engines.

No one knows exactly how search engines identify whether a website is buying and selling links, but at least Google provides a corresponding [paid link reporting tool](https://www.google.com/webmasters/tools/paidlinks). If reported, Google will investigate, and once verified, penalties will be imposed.

Generally, we believe that nofollow links do not affect search engine rankings. However, some claims suggest that nofollow links may also impact the ranking of the linked webpage in search engines. This is uncertain, as search engine algorithms are not fully disclosed. However, it is generally accepted that dofollow links on the same page will pass more weight to the linked webpage than nofollow links.

There is no need to pursue having all external links to your website as dofollow links; a certain proportion of nofollow links is normal (even having 100% dofollow links would be unusual).

Moreover, nofollow links are not entirely without value; after all, any link can increase exposure opportunities. Any link has the potential to bring traffic, and traffic can create opportunities for generating dofollow links.

The three core steps to building external links are: 1. Your website is seen, 2. Your website is liked, 3. Your website is shared.

## Reference

- [https://ahrefs.com/blog/zh/nofollow-links/](https://ahrefs.com/blog/zh/nofollow-links/)
