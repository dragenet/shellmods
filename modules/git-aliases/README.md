# git-aliases

Git aliases and helper functions extracted from the Oh My Zsh git plugin.

## What It Does

Provides a comprehensive set of short aliases for common git commands and helper functions for branch management.

### Key Functions

- `git_main_branch` — Detects the main branch name (main, master, trunk, etc.).
- `git_develop_branch` — Detects the develop branch name.
- `git_current_branch` — Returns the current branch name.
- `grename` — Renames a branch locally and on origin.
- `work_in_progress` — Checks if the last commit is a WIP commit.

### Common Aliases

| Alias | Command |
|-------|---------|
| `g`   | `git` |
| `gst` | `git status` |
| `ga`  | `git add` |
| `gc`  | `git commit --verbose` |
| `gd`  | `git diff` |
| `gco` | `git checkout` |
| `gb`  | `git branch` |
| `gl`  | `git pull` |
| `gp`  | `git push` |
| `glo` | `git log --oneline --decorate` |
| `gm`  | `git merge` |
| `grb` | `git rebase` |

See the `init` file for the full list of aliases.

## Prerequisites

None — this module is self-contained.

## Source

https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git
