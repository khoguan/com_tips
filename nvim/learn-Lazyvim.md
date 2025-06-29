NOTE: 以下關係 LazyVim.nvim 套件个概觀佮學習方向，是 Warp AI 所提供

# LazyVim on my Mac.

## 🔧 Your Neovim Configuration Overview

You're running LazyVim - a well-structured Neovim distribution that provides
a solid foundation with sensible defaults. Here's what you have:

## 🎨 Core Framework
•  LazyVim: Modern Neovim configuration framework
•  Lazy.nvim: Plugin manager for fast loading
•  Theme: Tokyo Night (with Gruvbox also configured)

## 📁 Key Plugins & Features

### 🚀 Editor Enhancement

| Plugin | What it does | How to use |
|--------|-------------|------------|
| Flash.nvim | Lightning-fast navigation | <leader>s for jump, <leader>S for treesitter |
| Which-key | Shows keybinding hints | Automatic popup when you pause typing |
| Mini.pairs | Auto-close brackets/quotes | Automatic |
| Mini.ai | Enhanced text objects | vaf (around function), vac (around class) |

### 🎯 File Management & Search
| Feature | Keybinding | Description |
|---------|------------|-------------|
| File finder | <leader>ff | Find files in project |
| Live grep | <leader>/ | Search text in files |
| Recent files | <leader>fr | Open recently used files |
| File explorer | <leader>e | Toggle file tree |

### 💻 Language Support

#### Python (Your custom config)
•  Pyright: Language server for completions, diagnostics
•  Ruff: Lightning-fast linting and formatting
•  Usage: Automatic on .py files

#### TypeScript/JavaScript 
•  Full language server support
•  Keybindings: <leader>co (organize imports), <leader>cR (rename file)

#### JSON
•  Schema validation and completion
•  Automatic formatting

#### Markdown (via VimTeX)
•  Advanced editing features
•  Typora integration: <leader>ot (open current file), <leader>oT (open file under cursor)

### 🔧 Development Tools
| Plugin | Purpose | Key Features |
|--------|---------|--------------|
| LSP | Language intelligence | Completions, diagnostics, go-to-definition |
| Treesitter | Syntax highlighting | Better syntax understanding |
| Gitsigns | Git integration | Show git changes in gutter |
| Trouble | Diagnostics viewer | <leader>xx to toggle |
| Grug-far | Find and replace | Advanced search/replace across files |

### ✨ UI & Experience
| Feature | Description | Usage |
|---------|-------------|-------|
| Bufferline | Tab-like buffer management | Click or <leader>bb for buffer list |
| Lualine | Status line with git info | Always visible |
| Noice | Better UI for messages | Automatic |
| Dashboard | Welcome screen | <leader>h to return |

### 🎮 Your Custom Keybindings

Insert Mode Navigation
•  Ctrl+h/j/k/l: Move cursor without leaving insert mode
•  Ctrl+a: Jump to beginning of line
•  Ctrl+e: Jump to end of line

### Indentation & Formatting
•  <leader>i=: Fix indentation for entire file
•  <leader>it: Toggle between tabs and spaces
•  <leader>ii: Show current indentation settings
•  Alt+j/k: Move lines up/down

### Diagnostics & Debugging
•  <leader>xx: Toggle Trouble diagnostics
•  <leader>xd: Show diagnostics in Telescope
•  ]d / [d: Navigate between diagnostics

### Restored Vim Commands
•  s: Substitute character (instead of Flash jump)
•  S: Substitute line (instead of Flash jump)

### 🎯 Language-Specific Indentation
Your config automatically adjusts indentation:
•  Python: 4 spaces
•  JavaScript/TypeScript/JSON: 2 spaces  
•  Go: Real tabs (4 width)
•  Lua: 2 spaces
•  HTML/CSS: 2 spaces
•  Markdown: 2 spaces with word wrap

### 🚀 How to Get Started

1. Finding files: Press <leader>ff and start typing
2. Searching text: Press <leader>/ to search across all files
3. File explorer: Press <leader>e to browse files
4. Command palette: Press <leader><leader> 
5. Help with keys: Press <leader> and wait - Which-key shows options

### 🔧 Special Features

•  Session persistence: Your sessions auto-save and restore
•  Smart spell check disabled: No red underlines on Chinese characters
•  Custom scroll offset: 4 lines instead of default 10
•  Beautiful list characters: Uses dots and arrows for whitespace
•  Todo highlighting: TODO, FIXME, etc. are automatically highlighted

### Conclusion

This is a very well-configured setup that should handle most development tasks efficiently! The LazyVim foundation gives you modern Neovim features while your customizations add personal workflow improvements.

