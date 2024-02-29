# HydraVim Commands

Diogo Silva edited this page Sep 3, 2023 · [6 revisions](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands/_history)

# Source code

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#source-code)

The source code of the commands is available [here](https://github.com/HydraVim/HydraVim/blob/main/lua/hydravim/config/commands.lua).

## HydraVimUpdate

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimupdate)

This command updates HydraVim to the latest version. You can also specify a custom repository and branch, see at: [settings](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#settingslua)

```lua
hydravim.repository = {
  branch = "main",
  remote = "HydraVim/hydravim"
}
```

## HydraVimCustomConfig

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimcustomconfig)

Generate a custom configuration for HydraVim or install an existing configuration from a remote repository. You can specify the repository and branch as optional arguments.

### Generate a custom config

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#generate-a-custom-config)

To create a template of the settings, use `HydraVimCustomConfig`. By default, the directory will be located inside `../nvim/lua/user/`. The base template that will be installed is [HydraVim/user-config](https://github.com/HydraVim/user-config)

```lua
:HydraVimCustomConfig
```

### Install an existing config:

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#install-an-existing-config)

If you already have a custom config in a remote repository and want to install it, you can use the same command. For example, if you have your configuration in the repository `yourusername/hydravim-config` and the branch is `main`, use:

```lua
:HydraVimCustomConfig yourusername/hydravim-config main
```

If you don't specify a branch, the command will clone the default branch of the repository. You can use the following command:

```lua
:HydraVimCustomConfig yourusername/hydravim-config
```

## HydraVimSaveSession

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimsavesession)

This command saves the current session.

## HydraVimLoadSession

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimloadsession)

This command loads a previously saved session.

## HydraVimCloseBuffer

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimclosebuffer)

This command closes the current buffer.

## HydraVimCloseEmptyBuffer

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimcloseemptybuffer)

This command closes all empty buffers.

## HydraVimFormat

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimformat)

This command formats the code in the current buffer according to the configured formatting settings.

## HydraVimSaveAllBuffers

[](https://github.com/HydraVim/HydraVim/wiki/HydraVim-Commands#hydravimsaveallbuffers)

This command saves all modified buffers.