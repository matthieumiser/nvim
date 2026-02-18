# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

Personal Neovim configuration based on kickstart.nvim. Primarily a single `init.lua` file with optional modular plugins.

## Configuration Architecture

### Core Structure
- **init.lua**: All core settings, keymaps, and plugin specs via lazy.nvim
- **lua/kickstart/plugins/**: Optional kickstart plugins (debug.lua and indent_line.lua are enabled)
- **lua/custom/plugins/**: Personal plugin additions (returns empty table, import commented out in init.lua)

### Plugin Management
Uses lazy.nvim. Plugins defined in `require('lazy').setup()` call in init.lua.

### LSP Configuration
- mason.nvim for automatic LSP server installation
- nvim-lspconfig for server configuration
- Configured servers: gopls, pyright, terraformls, kotlin_language_server, lua_ls, tailwindcss, jdtls (Java via nvim-java)

### Formatting (conform.nvim)
- Lua: stylua
- Python: isort + black
- Java: formatting disabled (deferred to external tools)
- Format on save enabled (disabled for C/C++/Java)

## Common Commands

### Plugin Management
- `:Lazy` - Plugin manager interface
- `:Lazy update` - Update plugins
- `:Mason` - LSP/tool installer

### Health Check
- `:checkhealth` - Check Neovim/LSP status

## Key Keymaps

**Leader key**: `<space>`

### Navigation & Search
- `<leader>pv` - Open netrw file explorer
- `<leader>sf` - Search files
- `<leader>sg` - Live grep
- `<leader>fg` - Live grep with args (telescope extension)
- `<leader><leader>` - Find buffers
- `<leader>/` - Fuzzy find in current buffer
- `<leader>sn` - Search Neovim config files
- `<leader>s.` - Search recent files
- `<leader>sh` - Search help tags
- `<leader>sk` - Search keymaps

### LSP
- `gd` - Go to definition
- `gr` - Find references
- `gI` - Go to implementation
- `gD` - Go to declaration
- `K` - Hover documentation
- `<leader>ca` - Code action
- `<leader>rn` - Rename symbol
- `<leader>D` - Type definition
- `<leader>ds` - Document symbols
- `<leader>ws` - Workspace symbols
- `<leader>f` - Format buffer

### Diagnostics
- `[d` / `]d` - Previous/next diagnostic
- `<leader>e` - Show diagnostic float
- `<leader>q` - Open diagnostic quickfix list
- `<leader>sd` - Search diagnostics (Telescope)

### Completion (nvim-cmp)
- `<C-n>` / `<C-p>` - Next/previous item
- `<C-y>` - Accept completion
- `<C-Space>` - Trigger completion
- `<C-b>` / `<C-f>` - Scroll docs
- `<C-l>` / `<C-h>` - Jump in snippet

### Debugging (nvim-dap)
- `<F5>` - Start/Continue
- `<F1>` - Step into
- `<F2>` - Step over
- `<F3>` - Step out
- `<F7>` - Toggle DAP UI
- `<leader>b` - Toggle breakpoint
- `<leader>B` - Set conditional breakpoint

### Claude Code Integration
- `<leader>ac` - Toggle Claude
- `<leader>af` - Focus Claude
- `<leader>ar` - Resume Claude
- `<leader>aC` - Continue Claude
- `<leader>am` - Select Claude model
- `<leader>as` - Send selection to Claude (visual mode)
- `<leader>ab` - Add current buffer
- `<leader>aa` - Accept diff
- `<leader>ad` - Deny diff

## Development Notes

### Configuration Style
- 4-space indentation (spaces, not tabs)
- Leader key: space

### Adding Plugins
1. Create file in `lua/custom/plugins/` returning lazy.nvim spec table
2. Uncomment `{ import = 'custom.plugins' }` in init.lua to enable

### Notable Features
- Gruvbox colorscheme
- Tmux navigation integration (vim-tmux-navigator)
- Automatic file reload on external changes
- Harpoon for quick file navigation
- Relative line numbers (set in Telescope config)
- nvim-autopairs for automatic bracket/quote pairing
- todo-comments.nvim for highlighting TODO/NOTE/etc in comments
