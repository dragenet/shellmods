# shellmods-cli

Adds the `shellmods` management CLI to `$PATH` and provides shorthand aliases.

## Commands

| Command              | Description                  |
|----------------------|------------------------------|
| `shellmods`          | Show usage and list modules  |
| `shellmods enable`   | Enable a module              |
| `shellmods disable`  | Disable a module             |

## Aliases

| Alias  | Command             |
|--------|---------------------|
| `shm`  | `shellmods`         |
| `shme` | `shellmods enable`  |
| `shmd` | `shellmods disable` |

## Notes

- This module is enabled by default after running `bootstrap`.
- The CLI script lives at `$SHELLMODS_HOME/bin/shellmods`.
