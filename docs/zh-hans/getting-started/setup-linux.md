---
title: 在 Linux 中安装
---

import Alert from '@theme/Alert'
import Icon from '@theme/Icon'
import { Intro } from '@theme/SetupDocs'
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Intro />

## 1. 系统依赖&nbsp;<Icon title="alert" color="danger"/>

<Tabs
defaultValue="debian"
values={[
{label: 'Debian', value: 'debian'},
{label: 'Arch', value: 'arch'},
{label: 'Fedora', value: 'fedora'},
]}>
<TabItem value="debian">

```sh
$ sudo apt update && sudo apt install libwebkit2gtk-4.0-dev \
    build-essential \
    curl \
    wget \
    libssl-dev \
    libgtk-3-dev \
    libappindicator3-dev \
    patchelf \
    librsvg2-dev
```

</TabItem>
<TabItem value="arch">

```sh
$ sudo pacman -Syy && sudo pacman -S  webkit2gtk \
    base-devel \
    curl \
    wget \
    openssl \
    appmenu-gtk-module \
    gtk3 \
    libappindicator-gtk3 \
    patchelf \
    librsvg \
    libvips
```

</TabItem>
<TabItem value="fedora">

```sh
$ sudo dnf check-update && sudo dnf install webkit2gtk3-devel.x86_64 \
    openssl-devel \
    curl \
    wget \
    libappindicator-gtk3 \ #
    patchelf \
    librsvg2-devel \
    && sudo dnf group install "C Development Tools and Libraries"
```

</TabItem>
</Tabs>



### 可选依赖:

- `libappindicator`: 使用系统托盘功能时需要。
- `patchelf` and `librsvg`: 构建 `AppImage` 时需要。

## 2. Node.js 和包管理工具&nbsp;<Icon title="control-skip-forward" color="warning"/>

### Node.js (包含 npm)

我们建议使用 **nvm** 来管理你的 Node.js。它允许你轻松切换版本和更新 Node.js。

```sh
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
```

<Alert title="Note">
我们已经审计了这个 bash 脚本，它做了它所说的事情。尽管如此，在盲目的 curl-bashing 一个脚本之前，先看看它总是明智的，这是该文件的[下载链接](https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh)。 *该链接可能需要翻墙*
</Alert>

nvm 安装完毕，关闭并重新打开你的终端，然后安装最新版本的 Node.js 和 npm。

```sh
$ nvm install node --latest-npm
$ nvm use node
```

如果你在使用nvm时有任何问题，请查看 [project readme](https://github.com/nvm-sh/nvm)

### 可选的 Node.js 包管理器

你也可以使用npm的替代品：

- [Yarn](https://yarnpkg.com/getting-started)，是 Tauri 团队推荐的
- [pnpm](https://pnpm.js.org/en/installation)

## 3. Rustc and Cargo 包管理器&nbsp;<Icon title="control-skip-forward" color="warning"/>

下面的命令将安装 [rustup](https://rustup.rs/)，即 [Rust](https://www.rust-lang.org/) 的官方安装程序。

```bash
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

<Alert title="Note">
我们已经审计了这个 bash 脚本，它做了它所说的事情。尽管如此，在盲目的 curl-bashing 一个脚本之前，先看看它总是明智的，这是该文件的[下载链接](https://sh.rustup.rs)。
</Alert>

查看 Rust 是否被成功安装，请运行以下命令：

```sh
$ rustc --version
latest update on 2019-12-19, rust version 1.40.0
```

如果该命令不起作用，你可能需要重新启动你的终端。

## 4. 对于 Windows 的 Linux 子系统（WSL）用户&nbsp;<Icon title="info-alt" color="info"/>

为了在 WSL 中运行图形化的应用程序，你需要下载这些 **Xming**、**Cygwin X**、**vcXsrv** 的一个。
**vcXsrv** 已经在内部使用，所以我们推荐安装它。

### WSL 版本 1

启动 X 服务，然后在终端运行 `export DISPLAY=:0`。现在你应该能够通过终端运行任何图形化的应用程序。

### WSL 版本 2

你需要运行一个比 WSL 1 稍微复杂的命令：`export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0`，你需要在 X 服务上添加 `-ac` 参数。**注意：如果由于某种原因，这个命令不能工作，你可以使用其他命令，如。`export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | sed 's/.* //g'):0` 或者你可以使用 `cat /etc/resolve.conf | grep nameserver` 手动找到地址**。

<Alert type="info" title="Note">

不要忘了，当你想使用一个图形化的应用程序时，你必须对每个新打开的终端使用 `export` 命令。<br/>你可以用 `sudo apt-get install x11-apps` 下载一些例子来试试。在排除WSL问题时，它可以很方便。

You can download some examples to try with `sudo apt-get install x11-apps`. xeyes is always a good one. It can be handy when troubleshooting WSL issues.
</Alert>

## 接下来

现在你已经在 Linux 中为 Tauri 安装了相关依赖，学习如何将 [Tauri 添加到你的项目中](/docs/usage/development/integration)
