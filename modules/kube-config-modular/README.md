# kube-config-modular

Splits kubeconfig into one file per cluster and merges them via `KUBECONFIG`.

## What It Does

- Always includes the default `~/.kube/config` (if present), then scans `~/.kube/config.d/<cluster-name>/config` using a zsh glob (no subprocess, non-blocking).
- Joins all matching paths with `:` and exports them as `KUBECONFIG`, so `kubectl` merges them in memory.
- If no per-cluster configs exist, leaves `KUBECONFIG` untouched.

## Usage

Split your existing `~/.kube/config` into per-cluster files:

```sh
mkdir -p ~/.kube/config.d/<cluster-name>
mv ~/.kube/config ~/.kube/config.d/<cluster-name>/config
```

Add more clusters the same way — each gets its own directory with a `config` file inside.

## Prerequisites

- `kubectl` (or any tool respecting `KUBECONFIG`).
- Per-cluster config files placed at `~/.kube/config.d/<cluster-name>/config`.
