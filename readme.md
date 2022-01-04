# 專案說明

這是一個 git 的範例專案  
這是給 MFEE22 的專案

## 這是 _markdown_ 的示範

- 第一點
    - 第一小點
- 第二點

[我的github]
(https://github.com/IanHsieh1015)

# 12/25
## 任務 0: 終端機指令練習

```
. 現在的檔案夾位置
.. 上一層案夾
~ 我的目錄，目前使用者的目錄(ex /Users/aaa)
```

參數的意義，不同指令會不一樣，但通常會是這樣
`-a` ==> all   全部
`-f` ==> force 強制
`-r` ==> recursive 遞迴
`-l` ==> long 查看完整名稱

```bash=
# touch 可以建立檔案
touch a.txt
```

| Windows | MacOS/Linux | 說明 |
| -------- | -------- | -------- |
| cd     | cd     | 切換目錄 change directory    |
| cd     | pwd     | 顯示目前所在路徑 print working directory    |
| dir     | ls     | 列出目前檔案夾的檔案列表  list   |
| mkdir     | mkdir     | 建立新的檔案夾  make dir   |
| copy     | cp     | 複製檔案   copy  |
| move     | mv     | 移動檔案   move  |
| del     | rm     | 刪除檔案    remove |
| cls     | clear     | 清除畫面上的內容     |

> 裝 source tree 好像就會順便裝 linux 可以用的終端

```bash=
# 建立 git-workshop 檔案夾
mkdir git-workshop
# 進入 git-workshop 檔案夾
cd git-workshop
# 建立檔案 test.txt
touch test.txt

ls
# 列出全部檔案（包含隱藏檔）
# 隱藏檔/隱藏檔案夾在 linux 作業系統，通常是以 . 為開頭
ls -a   
# 以完整格式列出檔案
ls -l
# 以完整格式列出所有的檔案
ls -al

# 檢視檔案內容
cat test.txt
```

```bash=
# 刪除了全部的東西
rm -rf *
```

11:20

---
## 任務 1: 安裝 git

https://git-scm.com/


---
## 任務 2: 設定環境變數

```bash=
$ git config --global user.name "ashleylai58"
$ git config --global user.email "ashleylai58@gmail.com"

# 確認設定的內容
$ git config --list


# cat 印出檔案內容
cat ~/.gitconfig
```

sublimt text, vscode
nano 
vi, vim

```
[alias]
	co = checkout
	br = branch
	ci = commit
	st = status
        lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date=iso
	l = log --oneline --graph
        la = log --all --oneline --decorate --graph
```

---
## 任務 3: 建立 repo

init ==> initial

初始化一個檔案夾，讓這個檔案夾可以被 git 管理

```bash=
git init
```

![](https://i.imgur.com/iYbhwu4.png)

---
## 任務 4: 在 repo 中新增、修改、刪除檔案

```bash=
# 查看 git 的狀態
$ git status
$ git st

# 把檔案加入
$ git add test.txt

# 提交這次的修改
$ git commit -m "正確填寫這次 commit 的資訊"
$ git ci -m "正確填寫這次 commit 的資訊"

# 檢視這次修改的差異
$ git diff

# 已經加入過的檔案，又有修改的話，一樣要再 add 一次，才可以 commit
$ git add test.txt
$ git ci -m "xxxx"
# 針對已經加入過的檔案，可以直接用以下指令提交
$ git ci -am "xxxxx"

# 可以「反悔」加入暫存區
$ git restore --staged test.txt

# 反悔剛剛的修改
$ git restore test.txt



# 查看提交紀錄
$ git log

# 查看特定檔案的紀錄
$ git log <檔名>

# 查看檔案修改細節
$ git log -p test.txt

# 可以針對 commit 訊息做搜尋
$ git log --grep="delete"

# 查看內容是誰編寫的
$ git blame test.txt
```

Q. 多久（寫多少程式）應該 commit 一次？

A.「團隊一致性」，原則上是盡量小、但要完整(依公司)

-> 下班前請先 commit 一次
	- 看進度
	- 萬一電腦/人出問題

1:30

bitbucket
	-> private / public 都不用收費
	-> 專案人數只能 5 人以下
gitlab

github -> 以前 private 就要收費
	   -> 工程師的社群、作品證明
面試前需整理一下 github
commit message 


---
## 任務 5: 建立分支與合併

main? (早期master，後期改為main)

master
master - slave (主要的機器、備份的機器)

BLM

~/.gitconfig
```bash=
[init]
        defaultBranch = main
```

```bash=
git branch -M main
```

SCRUM

![](https://i.imgur.com/1IHb1J1.png)


sprint 通常是 2 - 4 週 
假設 srpint 是 2 週
-> 每兩週就要產出可以 demo 的成果
	-> 做錯的損失比較少
	-> 盡快回應市場變化
-> 每兩週就會改善

daily meeting -> stand meeting


反省會議：
- 這個 sprint 當中，有沒有哪些地方做得好的？ --> 持續加強好的地方
- 這個 sprint 當中，有沒有哪些地方做得不好的？ --> 怎麼改善？
- 感謝誰...

對事不對人

設計師
「這不是我要的」


ＰＭ: 如時如質如預算
時間 vs 品質 vs 範疇
--> 通常會犧牲品質 （通常犧牲工程師）

SCURM 就是希望維持時間、品質，用範疇的變動來討論

台灣比較偏向硬體思維（硬體比較可以是瀑布式）

「命名」-> 電腦科學界的兩大難題之一

```bash=
git branch <分支名稱>
git br <分支名稱>

# 切換分支 （新版）
git switch <分支名稱>

# 合併分支
# 把 feat-login 合併進去 main 裏面
# 1. 切換回 main 分支
git switch main
# 2. 把 feat-login 合併進來
git merge feat-login
```

https://udacity.github.io/git-styleguide/

coding style (不同程式語言會有自己這個語言慣用的寫法)
```javascript=
let a = 1234;
if (a == 1234) {
  return a + 34;
}
```

https://google.github.io/styleguide/jsguide.html

或者就是依賴工具

refactor 重構
在不改變功能(介面)的情況下，修改程式，使程式更容易維護與擴充。


bad smell 壞味道
https://www.tenlong.com.tw/products/9789865021832?list_name=srh

「盡量」避免衝突
可以頻繁地 merge 你的功能分支 （當然還是要保持完整性）

---
## 任務 6: 建立 Github 帳號

---
## 任務 7: 建立 github repo

git-workshop

---
## 任務 8: 撰寫 readme

markdown 語法: https://markdown.tw/
- 純文字檔 nano, vi, sublime text, vscode, 記事本,...
- 希望有點簡易的格式可以用

--> 可不可以用 html 寫文件？
讀還行，但編輯不夠好，編輯時會看到一堆雜訊(html element)

文件
word, execl, google doc,...
notion, hackmd, ..線上文件系統 --> 共同編輯

文件跟程式碼對不起來，因為文件的維護很困難

readme.md

# 標題 --> h1

## 副標題 --> h2

### 小標題 --> h3

- 第一點
	- 第一小點
- 第二點

[Git Workshop for MFEE22 這是連結示範](https://hackmd.io/Ns0AuMFtROOT9E0oSujQ7A)

> 這是引言

markdown 語法參考: 
https://gist.github.com/billy3321/1001749662c370887c63bb30f26c9e6e

Q. 把本地的分支推送到 github 上面去？

第一次推 feat-login 上去 github
```bash=
git push -u origin feat-login
```

第二次之後就只需要 `git push` 就可以了


---
## 任務 9: 了解 git flow

![](https://i.imgur.com/rV7GdFn.png)

### pull requests 
在 develop / main / production ..等團隊分支上，不會直接下 merge 指令，通常都會在 github 上發 pull requests，然後請同事幫忙 review，同事 review 完成之後，才會按下 merge。

### code review
檢查別人的程式碼？ --> 確保程式跟專案的品質
- coding style 是否有符合規範
- 功能開發的是否符合需求
- 測試功能是否正確
	- 有可能是用眼睛看
	- 可能需要在本機切換到這個分支執行看看
- 效能？安全性？...

code review 的規範
對事不對人

https://google.github.io/eng-practices/review/reviewer/

及早發現問題，這樣處理問題的成本才會低！

---

--- 

資料結構 Data Structure (DS)
演算法 Algorithm (Algo)
資料庫 Database (DB)
  正規化 <-- 怎麼設計 table schema
  （這不是一定非得要遵守的法律，但是我們會盡量遵守，的確有時候會因為一些商業邏輯特殊的設定，會違反正規化）
網路 Networking
作業系統 Operating System (OS)

# 12/26
# NodeJS

什麼是 NodeJS?
- 不是框架
- 後端在用的？
- 不是程式語言

到目前為止，你們寫的 Javascript 都在哪裡「執行」？ 瀏覽器

==> NodeJS 另外一個可以執行 Javascript 的地方

## 安裝

版本
- Current: 最新的 NodeJS 版本
- Active: 正在積極維護和升級的版本
- Maintenance: 維護中的 LTS，直到生命週期結束
- LTS: Long-Term Support 長期維護版
- EOL: end of life，生命週期結束、不再維護

第一種安裝方式：到官網下載安裝檔案安裝 https://nodejs.org/en/

第二種方式：用 nvm

node version manager

mac:
https://github.com/nvm-sh/nvm

```bash=
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash


echo $0
# 查詢自己目前用的 shell
```

查詢目前自己使用的 shell，然後把畫面上出現需要你複製貼上的文字，貼到該 shell 的設定檔 ~/.zshrc 或是 bash 的設定檔


windows: https://github.com/coreybutler/nvm-windows/releases


```bash=
nvm -v 

nodenvm -v
```


使用者名稱用中文的話，安裝 nvm 可能會有問題。


## nvm 指令

```bash=
# 查詢 nvm 指令
nvm ??

# 列出可以安裝的版本
nvm ls-remote 16
# windows版本
nvm list available

# 安裝最新版本號
nvm install 16.13.1

# 切換要使用的 node 版本
nvm use 16.13.1

# 確認目前執行的版本
node -v

# 列出你目前主機安裝的版本
nvm ls
# windows版本
nvm list 


# 設定預設的版本
nvm alias default 16.13.1
```

用 nvm 來安裝了 node
nvm -v  (node version management)
node -v


12/26 練習1
1. 在 github 上建立一個 node-mfee22 的 repo
2. clone 下來
3. 請在裡面建立一個 basic 檔案夾
4. 在 basic 裡，建立一個 hello.js
5. 在 hello.js 裡編寫一些 js 程式
6. 切換 (cd) 到跟 hello.js 同樣檔案層級
7. 執行 hello.js

```bash=
node hello
```

12/26 練習2
完成 sum.js 並且 push 到 github 上

## NodeJS 是？

- NodeJS 是不是一個程式語言？ No
- NodeJS 是不是一個框架？ No
- NodeJS 可以讓我們脫離瀏覽器執行 JS 的環境 ==> 讓你可以在伺服器端執行程式
- NodeJS 是以 Chrome 的 V8 引擎為核心
	https://github.com/nodejs/node/tree/master/deps/v8

JS 的執行環境
- 瀏覽器
- NodeJS

![](https://i.imgur.com/JcXqMC2.png)

ducument.getElementBy
window.location 

==> document, window,... 這些是瀏覽器提供的物件
==> 所以這些物件不可以在 nodejs 裡面用

已經有 PHP 了，為什麼還會有 NodeJS??

Ryan 高性能的 Web Server
	研究過 apache
	嘗試用 C, Lua, Haskell, Ruby 這些程式語言去開發

Microsoft Windows
「內建 IE 瀏覽器」 --> 壟斷

Mozilla --> firefox (工程師用 geek)

Chrome 執行 JS 引擎 --> V8
https://github.com/v8/v8
-> jquery, vue/react/angular
Edge 他要用 Chrome 的核心 V8

Chrome V8
Firefox SpiderMonkey
Safari JavaScriptCore / Nitro
Edge Chakra 後來改用 V8

## NodeJS 的特色 (JS)

- 單執行緒
- 非阻塞
- 非同步 IO
- 事件循環 (event loop)

### 單執行緒 single-thread

thread --> 作業系統

- Process vs Thread (multi-thread)
- 排程演算法, FIFO, SJF
- Thread pool
- Deadlock
- Context Switching
- Race Condition **

# 12/25~26上課心得

小賴老師上課方式與目前有上過課的老師相比之下差異甚大，感覺是一個非常熱血，上課方式也非常的生動活潑，但同時也感到巨大的壓力，感覺又回到國、高中那種上課的感覺，老師會不定時隨機抽點同學，除了學習code、架構、原理，更重要的是還可以聽到工作經驗相關分享及如何找到學習的方法、態度！