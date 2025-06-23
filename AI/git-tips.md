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
