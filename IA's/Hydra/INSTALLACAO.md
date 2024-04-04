## Installation
# Get started

Diogo Silva edited this page Sep 3, 2023 · [10 revisions](https://github.com/HydraVim/HydraVim/wiki/Get-started/_history)

## Requirements

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#requirements)

- [Neovim](https://neovim.io/) 8.0+
- [Nerd Fonts](https://www.nerdfonts.com/) (optional)

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#installation)

After dependencies setup , execute the command below . Make sure that [Git](https://git-scm.com/) is installed

### Linux/macOS

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#linuxmacos)

Backup of your current nvim

```shell
mv ~/.config/nvim ~/.config/nvim.old
```

Clear cache and data (recommend)

```shell
rm -rf ~/.local/share/nvim
rm -rf ~/.cache/nvim
```

Clone the HydraVim and start Neovim

```shell
git clone https://github.com/HydraVim/HydraVim.git --depth 1 ~/.config/nvim
nvim
```

### Windows - Powershell

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#windows---powershell)

Backup of your current nvim

```powershell
Move-Item $env:LOCALAPPDATA\nvim $env:LOCALAPPDATA\nvim.old
```

Clear data (recommend)

```powershell
Remove-Item -Path $env:LOCALAPPDATA\nvim-data -Recurse -Force
```

Clone the HydraVim and start Neovim

```powershell
git clone https://github.com/HydraVim/HydraVim.git --depth 1 $env:LOCALAPPDATA\nvim
nvim
```

### Using Lua

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#using-lua)

Add this to your `init.lua`, it will remove all your config and install HydraVim.

```lua
vim.fn.delete(vim.fn.stdpath("config"), "rf")
vim.fn.delete(vim.fn.stdpath("cache"), "rf")
vim.fn.delete(vim.fn.stdpath("data"), "rf")
vim.fn.system("git clone --depth 1 https://github.com/HydraVim/HydraVim.git " .. vim.fn.stdpath("config"))
vim.cmd("source $MYVIMRC")
```

## Uninstall

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#uninstall)

### Linux/macOS

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#linuxmacos-1)

```shell
rm -rf ~/.config/nvim
rm -rf ~/.local/share/nvim
rm -rf ~/.cache/nvim
```

### Windows - Powershell

[](https://github.com/HydraVim/HydraVim/wiki/Get-started#windows---powershell-1)

Remove-Item -Path $HOME\AppData\Local\nvim -Force -Recurse
Remove-Item -Path $HOME\AppData\Local\nvim-data -Force -Recurse