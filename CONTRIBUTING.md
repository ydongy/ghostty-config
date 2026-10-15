# Contributing

Issues and pull requests are welcome. Read [AGENTS.md](AGENTS.md) for the full set of repository rules.

## Before you start

- Issues and pull requests may be written in English or Simplified Chinese. 欢迎用中文或英文提 issue 和 PR。
- Open an issue before a large change, such as a new theme or a different set of key bindings, so we can agree on
  the direction first. Small fixes can go straight to a pull request.
- Do not report vulnerabilities in public issues; see the
  [security policy](https://github.com/ydongy/ghostty-config/security/policy).

## Development setup

Requirements: macOS with Ghostty for trying the configuration, and `make`.

```sh
make -n install                    # check that the Makefile targets parse
make install PREFIX="$(mktemp -d)" # install into a temporary directory
/Applications/Ghostty.app/Contents/MacOS/ghostty +validate-config --config-file=config
```

Run all three before opening a pull request. CI runs the Makefile checks; it cannot run Ghostty, so run
`+validate-config` locally and say in the pull request that you did.

## Commits, branches and pull requests

- Commit messages and pull request titles follow [Conventional Commits](https://www.conventionalcommits.org/):
  `feat|fix|docs|refactor|perf|test|build|ci|chore|revert(scope)!: subject`.
- Name branches `<type>/<issue>-<slug>`, for example `feat/12-tab-keybinds`.
- Link the issue with `Closes #<n>`. The maintainer squash-merges, so the pull request title becomes the commit
  message. No DCO or sign-off is required.
- `README.md` (English) and `README.zh-CN.md` (Chinese) say the same thing; change both together.
- If users would notice a change, add a line under `## [Unreleased]` in `CHANGELOG.md`.

## License

Contributions are licensed under the [MIT License](LICENSE).
