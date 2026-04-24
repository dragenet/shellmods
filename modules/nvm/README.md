# nvm

Initializes Node Version Manager (nvm) for the shell session using lazy loading.

## What It Does

- Exports `NVM_DIR` pointing to `~/.nvm`.
- Defines lightweight wrapper functions for `nvm`, `node`, `npm`, and `npx`.
- On first invocation of any of these commands, loads the full nvm script and bash completions, then runs the original command.
- This lazy-loading approach avoids the ~300ms startup cost of sourcing nvm on every shell launch.

## Prerequisites

- nvm installed at `~/.nvm`. Install via `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`.

## See Also

- `auto-nvm` -- optional companion module that auto-switches Node.js versions on directory change.
