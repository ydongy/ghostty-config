<div align="center">

# ghostty-config

一份 macOS 上的 Ghostty 终端配置，为配合 Claude Code 使用而调整。

[![CI](https://github.com/ydongy/ghostty-config/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/ydongy/ghostty-config/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
![Platform: macOS](https://img.shields.io/badge/platform-macOS-lightgrey)

[English](README.md) · **简体中文**

</div>

## 功能

- **Cmd + D** 在右侧新建一个分屏，例如一边写代码、一边调试。
- **Cmd + Shift + Enter**（或 **Cmd + Shift + F**）把当前分屏放大到整个窗口，例如查看较长的 Claude Code
  输出，再按一次恢复。
- Catppuccin Mocha 主题，半透明毛玻璃背景（不透明度 0.85，模糊半径 30），透明标题栏。
- Maple Mono NF CN 字体，14 号，行高略增。
- 重启后恢复窗口和分屏（`window-save-state = always`）。
- 快速终端：从鼠标所在屏幕的顶部弹出，失去焦点后自动隐藏。
- 粘贴保护、命令结束时的通知，以及较大的回滚缓冲区。
- 可与 Starship 提示符配合使用；Starship 需另行安装和配置。

## 环境要求

- macOS，并已安装 [Ghostty](https://ghostty.org)。快捷键使用 Cmd，部分选项仅在 macOS 上生效。
- Maple Mono NF CN 字体，需另行安装；未安装时 Ghostty 会改用其他字体。
- 登录 shell 为 zsh（配置中设置了 `shell-integration = zsh`）。
- 使用 Makefile 安装时需要 `make`。

## 快速开始

`make install` 会覆盖 `~/.config/ghostty/config`。如已有配置，请先备份。

```sh
git clone https://github.com/ydongy/ghostty-config.git
cd ghostty-config
make install
```

然后在 Ghostty 中按 **Cmd + Shift + ,** 重新加载配置。

不使用 `make` 时，手动把 `config` 文件复制到 `~/.config/ghostty/config`。

## 使用

```sh
make            # 列出可用目标
make install    # 把 config 安装到 ~/.config/ghostty/config
make uninstall  # 删除 ~/.config/ghostty/config
```

`PREFIX`（默认 `~/.config`）和 `DESTDIR` 可修改安装位置，例如 `make install PREFIX=/tmp/test`。

建议搭配的工具：

```sh
brew install --cask claude-code
brew install starship fastfetch btop
```

如需在每个新窗口中启动 Claude Code，取消 `config` 中 `initial-command` 一行的注释，并确认路径与本机安装位置一致
（`which claude`）。

## 开发

```sh
make -n install                    # 检查 Makefile 目标能否解析
make install PREFIX="$(mktemp -d)" # 安装到临时目录
/Applications/Ghostty.app/Contents/MacOS/ghostty +validate-config --config-file=config
```

最后一条命令需要 macOS 上的 Ghostty；CI 只运行 Makefile 检查。

## 参与贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 安全

见[安全策略](https://github.com/ydongy/ghostty-config/security/policy)。请不要在公开 issue 中报告漏洞。

## 致谢

本仓库 fork 自 BruceBlue 的 [BruceLanLan/ghostty-config](https://github.com/BruceLanLan/ghostty-config)，原始配置由其编写。

## 许可证

[MIT](LICENSE)
