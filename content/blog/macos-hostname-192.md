+++
title = "修复 macOS 终端主机名显示 192"
description = "修复 macOS 终端中主机名始终显示 192 的异常。"
slug = "macos-hostname-192"
tags = [
    "macos",
    "skill"
]
date = "2024-08-07"
draft = false
+++

通常 macOS 终端（Terminal）App 中显示的主机名（HostName）应该是当前设备设定的用户名。

但是有时打开终端时会发现主机名变成了 192，这主要是由于当前使用的 DNS 服务因为某些原因变成了默认的 `192.168.1.1` 或 `192.168.0.1`，我通常在启动了代理服务之后会出现。

**解决方案一**

> 设备：Mac mini M2
> 
> macOS: Sonama 14.6

这种情况首先可以尝试修改 DNS 设置，打开「系统偏好设置 -> 网络（或 Wi-Fi） -> 详细信息 -> DNS」。


如果这里的 DNS 服务器为上面提到的默认 IP 地址，那么直接删除，然后添加新的 DNS 服务器 IP 地址：`8.8.8.8` 即可。

⚠️ 注意：修改 DNS 配置后记得「应用」。

**解决方案二**

首先确认本机是否存在已配置的 HostName，打开终端执行以下命令：

```bash
scutil --get HostName 
```

如果本机没有配置 HostName，那么执行该命令不会获得任何输出，如果存在 HostName 则会直接返回 HostName 字符串。

当本机没有配置 HostName 是，终端的主机名会使用来自 DNS 或者 DHCP 服务器，所以我们也可以通过主动配置一个 HostName 解决这个问题，在终端执行以下命令：

```bash
sudo scutil --set HostName "yourHostName"
```

⚠️ 注意：使用你想要设置的 HostName 替换上面命令中的 `yourHostName` 。