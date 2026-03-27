# AGENTS.md

## Overview

Modularized zsh configuration repo. Uses Oh My Zsh as the base framework.
`~/.zshrc` is a pure bootstrap -- it only sets `SHELLMODS_HOME` and sources `shellmods_init`.
All configuration lives in shell modules under `shellmods/modules/`.

## Repo Structure

```
shellmods/
  bootstrap                  # Sets up shellmods in ~/.zshrc and creates enabled/
  shellmods_init             # Iterates over enabled modules and sources their init files
  modules/                   # All available shell modules (not all necessarily active)
    <module-name>/
      init                   # Entrypoint sourced by shellmods_init
      README.md              # Module documentation
```

## How It Works

- `~/.zshrc` sets `SHELLMODS_HOME` to the `shellmods/` directory and sources `shellmods_init` from that path.
- `shellmods_init` iterates over files in `$SHELLMODS_HOME/enabled/` and sources each one.
- Modules are activated by symlinking module `init` files into `enabled/` (named by module):
  ```
  ln -s $SHELLMODS_HOME/modules/my-module/init $SHELLMODS_HOME/enabled/my-module
  ```
- The `enabled/` directory is not tracked in this repo.

## Creating a New Module

1. Create a new directory under `shellmods/modules/` with a descriptive kebab-case name:
   ```
   mkdir shellmods/modules/my-module
   ```
2. Create an `init` file inside it with the shell code to be sourced:
   ```
   touch shellmods/modules/my-module/init
   ```
3. Create a `README.md` describing what the module does, its prerequisites, and any configuration notes.
4. The `init` file is sourced directly into the zsh session. Use it for `export`, `alias`, `eval`, or function definitions.
5. To enable the module, symlink its `init` file into `enabled/` (named by module):
   ```
   ln -s $SHELLMODS_HOME/modules/my-module/init $SHELLMODS_HOME/enabled/my-module
   ```

### Multi-File Modules

When a module has multiple distinct responsibilities, split them into separate component files and source them from `init`. Each component should handle a single concern.

Use `${0:a:h}` to resolve the module directory path relative to `init`.

Example:
```
shellmods/modules/my-module/
  init             # Sources components in order
  setup            # Tool initialization
  hooks            # Shell hooks
  README.md
```

`init` contents:
```zsh
source "${0:a:h}/setup"
source "${0:a:h}/hooks"
```

Use this pattern whenever a module would otherwise mix concerns (e.g. tool init + shell hooks, env setup + aliases).

## Module Conventions

- Each module is a directory containing an `init` entrypoint and a `README.md`.
- Each module should follow single responsibility -- one tool, one concern.
- Directory names use lowercase kebab-case (e.g. `auto-nvm`, `java-home`, `alias-yarn`).
- The `init` file must be a valid zsh script -- it is sourced, not executed.
- No secrets or credentials should be stored in modules.
- This repo targets macOS with zsh.
- `~/.zshrc` must stay minimal (bootstrap only). New config goes into modules.
- `zshrc` is not tracked in this repo; it is managed per machine.
