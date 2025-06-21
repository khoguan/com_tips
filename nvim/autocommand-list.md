# 列出 nvim 目前所有个 autocommands

## 我問

I know I can do `:autocmd` to list all the autocommands currently effective in my Neovim ecosystem, but the list can not be searched. How to save the result list for later review?

## AI 答

You can save the autocommands list to a file for later review using Neovim's command redirection. Here are a few methods:

### Method 1: Redirect to a file
```vim
:redir > ~/autocmds.txt | autocmd | redir END
```
This saves all autocommands to ~/autocmds.txt in your home directory.

### Method 2: Redirect and open the file immediately
```vim
:redir > /tmp/autocmds.txt | autocmd | redir END | edit /tmp/autocmds.txt
```
This saves to a temporary file and opens it for immediate viewing.

### Method 3: Capture to a new buffer
```vim
:enew | put =execute('autocmd') | 1delete
```
This creates a new buffer and puts the autocommands output directly into it, then deletes the first empty line.

### Method 4: Use a scratch buffer (recommended)
```vim
:enew | setlocal buftype=nofile bufhidden=hide noswapfile | put =execute('autocmd') | 1delete
```
This creates a scratch buffer (won't be saved) with the autocommands list that you can search through with / and navigate normally.

### For specific autocommand groups:
If you want to filter for specific groups (like the one in your earlier example):
```vim
:redir > ~/kickstart_autocmds.txt | autocmd kickstart-highlight-yank | redir END
```
The scratch buffer method (Method 4) is probably most convenient since you can search it immediately with Neovim's search functionality (/, n, N) and don't have to worry about file cleanup.
