# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal Neovim configuration based on kickstart.nvim, a teaching-focused starter configuration. The configuration is primarily contained in a single `init.lua` file with some modular plugin extensions.

## Configuration Architecture

### Core Structure
- **init.lua**: Main configuration file containing all core settings, keymaps, and plugin specifications
- **lua/kickstart/plugins/**: Optional kickstart plugins (indent_line.lua is currently enabled)
- **lua/custom/plugins/**: Directory for personal plugin additions (currently empty but ready for extensions)

### Key Configuration Patterns

**Plugin Management**: Uses lazy.nvim as the plugin manager. Plugins are defined in the main `require('lazy').setup()` call in init.lua:230-966.

**LSP Configuration**: Comprehensive LSP setup using:
- mason.nvim for automatic LSP server installation
- nvim-lspconfig for server configuration
- mason-tool-installer for ensuring required tools are installed
- Configured servers: gopls, pyright, terraformls, lua_ls, tailwindcss

**Key Plugin Integrations**:
- Telescope for fuzzy finding with live-grep-args extension
- nvim-treesitter for syntax highlighting
- conform.nvim for auto-formatting (stylua for Lua, isort+black for Python)
- nvim-cmp for completion with LSP integration
- Claude Code integration with comprehensive keymaps under `<leader>a`

## Common Commands

### Plugin Management
- `:Lazy` - Open plugin manager interface
- `:Lazy update` - Update all plugins
- `:Mason` - Open LSP server/tool installer

### LSP Tools
- `:checkhealth` - Check Neovim health (including LSP status)

### Formatting
- `<leader>f` - Format current buffer using conform.nvim
- Format on save is enabled by default (configurable per filetype)

### Key Custom Keymaps
- `<leader>pv` - Open netrw file explorer (`:Explore`)
- `<leader>fg` - Live grep with arguments using Telescope extension
- Claude Code integration available under `<leader>a` prefix

## Development Notes

### Configuration Style
- Uses spaces (4-space indentation) as configured in init.lua:101-109
- Follows kickstart.nvim conventions with extensive inline documentation
- Leader key is set to space (`<leader>` = `<space>`)

### Extension Points
- Add new plugins to `lua/custom/plugins/` directory
- Plugin files should return a Lua table following lazy.nvim plugin spec format
- The custom plugins directory is ready for use but imports are currently commented out in init.lua:945

### LSP and Formatting
- Mason automatically installs configured LSP servers
- Conform.nvim handles formatting with LSP fallback
- Format on save is enabled except for C/C++ files (see init.lua:715)

## Notable Features
- Claude Code plugin integrated with comprehensive keybindings
- Telescope with live grep args extension for enhanced searching
- Automatic file reload when changed externally
- Tmux integration for seamless pane navigation
- Gruvbox colorscheme with custom highlight overrides