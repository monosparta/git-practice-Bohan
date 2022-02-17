# 基本介紹 GIT 簡略歷史、使用緣由、何為版本控制？
## 歷史及使用緣由
git是一個分散式版本控制軟體，最初由林納斯·托瓦茲創作，於2005年以GPL授權條款釋出。最初目的是為了更好地管理Linux核心開發而設計。git最初的開發動力來自於BitKeeper和Monotone。git最初只是作為一個可以被其他前端（比如Cogito或Stgit）包裝的後端而開發的，但後來git核心已經成熟到可以獨立地用作版本控制。很多著名的軟體都使用git進行版本控制，其中包括Linux核心、X.Org伺服器和OLPC核心等專案的開發流程。

## 何謂版本控制
版本控制系統是一種軟體，可協助追蹤在程式碼中隨著時間變更的變更。 當開發人員編輯程式碼時，版本控制系統會取得檔案的快照集。 然後，它會永久儲存該快照集，以便稍後視需要重新叫用。

如果沒有版本控制，開發人員會想要在電腦上保留多個程式碼複本。 這是危險的，因為很容易就能在錯誤的程式碼複本中變更或刪除檔案，因此可能會遺失工作。 版本控制系統會藉由管理所有版本的程式碼來解決此問題，但一次只會為小組呈現單一版本。

# 版本控制的邏輯說明



