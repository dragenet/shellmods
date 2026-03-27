# zsh-config

Modularized zsh configuration built on top of [Oh My Zsh](https://ohmyz.sh/).

Each piece of shell configuration lives in its own module -- a self-contained directory with an `init` entrypoint. Modules are enabled by symlinking them, making it easy to toggle features per machine without editing config files.

## Structure

```
shellmods/
  bootstrap                  # Sets up shellmods in ~/.zshrc and creates enabled/
  shellmods_init             # Sources init from each enabled module
  modules/                   # All modules (see below)
```

At runtime, `SHELLMODS_HOME` points to the `shellmods/` directory. The `enabled/` directory (not tracked) contains symlinks to the modules you want active.

## Available Modules

| Module | Description |
|--------|-------------|
| `alias-yarn` | Shorthand aliases for Yarn commands |
| `android-home` | Android SDK environment setup |
| `auto-nvm` | Auto-switch Node.js versions on `cd` via `.nvmrc` |
| `bun` | Bun runtime and completions |
| `docker-completions` | Docker CLI tab completions |
| `homebrew` | Homebrew shell environment |
| `java-home` | JAVA_HOME for Azul Zulu JDK 17 |
| `local-bin` | Adds `~/.local/bin` to PATH |
| `nano-default-editor` | Sets nano as default EDITOR |
| `nvm` | Node Version Manager initialization |
| `oh-my-zsh` | Oh My Zsh framework, theme, and plugins |
| `pg-client` | PostgreSQL client tools (libpq) |
| `rbenv` | Ruby version management via rbenv |
| `vim-default-editor` | Sets vim as default EDITOR |
| `windsurf` | Windsurf (Codeium) editor CLI |

See each module's `README.md` for details, prerequisites, and configuration options.

## Setup

1. Clone the repo:
   ```sh
   git clone <repo-url> ~/.zsh-config
   ```

2. Run the bootstrap script:
   ```sh
   ~/.zsh-config/shellmods/bootstrap
   ```

   This creates the `enabled/` directory and appends the shellmods init to `~/.zshrc`.

3. Enable the modules you need:
   ```sh
   ln -s $SHELLMODS_HOME/modules/oh-my-zsh $SHELLMODS_HOME/enabled/oh-my-zsh
   ln -s $SHELLMODS_HOME/modules/homebrew $SHELLMODS_HOME/enabled/homebrew
   # ... add more as needed
   ```

4. Restart your shell or run `source ~/.zshrc`.

## Adding a New Module

```sh
mkdir shellmods/modules/my-module
# Create init with your shell config
vi shellmods/modules/my-module/init
# Document it
vi shellmods/modules/my-module/README.md
# Enable it
ln -s $SHELLMODS_HOME/modules/my-module $SHELLMODS_HOME/enabled/my-module
```

See [AGENTS.md](AGENTS.md) for detailed conventions and the multi-file module pattern.
