# 家己寫个 lua configuration file 按怎測試效果？

Here are the best practices for testing your Neovim configuration:

1. Syntax Check First
```bash
nvim --headless -c "luafile ~/khoguan.lua" -c "qa"
```
This runs your config file in headless mode to check for syntax errors without opening the full editor.

2. Test in a Clean Environment
```bash
# Start nvim with minimal config to isolate your changes
nvim --clean -c "luafile ~/khoguan.lua"
```

3. Test Specific Functionality
For your autocmd changes (for text and markdown file types), test by:
```bash
# Open a text file to trigger the FileType autocmd
nvim test.txt
# Or markdown
nvim test.md
```

4. Check Lua Execution
```bash
# Run nvim and execute Lua commands to verify behavior
nvim -c "lua print('Testing config')" -c "qa"
```

5. Incremental Testing Approach
•  Comment out sections of your config
•  Test each part individually
•  Gradually uncomment to isolate issues

6. Use Neovim's Built-in Debugging
Once in nvim:
```nvim
:lua print(vim.inspect(vim.bo.filetype))
:lua print(pcall(require, "cmp"))
:messages
```

