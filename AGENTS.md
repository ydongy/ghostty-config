# AGENTS.md

## What it is

A Ghostty terminal configuration for macOS, set up for working with Claude Code: split and zoom key bindings, the
Catppuccin Mocha theme with a translucent background, and a Makefile that installs it. MIT licensed. A fork of
`BruceLanLan/ghostty-config`. `CLAUDE.md` is the single line `@AGENTS.md`; put nothing else in it and keep no
other agent file.

## Layout

```
config              the Ghostty configuration (installed as ~/.config/ghostty/config)
Makefile            install, uninstall and help targets; PREFIX and DESTDIR change the location
README.md           English README; README.zh-CN.md is the Chinese one
.github/workflows/  ci.yml (Makefile checks), pr-title.yml (Conventional Commits title)
```

## Commands

```sh
make -n install                    # check that the Makefile targets parse
make install PREFIX="$(mktemp -d)" # install into a temporary directory
/Applications/Ghostty.app/Contents/MacOS/ghostty +validate-config --config-file=config   # macOS with Ghostty only
```

Never run `make install` without `PREFIX` while testing: it overwrites the user's `~/.config/ghostty/config`.

## Conventions

- Commit messages and PR titles use Conventional Commits: `feat|fix|docs|refactor|perf|test|build|ci|chore|revert(scope)!: subject`.
  Branches are `<type>/<issue>-<slug>`. Open an issue first for large changes; the PR body says `Closes #<n>`;
  squash merge by the maintainer.
- Every option in `config` must be a real Ghostty option; check it with `+validate-config` and the Ghostty
  documentation. Do not invent options or key binding actions.
- `README.md` and `README.zh-CN.md` have the same structure and facts; change both together. Describe features
  factually. A README feature that depends on `config` must match it.
- User-visible changes go under `## [Unreleased]` in `CHANGELOG.md`.

## Issues and pull requests

`gh issue create` and `gh pr create --body` skip the issue forms and the pull request template, so write their
structure yourself. Search open issues first; one issue is one problem.

- Issue title: one short sentence that says the problem or the outcome, in English or Simplified Chinese. No type
  prefix such as `[feat]`; the label carries the type.
- Bug, `--label bug`: `## What happened`, `## What you expected`, `## Steps to reproduce`,
  `## Version and environment`.
- Feature or improvement, `--label enhancement`: `## Problem`, `## Proposed solution`,
  `## Alternatives considered` (when there were any), `## Done when`.
- Documentation, `--label documentation`: `## Where`, `## What is missing, unclear or wrong`, `## Suggested change`.
- Pull request: the title is the Conventional Commits subject (it becomes the squash commit). The body has
  `## Summary` (what changes and why), `## Related issue` (`Closes #<n>`), `## How tested` (the commands run and
  their results, and what was not run) and `## Checklist`:
  `- [ ] PR title follows Conventional Commits`, `- [ ] Tests pass`,
  `- [ ] Documentation updated where behavior changed`, ticked only when true.

## Red lines

- Credentials never appear in pull requests, issues, logs or chat.
- Releases, signing and anything sent to an external service need the maintainer's confirmation.
- Review the staged file list before committing; no blind `git add -A` of unknown files.
- Do not overwrite or delete the user's own Ghostty configuration outside a test `PREFIX`.
