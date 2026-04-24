# docker-completions

Enables Docker CLI tab completions in zsh.

## What It Does

- Adds `~/.docker/completions` to the zsh `fpath`.
- Completion initialization (`compinit`) is handled centrally by the `oh-my-zsh` module.

## Prerequisites

- Docker Desktop installed (provides completion files at `~/.docker/completions`).
