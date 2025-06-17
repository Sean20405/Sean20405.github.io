---
title: 把 PowerShell 變得更 Zsh 一樣好用！
date: 2025-06-17 23:13:00 +0800
author: Sean
categories: [ 技術分享 ]
tags: [ powershell, zsh, development ]
math: true
summary: ㄏㄏ上學期的心得一樣又拖到開學後才打完
---

![](/assets/img/post/powershell/demo.gif) 

Zsh 的好用應該大家都知道，有很多好用的 plugin 如 [Oh My Zsh](https://ohmyz.sh/)、[zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) 等等，也有很多 [中文的教學文](https://www.kwchang0831.dev/dev-env/ubuntu/oh-my-zsh) 帶你一步一步把終端機變好看。但 PowerShell 相關的文章卻很少，中文資源甚至比~~日本製的壓縮機還稀少~~，當初趁著學期間沒作業之餘，把自己的 PowerShell 弄得好用一點，於是就有了這篇文的誕生。  
<small>但其實本來是想用完馬上寫的，結果沒想到用完後事情一個接著一個來，就被我拖到現在了 : ( <small/>

主要會將 PowerShell 裝上 Oh My Posh 並套用主題，接著加上 autosuggestion 和 syntax-highlight 的功能，讓他變得跟 Zsh 一樣好用！

### 安裝 Nerd Font

因為接下來使用的主題會有特殊 icon，因此需要將字體替換成 [Nerd Fonts](https://www.nerdfonts.com/)，也可以最後設定好發現有些符號顯示不出來再裝。相關字體網路上有很多，這裡提供一個 [官網列的字體表](https://www.nerdfonts.com/font-downloads)，找自己喜歡的就可以，我個人是用 MesloLGS NF。

下載四個不同字重的 .tff，如果用不到粗體或斜體的話，可以只載第一個

- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

接著照著平常安裝字體的流程安裝就好，在大部分的作業系統只需要點開檔案並點擊「安裝」就好

### 設定 PowerShell 字型

打開 Windows 終端機，點擊上方 tab 的下拉式選單 `⌵` > 設定 > Windows PowerShell > 外觀 > 字體，更換成剛剛想要的字體即可

![](/assets/img/post/powershell/powershell_setting.png)

### 下載 Oh My Posh

1. 方法一：winget
```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

2. 方法二：Microsoft Store
https://apps.microsoft.com/detail/xp8k0hkjfrxgck?mode=mini

3. 其餘方法：manual、chocolatey
參照 [Oh My Posh 官方文件](https://ohmyposh.dev/docs/installation/windows#installation)

下載後，可以利用 `oh-my-posh version` 確認是否安裝成功（需重啟 Powershell 以更新環境變數），正確安裝會顯示版本號（e.g. 24.8.0）

> 未來若需更新版本
> ```powershell
> winget install JanDeDobbeleer.OhMyPosh -s winget
> ```
{: .prompt-tip }

### 設定 Shell 使用 Oh My Posh

編輯自己的 Powershell 設定檔，可於 Powershell 中輸入 `$PROFILE` 查看設定檔位置。  

> 若該檔案未存在，可利用以下指令建立
> ```powershell
> new-item -type file -path $profile -force
> ```
{: .prompt-tip }

開啟設定檔，並在最後一行加入

```
oh-my-posh init pwsh | Invoke-Expression
```

如此便能讓 Powershell 裝上 Oh My Posh。

### 設定主題

先到尋找自己想要的主題，可上 [官網](https://ohmyposh.dev/docs/themes) 查看或利用 `Get-PoshThemes` 直接在 Powershell 中預覽。

選定好主題後，將上述命令改為

```
oh-my-posh init pwsh --config "path\to\your\theme\config" | Invoke-Expression
```

其中主題設定檔的位置可利用 `$env:POSH_THEMES_PATH` 此環境變數確認。

最後重新載入 Powershell 就可以看到效果了

```powershell
. $PROFILE
```

註：因為後續有些額外的需求（顯示 git branch 及當前 conda 環境等等），加上用一段時間後發現用不到一些預設顯示的資訊，因此有稍微研究如何撰寫主題的設定檔，詳細內容請見下一篇<small>（有生之年一定寫）</small>。

### Auto Suggestion - [PSReadLine](https://github.com/PowerShell/PSReadLine)

這是一個 Powershell 很好用的 module，裡面提供了很多功能與擴充性，如這篇會提到的 Auto Suggestion 就是他能做到的功能之一。

首先需要先安裝此套件

```powershell
Install-Module PSReadLine
```

接著打開 `$PROFILE` 開始進行設定，將以下內容加進 `$PROFILE`

```powershell
# Auto Suggestion
Import-Module PSReadLine
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward
Set-PSReadLineOption -Colors @{ InlinePrediction = '#666666'}
Set-PSReadLineKeyHandler -Chord "Ctrl+RightArrow" -Function ForwardWord

# Auto Complete
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
```

- 第四行：最近新增的功能，有兩種模式 ListView 及 InlineView，預設可利用 F2 切換，詳細效果如下  
![](/assets/img/post/powershell/PSReadLine_inlineview.png)  
![](/assets/img/post/powershell/PSReadLine_listview.png)
- 第六、七行：綁定上下鍵來選擇歷史指令
- 第八行：設定預測的顏色（此設定為灰色）
- 第九行：允許使用 Ctrl + 右鍵，僅接受預測的第一個字
- 第十二行：按下 Tab 以提供選單  
![](/assets/img/post/powershell/PSReadLine_Menu.png)

官方也有提供 [參考範例](https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/SamplePSReadLineProfile.ps1)，當中有更多功能的設定方法，可自行參考。

### Reference

- [Windows \| Oh My Posh](https://ohmyposh.dev/docs/installation/windows)
- [Windows 終端機自訂提示設定 \| Microsoft Learn](https://learn.microsoft.com/zh-tw/windows/terminal/tutorials/custom-prompt-setup)
- [digitalguy99/pwsh-syntax-highlighting: zsh-syntax-highlighting for PowerShell.](https://github.com/digitalguy99/pwsh-syntax-highlighting)
- [PowerShell/PSReadLine: A bash inspired readline implementation for PowerShell](https://github.com/PowerShell/PSReadLine)
- [Announcing PSReadLine 2.1+ with Predictive IntelliSense - PowerShell Team](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/?WT.mc_id=-blog-scottha)