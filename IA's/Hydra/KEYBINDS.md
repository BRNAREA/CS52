# Keybinds

Diogo Silva edited this page May 21, 2023 · [9 revisions](https://github.com/HydraVim/HydraVim/wiki/Keybinds/_history)

## Keybinds abbreviation

[](https://github.com/HydraVim/HydraVim/wiki/Keybinds#keybinds-abbreviation)

|Abbreviation|Description|
|---|---|
|`C`|Ctrl|
|`S`|Shift|
|`A`|Alt|
|`<leader>`|Space|

## Modes

[](https://github.com/HydraVim/HydraVim/wiki/Keybinds#modes)

|Mode|Description|
|---|---|
|`n`|normal|
|`i`|insert|
|`v`|visual|
|`t`|terminal|

## Table of keybinds

[](https://github.com/HydraVim/HydraVim/wiki/Keybinds#table-of-keybinds)

Remember that keybinds are case sensitive

| Keybinds       | Description                             | Mode          |
| -------------- | --------------------------------------- | ------------- |
| `C-q`          | Close the current buffer                | `n`, `i`, `v` |
| `C-s`          | Save changes                            | `n`           |
| `C-w`          | Close the current buffer                | `n`           |
| `C-h`          | Move cursor to the left buffer          | `n`           |
| `C-l`          | Move cursor to the right buffer         | `n`           |
| `C-k`          | Move cursor to the up buffer            | `n`           |
| `C-j`          | Move cursor to the down buffer          | `n`           |
| `C-z`          | Undo changes                            | `n`, `v`      |
| `C-r`          | Redo changes                            | `n`, `v`      |
| `C-c`          | Copy selected text                      | `v`           |
| `C-v`          | Paste text                              | `n`, `v`      |
| `C-a`          | Select all text                         | `n`, `v`      |
| `A-i`          | Toggle a floating terminal              | `n`, `t`      |
| `A-h`          | Toggle a horizontal terminal            | `n`, `t`      |
| `A-m`          | Toggle a vertical terminal              | `n`, `t`      |
| `S-j`          | Copy the current line down              | `n`, `v`      |
| `S-k`          | Copy the current line up                | `n`, `v`      |
| `A-n`          | Split the buffer vertically             | `n`           |
| `A-b`          | Split the buffer horizontally           | `n`           |
| `A-k`          | Move selected line or text down         | `n`           |
| `A-j`          | Move selected line or text up           | `n`           |
| `C-A-h`        | Resize the vertical buffer to the left  | `n`           |
| `C-A-l`        | Resize the vertical buffer to the right | `n`           |
| `C-A-k`        | Resize the vertical buffer to the up    | `n`           |
| `C-A-j`        | Resize the vertical buffer to the down  | `n`           |
| `A-S-s`        | Save the current session                | `n`           |
| `A-S-l`        | Load the last saved version             | `n`           |
| `<leader>sp`   | Convert current text to snippet         | `v`           |
| `<leader>e`    | Toggle from file explorer               | `n`           |
| `<leader>ff`   | Open file search                        | `n`           |
| `<leader>gc`   | Browse the commit history               | `n`           |
| `<leader>gb`   | Browse the branch                       | `n`           |
| `<leader>p`    | Pin the current buffer                  | `n`           |
| `<TAB>`        | Switch to next tab                      | `n`           |
| `<S-TAB>`      | Switch to previous tab                  | `n`           |
| `<TAB>`        | Add tab on all selected rows            | `v`           |
| `<S-TAB>`      | Remove tab on all selected rows         | `v`           |
| `C-A-PageUp`   | Move the tab to the next position       | `n`           |
| `C-A-PageDown` | Move tab to previous position           | `n`           |
| `<leader>`     | Pop up with other HydraVim functions    | `n`           |