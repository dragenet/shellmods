# defer

Provides the `zsh-defer` function for deferring shell commands until after the prompt is displayed.

## What It Does

Sources the [romkatv/zsh-defer](https://github.com/romkatv/zsh-defer) plugin, which allows other modules to defer expensive initialization (e.g. `compinit`) until after the first prompt renders. This improves perceived shell startup time.

## Dependencies

- [romkatv/zsh-defer](https://github.com/romkatv/zsh-defer) — bundled as `zsh-defer.plugin.zsh`.

## Notes

- This module should load **before** any module that calls `zsh-defer`.
- The module name `defer` is chosen to sort early alphabetically in the `enabled/` directory.
