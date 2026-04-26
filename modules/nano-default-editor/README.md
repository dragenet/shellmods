# nano-default-editor

Sets `nano` as the default text editor.

## What It Does

- Exports `EDITOR=nano` for both local and remote (SSH) sessions.
- Exports `VISUAL=nano` for both local and remote (SSH) sessions.

## Notes

Mutually exclusive with `vim-default-editor` and `nvim-default-editor`. Enable only one editor module at a time.
