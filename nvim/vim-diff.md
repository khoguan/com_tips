# 查看目前 buffer 个內容佮已經存檔个有啥出入

佇 vim/nvim 編輯文件个時，三不五時會雄雄 gông 去，毋知家己到底修改著啥所在，
毋敢直接 `:wq`，著先另存新檔名，離開 vim 了後，才閣去比較兩檔个差別，真無效率！

其實 vim 早就有提供 `:DiffOrig` 複合指令矣，執行了後，伊會開拆做兩个視窗，
顯示原檔佮新修改內容个比較。

可惜有袂濟 Neovim distros 煞共即个指令提挕捒，以下是 `:DiffOrig` 个定義：
```
vert new | set bt=nofile | r ++edit # | 0d_ | diffthis | wincmd p | diffthis
```

若是臨時無用 DiffOrig thang用，也會使得用：
```
:w ! diff % -
```
