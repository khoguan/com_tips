# 佇本地建立 remote repo 了後上傳本地 repo 去 remote

## 先確認本地repo建好

```shell
git init
git add .
git commit -m "Initial commit"
```

## 建立remote repo

```shell
gh repo create <repository-name> --public --source=. --remote=origin --push
```

### Options:

*  --public creates a public repo (use --private for private)
*  --source=. uses the current directory as the source
*  --remote=origin sets up the remote as "origin"
*  --push automatically pushes your local commits

### Additional options:

若是無設，後手上網去 github.com 遐設就好。

*  --description "Your repo description" - Add a description
*  --homepage "https://example.com" - Set homepage URL
*  --clone-url - Use HTTPS instead of SSH for cloning

## 上傳

```shell
git push
```
