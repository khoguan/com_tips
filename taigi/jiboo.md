# 記寫台語字幕个電腦工作流程

最近有咧做一个專案，是聽寫台語記錄片个字幕。愛交个字幕檔是 Word 檔，
兩欄个表格，第一欄寫台語漢字，毋通超過 14 字，第二欄寫台羅。

Mac 版个 Word 蓋兩光，扑台羅不時會出現歹看个字型，明明都有先設做 Times New Roman 矣，
伊嘛是家婆共咱換做新細明體抑是 Calibri 字型，見擺扑了攏著改字型，真 lóo！

Apple 个文書軟體 Pages 佇即方面就真好勢，字型袂走爭去。

即兩工研究出一套新个工作流程，越頭轉來我意愛个純文字環境做工課，
用 `vim/nvim` editor 程式先扑純文字檔，第一欄猶原是漢字，扑了，揤 `Tab`，
才閣扑數字式个台羅，了後揤 `Enter` 進到第二tsuā 个漢字，扑了，閣揤
`Tab`，扑台羅，按呢一直落去。

即種就是叫做 `TSV` (Tab Separated Values) 格式个純文字檔。完成了後存檔，
可比講號做 `jiboo.txt`。閣來開始踮 `bash` 環境批次處理轉做使用調號个正式版台羅，
利用我自家開發个命令列程式 `tlst.raku` 來轉換。指令如下：

```shell
paste <(cut -f1 jiboo.txt) <(cut -f2 jiboo.txt | tlst) > jiboo-fin.txt
```

即tsuā 指令用著 I/O redirection 个進階用法，本底我嘛袂曉，是問 AI 教我个。
按呢處理一下，所得著个 `jiboo-fin.txt` 檔案內底个台羅就變做調號式台羅啦！

閣來著愛將 `jiboo-fin.txt` 个內容規个 copy 過來 MS Word 內底，全選了後，
點功能表个 `表格 -> 轉換 -> 文字轉換為表格`，伊就會變做是兩欄个表格矣。
最後才選第二欄，做一睏將字型改做 `Times New Roman` 就著矣。

2026-06-20 記
