
# 我共 AI 問問題：vim.schedule()

## 我問

You helped me append 3 lines of code to load my personal configuration to
```lua
vim.schedule(function()
  dofile(vim.fn.expand("~/myconfig.lua"))
end)
```
But how does nvim "schedule" to load "~/myconfig.lua"?

## AI 答

Great question! Let me explain how vim.schedule() works and why it's important
for loading your config.

### What vim.schedule() Does:

vim.schedule() is Neovim's way of scheduling a function to run on the next event
loop iteration. Think of it as "run this later, when it's safe to do so."

### The Event Loop:

Neovim has an event loop that processes:
1. Startup tasks (loading core configs, plugins)
2. User input (keypresses, mouse clicks)
3. File operations (reading, writing)
4. Plugin callbacks and scheduled functions

### Why Use vim.schedule() Here:

#### Without vim.schedule() (immediate execution):
```lua
dofile(vim.fn.expand("~/khoguan.lua"))  -- Runs RIGHT NOW
```
#### With vim.schedule() (deferred execution):
```lua
vim.schedule(function()
  dofile(vim.fn.expand("~/khoguan.lua"))  -- Runs on NEXT event loop
end)
```
### Why This Matters for Your Config:

1. Loading Order: Your config has autocmds that might depend on plugins being
   fully loaded
2. Plugin Dependencies: Your pcall(require, "cmp") needs nvim-cmp to be available
3. Initialization Safety: Some Neovim APIs aren't ready during early startup

Execution Timeline:

```
Startup Phase:
├── 1. Load NvChad core
├── 2. Load plugins (lazy.nvim)
├── 3. Load mappings (scheduled)
├── 4. Load your config (scheduled) ← Your code runs here
└── 5. Event loop starts handling user input
```

Alternative Approaches:
```lua
-- Immediate (might fail if plugins aren't ready)
dofile(vim.fn.expand("~/khoguan.lua"))

-- Scheduled (safer, runs when ready)
vim.schedule(function()
  dofile(vim.fn.expand("~/khoguan.lua"))
end)

-- Plugin callback (runs after specific plugin loads)
vim.api.nvim_create_autocmd("VimEnter", {
  callback = function()
    dofile(vim.fn.expand("~/khoguan.lua"))
  end
})
```

The vim.schedule() approach ensures your personal config loads after the core
system is stable but before you start using Neovim - perfect timing for personal
overrides!
