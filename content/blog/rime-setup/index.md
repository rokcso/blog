---
title: "我的 Rime 输入法配置方案"
description: "分享我常用的 Rime 输入法配置方案，基于雾凇拼音轻松用好 Rime。"
slug: "rime-setup"
tags: ["skill"]
date: "2024-07-19"
draft: false
---

[Rime](https://rime.im/) 是一个开源的输入法引擎，它支持多种输入方案，比如拼音、双拼、五笔等等，并且可以自定义输入方案。

使用 Rime 非常简单（也可以非常复杂），最简单的方式就是从 Rime 官网下载对应平台的客户端，Rime 客户端通常会内置一些默认的输入方案，当 Rime 默认的输入方案不满足我们的需求时就可以开始自定义配置啦！

我大概 5 年前就开始使用 Rime，在 Windows 平台使用 Rime 提供的官方客户端「小狼毫」，仅仅配置了 [小鹤双拼](https://flypy.com/) 输入方案和一些简单的皮肤样式、输入习惯等等。

词库、同步等等比较高级的配置都不曾涉及，每个使用 Rime 的用户都会有自己习惯的配置，为了保证每次换机等需要重新配置 Rime 时能更方便，个人维护一套自己的 Rime 配置非常有必要。

下面是我的安装、配置 Rime 的完整记录（macOS 平台）。

## 安装 Squirrel

Rime 在 macOS 平台的客户端名为「鼠须管（Squirrel）」，我通常使用 [Homebrew](https://brew.sh/) 安装，在 macOS 终端执行如下命令：

```bash
brew install --cask squirrel
```

随后打开 macOS 系统偏好设置，进入键盘设置，添加输入法选择简体中文下的鼠须管即可。

## 自定义配置

我现在的 Rime 配置使用的是 [雾凇拼音](https://github.com/iDvel/rime-ice) 维护的一套配置，输入方案依然是小鹤双拼。

我通过 Rime 官方的配置管理工具 [Plum](https://github.com/rime/plum) 来快速安装雾凇拼音的配置。

### 安装雾凇拼音配置

首先将 Plum 从 GitHub clone 到本地任意文件目录下：

```bash
git clone --depth=1 https://github.com/rime/plum
```

然后进入本地的 Plum 文件目录下，执行命令以安装雾凇拼音配置到本地 Rime 配置。

```
cd plum
bash rime-install iDvel/rime-ice:others/recipes/full
```

其实到这里整个 Rime 的雾凇拼音配置就已经安装完成可以正常使用了。

在启用 Rime 输入法的情况下，按下 `F4` 可以进入 Rime 的方案选单，雾凇拼音配置里面也预置了很多输入方案，我通常只保留全拼 + 小鹤双拼。

### 自定义部分配置

⚠️ 注意：一旦修改了 Rime 用户配置文件，必须「重新部署」之后才会生效。

在 macOS 系统下，Rime 的所有用户配置文件均保存在 `~/Library/Rime` 目录下，刚刚使用 plum 安装雾凇拼音配置其实就是将雾凇拼音的配置下载到本地并覆盖本地 Rime 的用户配置。

#### 基础配置

打开配置文件目录可以看到很多 `.yaml` 文件，这些就是配置文件，Rime 的核心默认配置在 `default.yaml` 文件中，我会进行如下更改：

- 方案列表（schema_list）：注释掉不用的输入方案，只保留全拼 + 小鹤双拼。

其他的配置暂时不会修改，默认的已经挺好用了，至于其他配置是什么意思、有什么用，雾凇拼音的配置文件中都有非常详细的注释。

然后是 Rime 输入法的皮肤配置，在 `squirrel.yaml` 文件中修改，这个就非常个性化了，我也会经常调整，此处不做记录。

#### 多设备同步

由于我需要在多台设备间同步我的用户词典和配置，所以我还会做一些同步相关的配置，在 `installation.yaml` 文件中修改 `installation_id` 和 `sync_dir` 即可。完整配置如下：

```yaml
distribution_code_name: Squirrel
distribution_name: "鼠鬚管"
distribution_version: 1.0.2
install_time: "Thu Jul 18 14:47:16 2024"
# 本机的 ID 标志，默认是一串 UUID
# 生成的文件夹是这个名字，可以改成更好识别的名称
installation_id: "rok_mac_mini"
rime_version: 1.11.2
# 同步文件保存的目录地址，默认是当前配置目录下的 `sync/`
sync_dir: "/Users/rokcso/Nutstore Files/rokConfig/Rime"
```

Rime 多设备同步需要借助第三方文件同步工具完成，比如：iCloud、Dropbox、坚果云等等，我使用的是 [坚果云](https://www.jianguoyun.com/)，本质上就是将 Rime 生成的同步文件存储在坚果云的同步文件目录中。

比如我在坚果云上创建了一个 `rokConfig/Rime` 这个目录，并且将其同步到我所有设备的本地，当我在设备 A、B 的 Rime 同步配置中将 `sync_dir` 设置为设备 A、B 本地的 `rokConfig/Rime` 时，假设设备 A 触发 Rime 同步，Rime 会更新同步文件到设备 A 本地的 `rokConfig/Rime` 文件目录下，然后坚果云的云同步会将本次更新的内容同步到设备 B 的本地。

这便实现了 Rime 多设备同步，其他第三方文件同步工具基本同理。

⚠️ 注意：上述案例中，设备 A 触发了 Rime 同步，设备 A 更新的同步文件通过坚果云同步到了设备 B 的本地，此时设备 B 需要再触发一次 Rime 同步才能启用设备 A 同步过来的最新用户词典和配置。这个操作可以理解为设备 B 本地的配置发生了变化，需要重新部署一下才能生效。