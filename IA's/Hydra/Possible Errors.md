# Possible errors

Diogo Silva edited this page Apr 1, 2023 · [6 revisions](https://github.com/HydraVim/HydraVim/wiki/Possible-errors/_history)

## Windows

[](https://github.com/HydraVim/HydraVim/wiki/Possible-errors#windows)

### Error with tree-sitter

[](https://github.com/HydraVim/HydraVim/wiki/Possible-errors#error-with-tree-sitter)

![image](https://user-images.githubusercontent.com/86174715/229292614-f69562d3-6828-415b-ad98-9020cb91e373.png)

- Install gcc from [scoop](https://scoop.sh)

```shell
scoop install gcc
```

- Install Tree-Sitter Cli

```shell
npm install -g tree-sitter-cli
```

### Error installing LSP in Window with Mason

[](https://github.com/HydraVim/HydraVim/wiki/Possible-errors#error-installing-lsp-in-window-with-mason)

Mason relaxes the minimum requirements for Windows: pwsh or powershell, [git](https://git-scm.com/), tar, and [7zip](https://www.7-zip.org/) or [peazip](https://peazip.github.io/) or [archiver](https://github.com/mholt/archiver) or [winzip](https://www.winzip.com/) or [WinRAR](https://www.win-rar.com/)

- Install with [scoop](https://scoop.sh)

```shell
scoop install pwsh git tar 7zip
```