---
title: Neovim command
created: 2026-07-09
tags: [programming, editor, neovim]
---

# Neovim command

## Notes

### Normal command

- ⎵ - list all command
- ⎵ + e - search
- :.,+4s/\s\+$// - delete last space from current line to next four lines
- :-7s/\s\+$// - delete end of space on line -7 from current cursor

### Telescope

- ⎵ + f + f - search file
- ⎵ + s + k - all key binding

### Buffer line

- :bd - unload the current file
- :bn - next tab
- :bp - previous tab

### Flash

- s + str - to search all string and choose character in red
- f + char - find the charactor and use semicolon (;) to go forward or comma (,) to go backward

### Lazyvim

- [All key binding](https://github.com/LazyVim/LazyVim/blob/main/lua/lazyvim/config/keymaps.lua)
