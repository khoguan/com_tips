# NvChad 設定改補

NvChad 是真出名个 Neovim distro，雖然真媠，但是有袂少對我來講真明顯个欠點，
今著來「改補」－－無好个設定改予較好，無設著个所在補設。

## 改設定

1. 檔案內容有修改个時，著愛有視覺提示

NvChad 有特製幾套 statusline 予儂用，雖然媠媠，但是有大欠點，就是一个 buffer
有修改个時，statusline 完全無出現提醒作用个視覺變化。本底我是叫 Warp AI 幫我
客製化 statusline，毋閣彼真厚工，做出來个美感也無夠好。後來我發現原生个 vim/nvim
除了 statusline 會做提醒，tabline (佇視窗懸頂) 也會有變化。但是編修單一 buffer
个時，預設袂顯示 tabline，所以著改設定：
```
:set showtabline=2
```

'showtabline' 'stal'    number (default 1)
	The value of this option specifies when the line with tab page labels
	will be displayed:
		0: never
		1: only if there are at least two tab pages
		2: always

2. nvim-tree 欠缺 go to directory 个功能：

佇 mappings.lua 遐補設：

```lua
-- Custom nvim-tree change root mapping
vim.api.nvim_create_autocmd("FileType", {
  pattern = "NvimTree",
  callback = function()
    vim.keymap.set("n", "<leader>cd", function()
      local path = vim.fn.input("Change root to: ", "", "dir")
      if path ~= "" then
        require('nvim-tree.api').tree.change_root(path)
      end
    end, { buffer = true, desc = "Change nvim-tree root directory" })
  end,
})
```
後擺佇 nvim-tree 視窗遐，扑 <leader>cd 下底就會跳出 prompt，予儂直接扑路徑。
