+++
title = "Favicon 最佳实践"
description = "介绍如何使用最小化的 Favicon 配置，满足绝大多数需求。"
slug = "how-to-favicon"
tags = ["dev", "note"]
date = "2024-08-08"
draft = false
+++

Favicon 是 favorite icon 的缩写，在网站的用户侧，用户看到的一个图标实际上是由很多很多个图标文件组成，这主要是为了适配各种各样的设备和屏幕。

使用 Favicon 生成器可以便捷的生成非常全面的 Favicon 集，但是这显然不是一个优雅的解。Andrey Sitnik 提出了下面这个最小化的 Favicon 配置，这些图标将在所有情况下和所有浏览器中工作，即使在某些边缘情况，这仍然有效，只是不是 100% 完美。

## 最小化配置

大多数情况下，只需要 5 个图标（各种文件格式）和一个 JSON 文件。

首先在 HTML 代码中使用如下配置：

```html
<link rel="icon" href="/favicon.ico" sizes="32x32">
<link rel="icon" href="/icon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png"> <!-- 180×180 -->
<link rel="manifest" href="/manifest.webmanifest">
```

而对应的 manifest 则使用如下配置：

```json
// manifest.webmanifest
{
  "icons": [
    { "src": "/icon-192.png", "type": "image/png", "sizes": "192x192" },
    { "src": "/icon-512.png", "type": "image/png", "sizes": "512x512" }
  ]
}
```

## 配置解释

`favicon.ico` 适用于那些古老的浏览器，注意一定将该文件放在网站根目录下，即 `https://rokcso.com/favicon.ico`，尺寸建议始终坚持使用 `32x32` 大小。

`icon.svg` 一个文件就可以提供给现代浏览器明/暗两个版本的图标，SVG 是一种矢量格式，它描述的是曲线而非像素，SVG 本质上是一种 XML 格式的文件，可以包含一个 `<style>` 标签来描述 CSS，所以可以使用 CSS 的一些特性（包含媒体查询），比如利用 `@media (prefers-color-scheme: dark)` 来[切换同一个图标的明/暗版本](https://web.dev/articles/building/an-adaptive-favicon?hl=zh-cn)。

`180x180` 大小的 PNG 图像适用于 Apple 设备，Apple touch icon 是 Apple 设备将网页添加到桌面快捷方式时显示的 App icon，尺寸使用 `180x180`，即使在某些设备上被压缩后也能得到一个较高质量的图标，如果给 Apple touch icon 提供 20px 的 padding 填充并添加一些背景色，会让图标在视觉上更好看。

`manifest.webmanifest` 包含适用于 Android 设备的 `192x192` 和 `512x512` 尺寸的 PNG 图像，与 Apple touch icon 类似，这种格式的图标来自于 Google PWA 的倡议，都是应用于将网站添加为桌面快捷方式时作为 App icon 使用。

## 如何制作 Favicon

### Step 01 > 准备 SVG 文件

一切的开始都是图标的 SVG 文件，注意确保该 SVG 是正方形，具体如何制作 SVG 图标这里不介绍。

将图标保存为 `icon.svg` 后，使用文本编辑器（比如 Visual Studio Code）打开该文件，文件内容是使用 `<svg> ... </svg>` 标签包裹着 `<path />` 标签的 XML 代码，图标的内容就是通过 `<path />` 实现（绘制曲线）的。

我们可以在 `<svg> ... </svg>` 中第一层级添加一个 `<style>` 标签，使用 CSS 语法来添加一个媒体查询，并且设置暗色主题下 SVG 的样式。比如：

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 447 428">
    <style>
        .favicon-stroke {
            stroke-width: 8px;
            stroke: #8929ff;
        }
        #skull-outline { fill: white }
        #eyes-and-nose, #hat-outline { fill: #8929ff }
        #hat-fill, #hat-bill { fill: #e662e6 }

        <!-- 设置暗色主题下 SVG 图标的样式 -->
        @media (prefers-color-scheme: dark) {
            .favicon-stroke { stroke: #343a40 }
            #skull-outline { fill: #adb5bd }
            #hat-outline { fill: #343a40 }
            #eyes-and-nose { fill: #343a40 }
        }
    </style>
    <g id="skull">
        <path id="skull-outline" class="favicon-stroke" stroke-linejoin="round" d="M19.62 188.39A166.62 166.62 0 0 1 186.24 21.77c115.25 0 166.61 74.59 166.61 166.62 0 1.83-.08 3.64-.13 5.46h.13s.68 175.09.68 178.65c0 30.11-16.26 41.67-36.32 41.67-12.7 0-35.22-3.93-36.22-32.69h-.2c-1 28.76-16.81 32.69-36.22 32.69-18 0-32.87-6.78-35.77-32.53-2.9 25.75-17.8 32.53-35.8 32.53-20.06 0-36.32-11.56-36.32-41.67 0-2.48.36-24.88.36-24.88A166.68 166.68 0 0 1 19.62 188.39Z" />
        <path id="eyes-and-nose" d="M180.77 205.76c0 23.64 12.84 42.81 28.68 42.81s28.68-19.17 28.68-42.81-12.84-42.82-28.68-42.82-28.68 19.17-28.68 42.82M275 205.76c0 23.64 12.84 42.81 28.68 42.81s28.68-19.17 28.68-42.81-12.84-42.82-28.68-42.82S275 182.11 275 205.76M264.51 276.85s-29.26 43.53-20.12 49.23c7.07 4.41 20.49-16.71 20.49-16.71s12.82 22.58 16.76 20c16.24-10.71-17.13-52.5-17.13-52.5"/>
        <path id="jawline" class="favicon-stroke" fill="none" stroke-linecap="round" d="M114.92 284.33c22.54-1 22 7 22 62.48" />
  </g>
</svg>
```

### Step 02 > 创建 ICO 文件

将 Step 01 中的 `icon.svg` 转换为 `32x32` 尺寸的 `favicon.ico` 文件。

### Step 03 > 创建 PNG 文件

将 Step 01 中的 `icon.svg` 转换为 `512x512` 和 `192x192` 尺寸的 PNG 文件。

将 Step 01 中的 `icon.svg` 中的图像本身调整为 `140x140` 尺寸，图像的画布调整为 `180x180` 导出尺寸为 `180x180` 的 PNG 文件，作为 Apple touch icon 使用。

### Step 04 > 优化文件大小

使用你喜欢的工具在保证图像质量的前提下尽可能的压缩文件大小，推荐使用 Google 开源的 [Squoosh](https://squoosh.app/) 图像压缩工具，网站、免费、可离线使用。

## 参考

- [How to Favicon in 2024: Six files that fit most needs](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs)