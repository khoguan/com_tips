# 一寡好用个 git 指令

## local vs. remote

1.  觀察 local 佮 remote 所有个 branches 个狀態：

```shell
# To fetch the latest remote branch information first:
    git fetch origin

# then check all the branches:
# -a 列出全部个 branches
# -v verbose

    git branch -av

# 輸出示例，看會出 local 个資料差 remote 一个 commit (behind 1)
    * main                4c19b3d [behind 1] 改用 md 格式
      remotes/origin/HEAD -> origin/main
      remotes/origin/main 6d97b04 Update autocommand-list.md

# To see remote branches with their tracking relationships:
    git remote show origin
```
2.  觀察 remote 比 local 加出啥乜改變

```shell
# To see a summary of differences:
    git fetch origin
    git diff HEAD origin/main

# To see which commits are different:
    git log --oneline HEAD..origin/main    # Commits in remote but not local
    git log --oneline origin/main..HEAD    # Commits in local but not remote

# To see a visual representation of the branch divergence:
    git log --oneline --graph --decorate HEAD origin/main
```

3. 列出CWD下底予 git 追蹤个檔案簡表：
```shell
  git ls-files
# 輸出
  .gitignore
  AI/README.md
  AI/git-tips.md
  AI/nvchad-config.md
  README.md
  git/git-diff.md
  git/remote-repo.md
```
加 -s 會列出遮个檔案个mode, object hash, and stage information:
```
  git ls-files -s
# 輸出
  100644 f143135ca1a18b000bdbe6f61492788fe941d7ca 0    .gitignore
  100644 7f38a1745fb37e826a89f8e5da2af2068a5afa91 0    AI/README.md
  100644 91e23235f2672bd5958e3f38b7455f3158c46026 0    AI/git-tips.md
  100644 bcb809b090720891962a7dd21dda5a951ce658aa 0    AI/nvchad-config.md
  100644 b2a4200517843d683dec00755549838d9d9bf67b 0    README.md
  100644 d9dfd0295ea847ccb34900d7c755882ec9168289 0    git/git-diff.md
  100644 5e30b27c0a4cdd930f0a92e618eed36818cb5b7a 0    git/remote-repo.md
```

### AI 解說 "100"

The 100644 you see in git ls-files -s is actually a 6-digit octal number that
represents the file mode in Git's internal format. Let me break it down:

*  100: This is the file type indicator
*  644: This is the traditional Unix permission you're familiar with

The first three digits (100) indicate the file type:

*  100 = regular file
*  040 = directory  
*  120 = symbolic link
*  160 = gitlink (submodule)

So 100644 means:

*  100 = regular file
*  644 = owner can read/write, group can read, others can read

Other common Git file modes you might see:

*  100644 = regular file with 644 permissions
*  100755 = regular file with 755 permissions (executable)
*  120000 = symbolic link
*  040000 = directory (though directories don't typically show up in git ls-files)

This is why all your files show 100644 - they're all regular files with standard
read/write permissions for the owner and read-only for group/others, which is
the default for most text files in Git repositories.