# Git 常用指令集介紹
## 1. 設定自己的 Git
**因為每一次提交 ( commit ) 修改，都會紀錄作者的訊息，因此必須先編輯自己的 Name 以及 E-mail。**
```
$ git config --global user.name "xxxxxxx"  
$ git config --global user.email "xxxx@xxxx"  
```
**設定完成後，可查詢設定內容**
```
$ git config --list
```
## 2.建立新的 Repository
```
$ git init
```
## 3.從 Github 複製別人的 Repository
```
$ git clone https://11111@1111.git(要複製的網址)
```
![image alt](https://i.imgur.com/vD5p56w.png "連結")
## 4.將修改的檔案加入版控
```
$ git add file.txt  // 加入file.txt
$ git add .         // 加入所有檔案
```
## 5.將add的檔案unstag回去
```
$ git reset --<檔案名稱>
```
## 6.提交修改的檔案
**記得必須先執行 $ git add 將修改檔案加入版控才可以提交。**
```
$ git commit               
$ git commit -m "修改file.txt內容"  
// 可同時送出這次 commit 的訊息
```
## 7.查詢過去 commit 紀錄
```
$ git log
$ git log --stat // --stat 參數可看到詳細內容
$ git log -p     // -p 可看到檔案更詳細的變更內容
```

## 8.建立分支
```
$ git branch 分支名稱
```
## 9.切換分支
```
$ git checkout 分支名稱
```
## 10.合併分支
```
$ git merge 分支名稱
```
## 11.更新遠端資料至本地端
```
$ git pull
```
## 12.查詢目前 Git 的狀態
```
$ git status
```
## 13.回復到上一次提交，並取消當前提交
```
$ git reset HEAD^ --hard
```
# .gitignore 配置
## 在Git項目中定義.gitignore文件
對於經常使用Git的朋友來說，.gitignore配置一定不會陌生。這種方式通過在項目的某個文件夾下定義.gitignore文件，在該文件中定義相應的忽略規則，來管理當前文件夾下的文件的Git提交行為。.gitignore 文件是可以提交到公有倉庫中，這就為該項目下的所有開發者都共享一套定義好的忽略規則。在.gitingore 文件中，遵循相應的語法，在每一行指定一個忽略規則。如：
1. *.log
2. *.temp
3. /vonder


## .gitignore檔案的使用方法
首先，在你的工作區新建一個名稱為.gitignore的檔案。
然後，把要忽略的檔名填進去，Git就會自動忽略這些檔案。
不需要從頭寫.gitignore檔案，GitHub已經為我們準備了各種配置檔案，只需要組合一下就可以使用了。  
有時對於git專案下的某些檔案，我們不需要納入版本控制，比如日誌檔案或者IDE的配置檔案，此時可以在專案的根目錄下建立一個隱藏檔案 .gitignore（linux下以.開頭的檔案都是隱藏檔案），然後在.gitignore中寫入需要忽略的檔案。
1. [root@kevin ~]# cat .gitignore
2. *.xml
3. *.log
4. *.apk

.gitignore註釋用‘#‘, *表示匹配0個或多個任意字符，所以上面的模式就是要忽略所有的xml文件,log文件和apk文件。


# 分支的使用方法
## 1.建立分支
```
$ git branch 分支名稱
```
## 2.切換分支
```
$ git checkout 分支名稱
```
## 3.合併分支
```
$ git merge 分支名稱
```
# Commit 介紹及使用
## Commit介紹
### 開發者要將修改檔案後的專案內容，增加為一個新的專案版本，這個動作就稱為提交（Commit）。開發者可以每次開發完一項功能，就先將新版程式碼，先提交到本機端儲存庫上，再等到多次提交後，才一次將本機端儲存庫上的專案程式碼，一次性發布（稱為Push）到GitHub網站上的雲端儲存庫。通常執行提交時會輸入提交訊息（commit message），說明這個版本做了些什麼修正。有了這些訊息記錄，專案中的開發者便可以追蹤每個版本間的更動。
## commit使用
### 1.提交修改的檔案
**記得必須先執行 $ git add 將修改檔案加入版控才可以提交。**
```
$ git commit               
$ git commit -m "修改file.txt內容"  
// 可同時送出這次 commit 的訊息
```
### 2.查詢過去 commit 紀錄
```
$ git log
$ git log --stat // --stat 參數可看到詳細內容
$ git log -p     // -p 可看到檔案更詳細的變更內容
```


# GitHub 使用方法：push, pull 實作
### push實作：
新增或修改檔案後，下$ git status可以看到那些檔案是有被修改過，並沒有被新增到暫存區，下$ git add . 把資料夾下的東西都存到暫存區，在下$ git commit -m "要輸入的訊息"，在$ git push ，就可以推上github了
![](https://i.imgur.com/bBAFaYe.png)


  

### pull實作：
從另一個main brunch push東西上去
![](https://i.imgur.com/aLjMgvR.png)
更新後可以從另一個brunch pull東西下來
![](https://i.imgur.com/DiUq2bB.png)

### pull-request實作
將修改好的檔案用命令$ git add .暫存，在使用指令$ git commit -m "檔案修改"將檔案傳到本機儲存庫，在使用$ git push將檔案發佈到GitHub的儲存庫
![image alt](https://i.imgur.com/WDBZEaG.png "push")
接下來就能在GitHub上看到上傳的檔案及訊息
![image alt](https://i.imgur.com/GBKzC57.png "")
點擊Pull requests在點擊New pull requests
![image alt](https://i.imgur.com/H0GVkGu.png "")
確定修改內容及發送對象，沒問題按下create pull requests
![image alt](https://i.imgur.com/rcvRmXy.png "修改及發送")
title是commit訊息，也可在下方輸入要告訴原作者的訊息，沒問題按下下方的create pull requests
![image alt](https://i.imgur.com/PyM97wH.png "title")
就能看到成功上傳了
![image alt](https://i.imgur.com/v6Vme0X.png "title")
原作者會收到pull requests訊息，就可以查看別人做了哪些事情
![image alt](https://i.imgur.com/VwPyJWn.png "")
沒問題就可以點下merge pull requests
![image alt](https://i.imgur.com/vLve8eC.png "title")
確定沒問題就可以點下confirm merge
![image alt](https://i.imgur.com/Vxf82jy.png "")
可以看到原本綠色的open變成紫色的merged
![image alt](https://i.imgur.com/fp8VpGp.png "title")

# GitFlow 介紹
一個開發團隊可能有好幾個branch，但每個人對於分支的認知不同，造成每次commit到不同分支，大家也不知道合併要回到誰，若是都合併到master，一定會出大問題，故有了GitFlow去規範使用者。

主要是規範一個工作流程，使開發團隊遵守branch的commit規則，讓最後合併時不容易出問題，並且簡化整個流程圖，讓開發團隊不必自己研發一個新的流程。

流程圖：
![image alt](https://i.imgur.com/3WwrUYO.png "title")

Git Flow主要的分支有 master、develop、hotfix、release 以及 feature 這五種分支，各種分支負責不同的功能。其中 Master 以及 Develop 這兩個分支又被稱做長期分支，因為他們會一直存活在整個 Git Flow 裡，而其它的分支大多會因任務結束而被刪除。

**Master**  
主要呈現給客戶的產品版本，確保每個版本都要可以執行，這個分支的來源只能從別的分支合併過來，開發者不會直接commit到這個分支，因為是穩定版，通常會在這分支上有版本編號。
**Develop**
這個分支 是所有開發的基礎分支，當要新增功能時，會新增feature分支，開發完後再合併回Develop。
**Hotfix**
當master有Bug時，會緊急產生hotfix的分支修復，修完後再合併回master，也同時會合併到develop分支，為何要合併到Develop呢?因為不這樣做，當develop就會有此bug。
**Release**
當認為 Develop 分支夠成熟了，就可以把 Develop 分支合併到 Release分支，在這邊進行算是上線前的最後測試。測試完成後，Release 分支將會同時合併到 Master 以及 Develop這兩個分支上。Master 分支是上線版本，而合併回 Develop 分支的目的，是因為可能在 Release，分支上還會測到並修正一些問題，所以需要跟 Develop 分支同步，免得之後的版本又再度出現同樣的問題。
**Feature**
當要開始新增功能的時候，就是使用 Feature 分支的時候了。Feature 分支都是從 Develop 分支來的，完成之後會再併回 Develop 分支。
容易遭遇的問題：多個feature合併時容易遇到衝突，故features branch的功能最好切越小越好，並且縮短開發時程，降低衝突機率。