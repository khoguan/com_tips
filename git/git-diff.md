# Git 三方版本比較 Cheatsheet by AI

## 📊 三個版本的流程圖說明

         ┌────────────┐
         │   HEAD     │  ← 最後一次提交的內容（已 commit）
         └────┬───────┘
              │
       git diff --cached
              │
         ┌────▼───────┐
         │   Stage    │  ← 暫存區（用 git add 加入的內容）
         └────┬───────┘
              │
       git diff f.txt
              │
         ┌────▼───────┐
         │ Work Dir   │  ← 你現在正在編輯的版本
         └────────────┘
    
      git diff HEAD f.txt  ↖︎ 直接從 HEAD 比到目前的檔案狀態


---

## 🧠 Git 比較 Cheatsheet

| 比較來源 | 比較目標 | 指令 | 說明 |
|-----------|-------------|--------|------|
| `HEAD` | `Stage` | `git diff --cached f.txt` | 顯示你 `git add` 的內容和最後一次提交的差異 |
| `Stage` | `Working Directory` | `git diff f.txt` | 顯示你修改但尚未 `add` 的部分 |
| `HEAD` | `Working Directory` | `git diff HEAD f.txt` | 顯示你目前所有修改，無論是否 add |
| `HEAD` | （完整檔案） | `git show HEAD:f.txt` | 查看 `HEAD` 裡的檔案完整內容（非 diff） |
| 三向比較（視覺化） | 使用 difftool | `git difftool -d f.txt` | 如果有設定 difftool（如 `meld`），可進行圖形化比對 |
| 查看目前修改狀態 | 無 | `git status` | 顯示哪些檔案 modified、staged、untracked |

---

## 📁 Git 三個狀態簡述

| 區域 | 說明 | 修改方式 |
|------|------|-----------|
| **HEAD** | 最後一次 commit 的版本 | 用 `git commit` 寫入 |
| **Stage (Index)** | 暫存區，下一次 commit 的內容 | 用 `git add` 加入 |
| **Working Directory** | 你正在修改中的檔案 | 直接在編輯器中修改 |

---

## ✅ 常見應用組合

```bash
# 檢查目前有哪些檔案有變更
git status

# 比較 Working Directory 和 Stage（未 add 的變更）
git diff f.txt

# 比較 Stage 和 HEAD（已 add 的變更）
git diff --cached f.txt

# 比較 HEAD 和 Working Directory（全部變更）
git diff HEAD f.txt

# 查看 HEAD 中的某個檔案
git show HEAD:f.txt
```
