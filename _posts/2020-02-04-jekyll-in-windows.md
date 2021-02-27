---
layout: post
title:  "在Windows上用Jekyll架設自己的Blog"
author: Sean
categories: [ 教學 ]
tags: [ Website, Jekyll, Cmder, Github Page ]
disqus: false
---

既然這是這個網站的第一篇文章，那我就來記錄架設過程以及我遇到的問題吧

### Why Jekyll?
原先的構想是自己刻一個HTML+CSS再放上Github，但寫了一些之後發現有夠麻煩，排版困難而且還要設定一堆連結，便想說先去搞定Github的那部份好了，找了找資料，找到[這篇](https://minglun-wu.medium.com/%E5%BB%BA%E7%AB%8B%E4%B8%80%E5%80%8B%E5%B1%AC%E6%96%BC%E8%87%AA%E5%B7%B1%E7%9A%84-%E7%A8%8B%E5%BC%8F-%E9%83%A8%E8%90%BD%E6%A0%BC-4d295ed96236)，沒想到還有Hexo這種東西，然而，在我建好Github Page時官方的文件又寫到Jekyll，於是我再度找他們的差異，最後卻選擇了Jekyll，原因是大部分的資料都指出Jekyll的社群較廣，雖然不像Hexo有較多中文社群，但看點英文網站應該不會對我造成太大的負擔，所以我就選了Jekyll（到後面真的遇到蠻多問題的...大部分還是得看其他人在Github或Stack Overflow的回答才解決）

好的，以下正文開始

### 創建Github Page
> 名稱：Github
> 網址：https://github.com/

先到Github註冊，然後它會出現一頁表單，問關於你的一些事情，如下圖，填不填都可（我是有填啦，方便他以後投放一些我有興趣的廣告）

![](https://i.imgur.com/zhj3tWS.png)

接著一般註冊流程結束後，創建資料庫(Ｃreate Repository)，如下圖，記得Repository Name要是`[User name].github.io`（中括號裡填自己的使用者名稱），下面設定一下，Done！

其實這裡已經可以開始架設了，Settings裡也有一些內建的主題，但我想要讓他好（ㄕˇ）看（ㄩㄥˋ）一（ㄇㄛˊ）點（ㄅㄢˇ），所以以下會是Jekyll的使用和主題使用

### 建置Jekyll環境
> 名稱：Jekyll
> 網址：https://jekyllrb.com/
> 文件（For Windows）：https://jekyllrb.com/docs/installation/windows/
> 功能：靜態網站產生器
> 特色：（對我來講）方便，支援 markdown

原本我在那邊試超久，試到懷疑是不是該架好我的Linux虛擬機，但我又很不想要，因為不常開可能會讓我降低發文章的動力，後來耐心一點仔細去看官方文件，才知道要先下載Ruby（笑），所以我要先離開這個小標題進到下載Ruby等等再回來

#### 下載Ruby
> 名稱：Ruby
> 網址：https://rubyinstaller.org/downloads/

下載WITH DEVKIT的，接著就跟著指示，同意該同意的，接著會自動打開一個類似cmd的東東，就照著上面指示（我都下載第一個的）

#### 下載Cmder
> 名稱：Cmder
> 網址：https://cmder.net/
> 功能：在 Windows 上執行 Linux 的終端機指令

因為 Windows 內建的命令提示字元功能很少，且網路上連官方文件的教學都是以Linux為主，所以便找到了這個程式，不用架 Linux 虛擬機就能解決。

進去官網後會看到兩個下載的地方，Mini 是不含一些 git 工具的，所以如果你的電腦本身就有下載過 git，在這裡下載 mini 版就好了（檔案小很多）。

> [color=#d80808]注：最新版本都是 for 64bits 的，所以如果你的電腦是 32bits，請下載 v1.3.4。
> 參考：https://github.com/cmderdev/cmder/issues/1699

#### [選] 找主題
網路上其實多 Jekyll 的主題，這裡列了幾個網站，當然你也可以自己找到你更喜歡的

> http://jekyllthemes.org/
> https://jekyllthemes.io/

官方文件中也有[相關頁面](https://jekyllrb.com/docs/themes/)

#### 正式開始建置
打開Start Command Prompt with Ruby，輸入以下指令：

更新gem
```
$ gem upgrade
```
下載jekyll & bundler
```
$ gem install jekyll bundler
```
檢查版本（順便確認是否成功下載）
```
$ jekyll -v
```

<---------------------------------------接著以下在 Cmder 執行--------------------------------------->

clone 主題（這裡以一個在 http://jekyllthemes.org/ 找到的主題 [Memoirs](https://bootstrapstarter.com/bootstrap-templates/jekyll-theme-memoirs/) 為介紹）
```
$　git clone https://github.com/wowthemesnet/jekyll-theme-memoirs.git
```
移進主題的資料夾
```
$ cd jekyll-theme-memoirs
```
安裝bundle
```
$ bundle install
```
在本機端執行
```
$ bundle exec jekyll server --watch
```

如果 Cmder 出現以下訊息，便代表成功了！然後就可以去訊息給的網址看成果了

![](https://i.imgur.com/dFfIkuG.png)

### 參考網站：
* https://minglun-wu.medium.com/%E5%BB%BA%E7%AB%8B%E4%B8%80%E5%80%8B%E5%B1%AC%E6%96%BC%E8%87%AA%E5%B7%B1%E7%9A%84-%E7%A8%8B%E5%BC%8F-%E9%83%A8%E8%90%BD%E6%A0%BC-4d295ed96236
* https://jekyllrb.com/docs/installation/windows/
* https://stackoverflow.com/questions/10012181/bundle-install-returns-could-not-locate-gemfile

### 遇到問題彙整
1. 無法執行`$ bundle install`
   sol：移進專案資料夾，再執行一次
   url：https://stackoverflow.com/questions/10012181/bundle-install-returns-could-not-locate-gemfile
   
2. 無法執行`$ bundle exec jekyll server --watch`
   原因可能有很多，以下舉我遇到的一個問題
   
   <img src="https://i.imgur.com/IGmL2tv.png" width=600 height=750 />
   
   黃框中寫道找不到 webrick 這個檔案，而實際去看檔案會發現最上面有一個`require "webrick"`，然後就去找找到了以下解法
   sol：輸入`bundle add webrick`
   url：https://github.com/jekyll/jekyll/issues/8523

### 下篇預告
可能會做此主題的詳細介紹（資料夾、檔案等等）