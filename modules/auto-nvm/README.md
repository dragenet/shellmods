# auto-nvm

Automatically switches Node.js versions when changing directories, based on `.nvmrc` files.

## What It Does

- Registers a `chpwd` hook that runs on every directory change.
- If a `.nvmrc` file is found in the new directory (or a parent), switches to the specified Node.js version.
- If the required version is not installed, runs `nvm install` automatically.
- When leaving a directory with `.nvmrc`, reverts to the nvm default version.

## Dependencies

- **Requires the `nvm` module to be enabled.** This module depends on nvm functions (`nvm_find_nvmrc`, `nvm use`, etc.) being available in the session.

## Prerequisites

- nvm installed at `~/.nvm`.
- The `nvm` shell module enabled before this one in the load order.
