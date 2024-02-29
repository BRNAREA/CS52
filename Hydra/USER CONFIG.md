# Custom User Config

Diogo Silva edited this page Sep 3, 2023 · [11 revisions](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config/_history)

## Config already existing

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#config-already-existing)

If you have a custom config, install it using:

```lua
:HydraVimCustomConfig <user>/<repo> <branch>
```

> **_EXAMPLE_** :HydraVimCustomConfig HydraVim/user-config main

## User Config File Structure

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#user-config-file-structure)

The user configuration allows for a HydraVim setup without having to fork or edit it directly, so you can always keep your HydraVim up to date without losing your customizations. To create a template of the settings, use `HydraVimCustomConfig`. By default, the directory will be located inside `../nvim/lua/user/`

```shell
📁 nvim
   └── 📁 lua
       └── 📁 user
           ├── 📁 config
           │   ├── 📄 autocmds.lua
           │   ├── 📄 commands.lua
           │   ├── 📄 mappings.lua
           │   └── 📄 settings.lua
           └── 📁 plugins
               ├── 📄 dap.lua
               ├── 📄 tokyonight.lua
               └── 📄 null-ls.lua

```

#### Note

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#note)

- It is possible to create subdirectories in `.../nvim/user/` and use them as needed.
- The user folder is ignored during update processes, so you can keep your HydraVim up to date without losing your customizations.
- The base template that will be installed is [HydraVim/user-config](https://github.com/HydraVim/user-config)
- You can start a repository in config and save it on GitHub. So you can restore it more easily.

### autocmds.lua

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#autocmdslua)

The `autocmds.lua` file allows for the creation of autocmds and will be loaded directly with source, giving you great freedom. It is possible to add other things besides autocmds, such as highlights and functions, according to your needs. Example configuration:

```lua
-- HydraVim Auto Commands
-- This Lua module defines custom auto commands for HydraVim.

-- Add auto commands using the vim.api.nvim_create_autocmd function.
-- These auto commands trigger when entering or leaving Insert mode.

local autocmd = vim.api.nvim_create_autocmd

-- Auto command "InsertEnter" triggers when entering Insert mode.
autocmd({ "InsertEnter" }, {
    pattern = '*',                  -- Match all file types.
    command = "setlocal nohlsearch",-- Set 'nohlsearch' to disable highlighting search matches.
})

-- Auto command "InsertLeave" triggers when leaving Insert mode.
autocmd({ "InsertLeave" }, {
    pattern = '*',                  -- Match all file types.
    command = "setlocal hlsearch",  -- Set 'hlsearch' to enable highlighting search matches.
})
```

### commands.lua

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#commandslua)

Add commands in `commands.lua`, as in the example.

```lua
-- HydraVim Custom Command
-- This Lua module defines a custom user command for HydraVim.

-- Add commands using the vim.api.nvim_create_user_command function.
-- The command "CustomUserCommand" takes an arbitrary number of arguments and prints them.

local command = vim.api.nvim_create_user_command

command(
  "CustomUserCommand",
  function(opts)
    print(opts.args)
  end,
  {
    nargs = "*",                    -- Allow an arbitrary number of arguments.
    desc = "Custom user command",   -- Description for the custom command.
  }
)
```

### mappings.lua

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#mappingslua)

The `mappings.lua` is a table that allows defining custom mappings:

|Key|Description|
|---|---|
|`n`|Normal|
|`i`|Insert|
|`v`|Visual|
|`t`|Terminal|

```lua
-- HydraVim Mappings
-- This Lua module defines custom key mappings for various modes in HydraVim.

return {
  -- n: Normal mode mappings.
  n = {
    ['<C-Q>'] = {'<ESC><CMD>q!<CR>',},  -- Map <Ctrl-Q> to forcefully quit without saving.
  },

  -- v: Visual mode mappings.
  v = {
    ['<C-Q>'] = {'<ESC><CMD>q!<CR>',},  -- Map <Ctrl-Q> to forcefully quit without saving.
  },

  -- i: Insert mode mappings.
  i = {
    ['<C-Q>'] = {'<ESC><CMD>q!<CR>',},  -- Map <Ctrl-Q> to forcefully quit without saving.
  },

  -- t: Terminal mode mappings.
  t = {
    ['<A-h>'] = {'<CMD>ToggleTerm<CR>',},  -- Map <Alt-h> to toggle the terminal.
  },
}
```

### settings.lua

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#settingslua)

The `settings.lua` is a table that defines the options for nvim (opt, wo, g, o, b):

```lua
-- HydraVim Configuration
-- This Lua module defines various options and configurations for HydraVim.
-- It includes settings for options (opt), window-local options (wo), global options (o),
-- buffer-local options (b), and vim global variables (g).

return {
  -- opt: Option settings.
  opt = {
    tabstop = 2,  -- Number of spaces for a tab character.
  },

  -- wo: Window-local options.
  wo = {
    wrap = false,  -- Disable line wrapping.
  },

  -- o: Global options.
  o = {
    syntax = "on",  -- Enable syntax highlighting.
  },

  -- g: Global variables.
  g = {
    -- hydravim: Main configuration table for HydraVim settings.
    hydravim = {

      -- dirs: Directory paths used by HydraVim.
      dirs = {
        user = vim.fn.stdpath "config" .. "/lua/user/",  -- User configuration directory. Set to `false` to disable the theme.
        data = vim.fn.stdpath "data" .. "/hydravim/",    -- Data directory for HydraVim.
      },

      -- ui: User Interface settings for HydraVim.
      ui = {
        theme = "catppuccin-mocha",  -- Theme to be applied (e.g., "catppuccin-mocha").
      },

      -- repository: Git repository related settings for HydraVim.
      repository = {
        branch = "main",  -- Default branch for HydraVim repository.
        user_config = {
          branch = "1.4",  -- Default branch for user-config repository.
          remote = "HydraVim/user-config",  -- Remote repository URL for user-config.
        },
      },
    },
  },
}
```

### plugins

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#plugins)

In the `plugins` folder, it is recommended that each plugin has its own file, making it simpler to remove them if necessary. However, you can choose to do it as you prefer. Below is an example of installing the `null-ls` plugin. Learn more about installing plugins in [Lazy.nvim](https://github.com/folke/lazy.nvim)

```lua
return {
  "jay-babu/mason-null-ls.nvim",
  event = { "BufReadPre", "BufNewFile" },
  opts = {
    ensure_installed = { "stylua" },
    automatic_installation = false,
    automatic_setup = true
  },
  dependencies = {
    "williamboman/mason.nvim",
    "jose-elias-alvarez/null-ls.nvim",
  },
  config = function(_, opts)
    require("mason").setup()
    require("mason-null-ls").setup(opts)
    require("null-ls").setup {}
  end,
}
```

### Customizing default installed plugins.

[](https://github.com/HydraVim/HydraVim/wiki/Custom-User-Config#customizing-default-installed-plugins)

It is possible to change any value defined by default, such as opts, config, and cmd. In this example, we will modify nvim-tree; simply create a Lua file in the user's plugins folder and customize it.

```lua
-- Customize the 'nvim-tree' plugin
return {
  "nvim-tree.lua", -- The name of the plugin
  opts = {
    view = {
      side = "right", -- Change the side where the tree appears
      adaptive_size = true, -- Enable adaptive sizing
    },
  },
  config = function(_, opts)
    require("nvim-tree").setup(opts)
  end,
}
```

You can do this for any plugin. You can change a field in the table while keeping another, for example, you can alter the 'opts' and keep the default 'config'.

```lua
-- Customize 'nvim-tree' by changing only the 'opts'
return {
  "nvim-tree.lua",
  opts = {
    view = {
      side = "right",
      adaptive_size = true,
    },
  },
}
```

Additionally, you can manage multiple plugins within a single file:

```lua
-- Customize multiple plugins
return {
  {
    "nvim-tree.lua",
    opts = {
      view = {
        side = "right",
        adaptive_size = true,
      },
    },
  },
  {
    "gitsigns.nvim",
    config = function(_, opts)
      require("gitsigns").setup(opts) -- Setup the 'gitsigns.nvim'
    end,
  },
  {
    "folke/tokyonight.nvim", -- Add a theme (note the 'lazy' option to load it on demand)
    lazy = true
  }
}
```