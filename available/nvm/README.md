# nvm

Initializes Node Version Manager (nvm) for the shell session.

## What It Does

- Exports `NVM_DIR` pointing to `~/.nvm`.
- Sources the nvm script to make `nvm` commands available.
- Loads nvm bash completions.

## Prerequisites

- nvm installed at `~/.nvm`. Install via `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`.

## See Also

- `auto-nvm` -- optional companion module that auto-switches Node.js versions on directory change.
