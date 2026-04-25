# ShellMods

Modular zsh configuration for macOS. Instead of a growing `.zshrc`, each piece of shell config lives in its own module — a self-contained directory with an `init` entrypoint. Modules are activated by symlinking them into `enabled/`, so you can toggle features per machine without touching config files.

## Setup

1. Clone the repo:
   ```sh
   git clone https://github.com/dragenet/shellmods.git ~/.shellmods
   ```

2. Run bootstrap:
   ```sh
   ~/.shellmods/bootstrap
   ```
   This creates `enabled/`, appends the init snippet to `~/.zshrc`, and enables the `shellmods` CLI.

3. Enable the modules you need:
   ```sh
   shellmods enable homebrew nvm auto-nvm git-aliases
   ```

4. Restart your shell or run `source ~/.zshrc`.

## Managing Modules

```sh
shellmods list              # show all available modules
shellmods enabled           # show currently enabled modules
shellmods enable <module>   # enable one or more modules
shellmods disable <module>  # disable one or more modules
shellmods enable --all      # enable everything
shellmods disable --all     # disable everything
```

Shorthand: `shm` = `shellmods`, `shme` = enable, `shmd` = disable.

## Available Modules

| Module | Description |
|--------|-------------|
| `alias-yarn` | Shorthand aliases for Yarn commands |
| `android-home` | Android SDK environment (`ANDROID_HOME`, `adb`, emulator, etc.) |
| `auto-nvm` | Auto-switches Node.js version on `cd` via `.nvmrc` (requires `nvm`) |
| `bun` | Bun runtime environment |
| `defer` | `zsh-defer` for deferred initialization — load before modules that use it |
| `docker-completions` | Docker CLI tab completions |
| `git-aliases` | Comprehensive git aliases and helpers (extracted from Oh My Zsh) |
| `homebrew` | Homebrew shell environment (hard-coded output for fast startup) |
| `inteli-history` | Up/down arrow searches history by current input prefix |
| `java-home` | Sets `JAVA_HOME` to Azul Zulu JDK 17 |
| `lazygit` | `lg` alias for lazygit |
| `local-bin` | Adds `~/.local/bin` to `$PATH` |
| `nano-default-editor` | Sets `nano` as `$EDITOR` |
| `nvm` | Lazy-loads Node Version Manager (avoids ~300ms startup cost) |
| `pg-client` | PostgreSQL client tools via Homebrew libpq |
| `rbenv` | Lazy-loads rbenv for Ruby version management |
| `robbyrussell-theme` | Classic robbyrussell prompt with git status indicators |
| `shellmods-cli` | The `shellmods` management CLI (enabled automatically by bootstrap) |
| `vim-default-editor` | Sets `vim` as `$EDITOR` |
| `windsurf` | Adds Windsurf (Codeium) editor CLI to `$PATH` |
| `zsh-completion` | Centralized `compinit` with deferred loading and dump caching |

Each module has its own `README.md` with prerequisites and configuration notes.

## Contributing

See [AGENTS.md](AGENTS.md) for module conventions, the multi-file module pattern, and how to add a new module.
