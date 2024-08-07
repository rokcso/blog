+++
title = "macOS 彻底阻止 FigmaAgent.app 被添加到登录项"
description = "如何让 macOS 下的 FigmaAgent.app 不再频繁自动添加到登录项中。"
slug = "figmaagent-auto-login"
tags = [
    "skill",
    "macOS"
]
date = "2024-06-03"
draft = false
+++

> 我的 macOS 版本：Sonoma 14.5

在使用 Figma macOS 客户端时，总有一个 FigmaAgent.app 被自动添加到登录项，即使在「系统设置 - 通用 - 登录项」中手动删除该项目，再次打开 Figma 依然会自动添加，这很烦人。😡

![alt text](image.png)

## 解决方案

1. 打开「活动监视器」，找到 FigmaAgent，选中后点击「停止（退出）」后选择「强制退出」。

![alt text](image-1.png)

2. 访问「系统设置 - 通用 - 登录项」，删除 FigmaAgent.app。
3. 打开「访达」，进入 `~/Library/Application Support/Figma` 文件夹，删除 FigmaAgent.app。

![alt text](image-2.png)

4. 打开「访达」，进入 `/Applications/Figma.app/Contents/Library` 文件夹，删除 FigmaAgent.app。

完成！✅

