# oh-my-zsh

Initializes the Oh My Zsh framework.

## What It Does

- Exports `ZSH` pointing to the Oh My Zsh installation directory.
- Sets the theme to `robbyrussell`.
- Loads the `git` plugin.
- Sources the Oh My Zsh entry point.
- Includes all default OMZ configuration options (commented out) for easy customization.

## Configuration

Edit `init` to change:
- `ZSH_THEME` -- see [Oh My Zsh Themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes).
- `ZSH_THEME_RANDOM_CANDIDATES` -- restrict random theme selection.
- `plugins` -- see [Oh My Zsh Plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins).
- `CASE_SENSITIVE` / `HYPHEN_INSENSITIVE` -- completion matching behavior.
- `zstyle ':omz:update'` -- auto-update mode and frequency.
- `DISABLE_MAGIC_FUNCTIONS` -- fix URL pasting issues.
- `DISABLE_LS_COLORS` -- toggle ls colors.
- `DISABLE_AUTO_TITLE` -- toggle terminal title auto-setting.
- `ENABLE_CORRECTION` -- toggle command auto-correction.
- `COMPLETION_WAITING_DOTS` -- show dots during completion.
- `DISABLE_UNTRACKED_FILES_DIRTY` -- speed up VCS status in large repos.
- `HIST_STAMPS` -- history timestamp format.
- `ZSH_CUSTOM` -- custom folder path.
- `LANG` -- language environment.
- `ARCHFLAGS` -- compilation flags.

## Prerequisites

- Oh My Zsh installed at `~/.oh-my-zsh`. Install via `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`.
