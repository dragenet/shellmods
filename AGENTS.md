# AGENTS.md

## Overview

Modularized zsh configuration repo. Uses Oh My Zsh as the base framework.
`zshrc` is a pure bootstrap -- it only sets `SHELLMODS_PATH` and sources `shellmods_init`.
All configuration lives in shell modules under `available/`.

## Repo Structure

```
zshrc              # Bootstrap: sets SHELLMODS_PATH, sources shellmods_init
shellmods_init     # Iterates over enabled modules and sources their init files
available/         # All available shell modules (not all necessarily active)
  <module-name>/
    init           # Entrypoint sourced by shellmods_init
    [component]    # Optional component files sourced by init
```

## How It Works

- `zshrc` sets `SHELLMODS_PATH=~/.zshrc.d` and sources `shellmods_init` from that path.
- `shellmods_init` iterates over directories in `$SHELLMODS_PATH/enabled/` and sources the `init` file in each.
- Modules are activated by symlinking directories from `available/` into an `enabled/` directory (not tracked in this repo).

## Creating a New Module

1. Create a new directory under `available/` with a descriptive kebab-case name:
   ```
   mkdir available/my-module
   ```
2. Create an `init` file inside it with the shell code to be sourced:
   ```
   touch available/my-module/init
   ```
3. The `init` file is sourced directly into the zsh session. Use it for `export`, `alias`, `eval`, or function definitions.
4. To enable the module, symlink the directory into `enabled/`:
   ```
   ln -s ~/.zshrc.d/available/my-module ~/.zshrc.d/enabled/my-module
   ```

### Multi-File Modules

When a module has multiple distinct responsibilities, split them into separate component files and source them from `init`. Each component should handle a single concern.

Use `${0:a:h}` to resolve the module directory path relative to `init`.

Example (`auto-nvm`):
```
available/auto-nvm/
  init             # Sources components in order
  nvm-setup        # Initializes nvm and bash completion
  auto-switch      # Hooks into chpwd to auto-switch node versions
```

`init` contents:
```zsh
source "${0:a:h}/nvm-setup"
source "${0:a:h}/auto-switch"
```

Use this pattern whenever a module would otherwise mix concerns (e.g. tool init + shell hooks, env setup + aliases).

## Module Conventions

- Each module is a directory containing an `init` entrypoint file.
- Each module should follow single responsibility -- one tool, one concern.
- Directory names use lowercase kebab-case (e.g. `auto-nvm`, `java-home`, `alias-yarn`).
- The `init` file must be a valid zsh script -- it is sourced, not executed.
- No secrets or credentials should be stored in modules.
- This repo targets macOS with zsh.
- `zshrc` must stay minimal (bootstrap only). New config goes into modules.
