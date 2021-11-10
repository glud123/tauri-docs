---
title: 简介
---

import OSList from '@theme/OSList'

欢迎使用 Tauri!

Tauri 是一个跨语言的通用系统，具有很高的组合性，允许工程师开发各种各样的应用。她使用 [Rust](https://www.rust-lang.org/) 工具和在 Webview 中渲染HTML 相结合构建桌面应用。Tauri构建的应用可以用任意数量的 JS API / Rust API 组合，使 Webview 可以通过消息控制整个系统。

任何可以在网站上显示东西，都可以在 Tuari 中显示！

开发人员可以自由地通过Tauri用他们选择的任何网络框架来构建显示在 Webview 中的前端页面!
**开发人员甚至可以用他们自己的功能来扩展默认的API**，并轻松地连接 Webview 和基于 Rust 的后端！

该架构在[架构](https://github.com/tauri-apps/tauri/blob/dev/ARCHITECTURE.md)中有更全面的描述。

本指南将帮助你创建你的第一个 Tauri 应用。它应该只需要10分钟左右，如果你有一个较慢的网络连接，它可能需要更长的时间。

如果你发现一个错误或不清楚的地方，或想提出一个改进意见，你有几个选择。

1.  在 [Github Repo](https://github.com/tauri-apps/tauri-docs) 上打开一个 issue
2. 访问 [Discord 服务器](https://discord.gg/tauri)并提出你的问题
3. 要求加入 Discord 上的教育工作组，以获得其讨论频道的访问权。

## 步骤

1. 安装和配置系统的先决条件
2. 用你选择的前端框架创建一个 Web 应用
3. 使用 Tauri CLI 在你的应用程序中设置 Tauri
4. 编写本地 Rust 代码以增加功能或提高性能（完全可选）
5. 使用 `tauri dev` 来开发你的应用程序，如热模块重载和 webview devtools 等功能
6. 使用`tauri build`将你的应用程序打包成一个安装程序

### 设置你的环境

在创建应用之前，你必须安装和配置一些开发工具。本指南假定您熟悉命令行，知道如何在操作系统中安装软件，并了解软件开发。

选择对应平台的指南开始：

<OSList content={{
    linux: { title: 'Linux Setup', link: '/docs/getting-started/setup-linux'},
    macos: { title: 'macOS Setup', link: '/docs/getting-started/setup-macos'},
    windows: { title: 'Windows Setup', link: '/docs/getting-started/setup-windows'}
}} />

接下来，您可以将 [Tauri 添加到您的项目中](docs/usage/development/integration)
