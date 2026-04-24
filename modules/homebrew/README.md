# homebrew

Initializes Homebrew shell environment.

## What It Does

- Sets `PATH`, `MANPATH`, `INFOPATH`, and other Homebrew-related environment variables.
- Output is hard-coded from `brew shellenv` for faster shell startup (avoids spawning a subprocess).

## Prerequisites

- Homebrew installed at `/opt/homebrew` (Apple Silicon default).

## Maintenance

If Homebrew's prefix changes (e.g. switching between Apple Silicon and Intel), regenerate the environment variables by running `brew shellenv` and updating the `init` file with the output.
