<div align="center">

# ghostty-config

A Ghostty terminal configuration for macOS, set up for working with Claude Code.

[![CI](https://github.com/ydongy/ghostty-config/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/ydongy/ghostty-config/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
![Platform: macOS](https://img.shields.io/badge/platform-macOS-lightgrey)

**English** · [简体中文](README.zh-CN.md)

</div>

## Features

- **Cmd + D** opens a new split to the right, for example code on one side and a debug session on the other.
- **Cmd + Shift + Enter** (or **Cmd + Shift + F**) zooms the current split to fill the window, for example to
  read long Claude Code output, and restores it.
- Catppuccin Mocha theme with a translucent, blurred background (opacity 0.85, blur radius 30) and a transparent
  title bar.
- Maple Mono NF CN font at 14 pt, with extra line height.
- Windows and splits are restored after a restart (`window-save-state = always`).
- A quick terminal that drops down from the top of the screen under the mouse and hides when it loses focus.
- Paste protection, a notification when a command finishes, and a large scrollback buffer.
- Works with the Starship prompt; Starship itself is installed and configured separately.

## Requirements

- macOS with [Ghostty](https://ghostty.org) installed. The key bindings use Cmd and some options are macOS-only.
- The Maple Mono NF CN font, installed separately. Without it Ghostty falls back to another font.
- zsh as the login shell (the configuration sets `shell-integration = zsh`).
- `make`, if you install with the Makefile.

## Quick start

`make install` overwrites `~/.config/ghostty/config`. Back up your current configuration first if you have one.

```sh
git clone https://github.com/ydongy/ghostty-config.git
cd ghostty-config
make install
```

Then reload the configuration in Ghostty with **Cmd + Shift + ,**.

Without `make`, copy the `config` file to `~/.config/ghostty/config` yourself.

## Usage

```sh
make            # list the targets
make install    # install config to ~/.config/ghostty/config
make uninstall  # remove ~/.config/ghostty/config
```

`PREFIX` (default `~/.config`) and `DESTDIR` change the install location, for example
`make install PREFIX=/tmp/test`.

Suggested companion tools:

```sh
brew install --cask claude-code
brew install starship fastfetch btop
```

To start Claude Code in every new window, uncomment the `initial-command` line in `config` and check that the
path matches your installation (`which claude`).

## Development

```sh
make -n install                    # check that the Makefile targets parse
make install PREFIX="$(mktemp -d)" # install into a temporary directory
/Applications/Ghostty.app/Contents/MacOS/ghostty +validate-config --config-file=config
```

The last command needs Ghostty on macOS; CI runs only the Makefile checks.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See the [security policy](https://github.com/ydongy/ghostty-config/security/policy). Do not report
vulnerabilities in public issues.

## Acknowledgements

This repository is a fork of [BruceLanLan/ghostty-config](https://github.com/BruceLanLan/ghostty-config) by
BruceBlue, who wrote the original configuration.

## License

[MIT](LICENSE)
