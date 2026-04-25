# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A modular zsh configuration system. `~/.zshrc` is kept minimal — it only sets `SHELLMODS_HOME` and sources `shellmods_init`. All shell configuration lives in self-contained modules under `modules/`. The `enabled/` directory (not tracked) holds symlinks to active modules, which `shellmods_init` iterates over and sources at shell startup.

## Key Files

- `shellmods_init` — iterates `enabled/*` and sources each file into the zsh session
- `bootstrap` — appends the init snippet to `~/.zshrc` and creates `enabled/`
- `bin/shellmods` — CLI for managing modules (enable/disable/list); sourced (not executed) by the `shellmods` function in `modules/shellmods-cli/init`

## Managing Modules

```sh
shellmods list                     # list all available modules
shellmods enabled                  # list currently enabled modules
shellmods enable <module>          # enable one or more modules
shellmods enable --all             # enable all modules
shellmods disable <module>         # disable one or more modules
shellmods disable --all            # disable all modules
```

Shorthand aliases: `shm` = `shellmods`, `shme` = `shellmods enable`, `shmd` = `shellmods disable`.

Manually enabling a module: `ln -s $SHELLMODS_HOME/modules/<name>/init $SHELLMODS_HOME/enabled/<name>`

## Module Conventions

- Each module is a directory under `modules/` with an `init` entrypoint and a `README.md`
- `init` is sourced directly into zsh — use it for `export`, `alias`, `eval`, or function definitions
- Directory names use lowercase kebab-case (e.g. `auto-nvm`, `java-home`, `alias-yarn`)
- Single responsibility: one tool or concern per module
- Use `${0:a:h}` to resolve paths relative to the `init` file
- This repo targets macOS with zsh
- `~/.zshrc` must stay minimal (bootstrap only) — new config always goes into modules
- `zshrc` is not tracked in this repo; it is managed per machine
- No secrets or credentials in modules

## Multi-File Modules

When a module has multiple distinct responsibilities, split them into separate component files and source them from `init`. Each component handles a single concern.

```
modules/my-module/
  init        # Sources components in order
  setup       # Tool initialization
  hooks       # Shell hooks
  README.md
```

`init` contents:
```zsh
source "${0:a:h}/setup"
source "${0:a:h}/hooks"
```

Use this pattern whenever a module would otherwise mix concerns (e.g. tool init + shell hooks, env setup + aliases).

## Adding a New Module

1. Create a directory under `modules/` with a lowercase kebab-case name
2. Create an `init` file with the shell code to be sourced
3. Create a `README.md` describing what the module does, its prerequisites, and any configuration notes
4. Enable it: `shellmods enable my-module`
