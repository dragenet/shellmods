# zsh-completion

Centralized zsh completion initialization with deferred loading and caching optimizations.

## What It Does

- **Deduplicates `fpath`** via `typeset -U fpath` to prevent redundant completion directories.
- **Defers `compinit`** using `zsh-defer` (if available from the `defer` module) so completion initialization happens after the first prompt renders, improving perceived startup time.
- **Skips security/freshness checks** with `compinit -C` when deferred, since the dump is validated lazily.
- **Compiles `.zcompdump`** to wordcode format (`.zcompdump.zwc`) for faster subsequent loads.
- **Falls back gracefully** if `zsh-defer` is not available: uses a 24-hour cache strategy that only regenerates the completion dump once per day.

## Why Centralize compinit

Multiple modules may add to `fpath` (e.g. docker-completions), but `compinit` should only be called once. This module should be loaded **after** all modules that modify `fpath`.

## Prerequisites

- Optional: `defer` module for deferred loading (recommended for fastest startup).
