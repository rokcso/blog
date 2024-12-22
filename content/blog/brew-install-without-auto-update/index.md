---
title: "在 brew install 时不要 Auto update"
description: "学习如何通过设置环境变量禁用 Homebrew 的自动更新功能，从而加快应用程序的安装速度。掌握这一技巧，提升你的开发效率，避免因自动更新而浪费的时间。"
slug: "brew-install-without-auto-update"
tags: ["skill"]
date: "2024-12-22"
draft: false
hidden: false
---

今天需要使用 Homebrew 安装一个 App，但是当我执行 `brew install {app_name}` 后，没想到终端里最先打印出来的是「Auto-updating Homebrew...」，随后 Homebrew 发现我有 38 个过时的 formulae，并开始了一系列 Fetching 和 Downloading 的 Auto-updating，大约 30 多分钟后，我原本要安装的 App 才被成功安装。

这就是 Homebrew 的默认逻辑，在每次执行 `brew install` 时，先更新 Homebrew 本体，再检查所有已安装的 App，并自动更新已过时的 App，再清理不再需要的旧版本和缓存文件，最后才是安装原本要安装的 App。

我知道 Homebrew 是出于好意，但是有的时候，这个逻辑真的很耽误事。

## 如何解决

在 Homebrew 安装命令之前添加环境变量：

```shell
HOMEBREW_NO_AUTO_UPDATE=1 brew install {app_name}
```

将环境变量 `HOMEBREW_NO_AUTO_UPDATE` 设置为 `1` 即表示禁用自动更新。也可以直接将该环境变量在 `~/.bashrc` 或 `~/.zshrc` 配置文件中 `export`：

```shell
export HOMEBREW_NO_AUTO_UPDATE=1
```