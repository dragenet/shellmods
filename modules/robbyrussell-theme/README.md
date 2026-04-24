# robbyrussell-prompt

The robbyrussell prompt theme extracted from Oh My Zsh.

## What It Does

Sets up the classic robbyrussell zsh prompt with git branch and dirty-state indicators.

- Green arrow `➜` for successful last command, red for failure.
- Current directory name in cyan.
- Git branch name in red with blue `git:()` wrapper.
- Yellow `✗` when the working tree is dirty.

## Prompt Appearance

```
➜ my-project git:(main) ✗
```

## Prerequisites

None — this module is self-contained. It does not depend on the git-aliases module.
