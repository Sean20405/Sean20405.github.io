---
title: 112-2 交大資工修課心得
date: 2024-09-08 17:00:00 +0800
author: Sean
categories: [ 修課心得 ]
tags: [ NYCU, 修課心得 ]
math: true
---
# 112-2 交大資工修課心得
ㄏㄏ上學期的心得一樣又拖到開學後才打完

### [必修] 計算機組織 教授：葉宗泰
#### 上課內容
RISC-V Instruction Set、Single Cycle CPU、Pipeline CPU（含實作）、Cache 簡介與設計、Memory。主要作業則是寫出 Single Cycle 和 Pipeline CPU 各一顆。

附上[課程網站](https://people.cs.nycu.edu.tw/~ttyeh/course/2024_Spring/CS10014/outline.html)

#### 上課方式
兩小時實體而已，沒有非同步。老師的簡報做得很讚，自己讀就讀的懂了，~~也因此我到後面也越來越少去了~~，但老師人蠻好的，很希望我們上課給多一點反饋（雖然都不如預期），最後期末去拿考卷的時候還會問我們對這堂課有沒有什麼建議，感覺是個很認真的老師。不過這堂是英授，有稍微感受到老師不像中文授課那麼流暢（問問題老師用中文回答的時候都蠻清楚的）。

前半堂講 CPU 的時候都是 based on RISC-V ISA，所以可能會跟其他堂不太一樣，但基本上只有細節不同而已，原理應該都一樣。

#### 評分方式
- labs*5 60%
    - 詳情可以看 [Lab 網站](https://nycu-caslab.github.io/CO2024/labs/Lab%205.html)
    - 前兩次 Lab 需要實作 Single Cycle CPU (based on RISC-V ISA)
        - 用 Verilog 寫，如果數電有學好的話其實蠻簡單的，照著給好的電路圖寫（可能小改良一下）就好了
    - 三四次則是改良成 Pipeline
        - 我覺得是 Lab 裡最難的地方了，可能要多花一點時間寫，但如果有搞懂上課講的內容，其實就是把那些概念實作出來而已
        - 每次作業都是基於上一次的 code，助教也不會提供上一次 Lab 的 sample code，所以如果自己前面寫的很亂，到後面可能會很慘
        - 這裡開始我覺得電路圖只能參考用，有些小邏輯和控制訊號要自己設計
    - 最後一次是實作 Cache Manager
        - 加分用，跟助教給的 code 比 miss count，小於就有 80 分，不過因為給的 code 是用最簡單的管理策略，所以其實蠻好超越
        - 剩下 20 分就是跟全班比，但因為當時沒什麼時間，加上分數占比沒有很重，所以我也沒有認真改良，只寫到比助教 code 好而已
- exams*2 40%
    - 從這配分應該猜得到重點不在考試，而考試內容也確實不難，期中考甚至開放可以帶筆電或平板，原本還允許上網，但後來發現有人會直接查答案，所以當場改成只能看上課簡報，但還是很佛。期末可能為了避免上網，所以只能帶大抄
    - 好險期中可以帶筆電，不然那些 opcode 和 Instruction set 不可能背起來

#### 分數
- A+

#### 評分
- Workload：3 / 5
    - Lab 其實不會很重，最重的就 Pipeline 那邊而已，考試也不會考很難
- 甜度：4 / 5
- 學到的東西：4 / 5
    - 其實寫完一顆 CPU 成就感蠻大的，尤其助教有教如何在自己寫出來的 CPU 上跑 C
- 綜合：4.5 / 5
    - 感覺是三個教授裡面最好的選擇 嗎(?)

### [選修] 人工智慧概論 教授：陳奕廷
#### 上課內容
AI 最基礎的概念，包含 Regression、Classification、Search、RL、CV 等，主要比較像介紹 AI，較少深入理論（撇除 Lab 的話還蠻像通識課的）。

#### 上課方式
2 小時實體 + 1 小時非同步。上課內容蠻少的，感覺老師主要想傳達概念，而且更多是在講 AI 的基本、趨勢、應用等。每個禮拜會有一部演講影片，每組據此提出兩個問題並試著回答，老師會挑出一些在下一堂課深入討論，接著才會進到上課內容。

原本覺得每個禮拜要看影片蠻花時間的，但後來發現挑出來的演講內容都蠻不賴，講者都是跟 AI 有關的大人物。一學期下來後認真覺得這樣的模式還不錯，因為 AI 要講可以很深，但作為大多數人的第一堂 AI 課，這樣的做法不會產生太大的負擔，也能從中學到很多。

而且老師英文講的非常流暢，聽的很舒服，老師本人也蠻有個人魅力的，很適合演講 & 教課，這學期選了同老師的影像處理，目前上起來感覺很讚，私心推這老師。

#### 評分方式
- Homework*5 60%
	- HW1: Supervised learning
	- HW2: A* search for route planning
	- HW3: Adversarial search in Pacman
	- HW4: Reinforcement learning
	- HW5: Applications of Large Language Models
	- 都不難，但蠻有用的
- Class Participation 7%
    - 就是上面講過的看影片問問題
- Final Project 33%
    - 限制不能只做 classification w/ CNN & RL on small games 和不能與前兩年的主題重疊（有給前兩年的作品參考），除此之外好像就沒有其他限制了，比起另一班只能做 LLM 自由很多
    - spec 給的蠻詳細的，照著做就不會有太大問題
    - 最後兩班會各選五組參加 workshop，最後選幾組得獎，但我們這組沒進所以就不知道其他細節了

#### 分數
- A+

#### 評分
- Workload：3 / 5
    - 除了 final project 以外都蠻輕的
- 甜度：4.5 / 5
    - 平均 90
- 學到的東西：4.5 / 5
    - 演講影片可以學到蠻多想法
    - HW 學到基本實作 & 概念
    - final project 實際經歷訓練 AI 的流程（找 dataset、train、evaluation...）
- 綜合：5 / 5
    - 老師很讚，也能學到東西，基本上這堂課也算資工系的必選修了

### [選修] 正規語言概論 教授：陳穎平
#### 上課內容
Some kinds of Automata & Grammar & Language (Finite Automata, Regular Languages, Context-Free Grammars...), Turing Machines, Decidability, Reducibility, Time Complexity, P, NP, NP-Completeness...

修之前我也不確定這堂課的內容，但修完我覺得他像是現代 CS 底層及背後的數學模型，前面先建構這些模型（Automata、Language 那部分），接著講說每個問題（如 SAT、Hamiltonian path 等）都可以對應到一個 Automata，再用先前學的知識分析這些問題，看是否可解、花費如何。會講一些你可能有聽過，但一直不知道是什麼的酷東東。

開在碩班的課叫正規語言與計算理論，我覺得這可能比較好理解。

#### 上課方式
2 堂實體 + 1 堂非同步，老師會放去年的上課影片，跟今年的上課內容一模一樣，~~所以可以直接看影片~~，在這裡不得不讚嘆老師控進度的能力，基本上實體的兩堂課上課內容會完全對應到兩部影片，所以剩下一堂非同步就是下部影片，下一次實體就會從第四部影片的內容開始，我第一次遇到能完全照進度上課的老師。

沒記錯這個老師教正規語言很久了，感覺對這個主題非常熟悉（老師實驗室本身也是在做類似領域的啦），上課會用一些簡單例子讓我們理解比較複雜的數學概念，而且下課去問老師問題的時候也能快速抓到問題的癥結點，跟之前資料庫的老師蠻像的，總之蠻推這個老師的，真的教得很好。

#### 評分方式
- Mid-term #1 30%
- Mid-term #2 30%
- Final 40%
    - 對 全考試，我覺得第二次最難，不過和數電一樣，跟考古**非常**類似，所以蠻好準備的

#### 分數
- A+

#### 評分
- Workload：3.5 / 5
    - 應該說，這堂算純理論課，所以需要花一點時間理解
- 甜度：3 / 5
    - 考試好準備
    - 不過看平均好像才 6 70 嗎(?)，忘記有沒有調分了
- 學到的東西：3.5 / 5
    - 說真的，可能實用度較低，但認真很酷（至少我學得很有興趣）
- 綜合：4.5 / 5
    - 老師第一堂課就說這算是資工系獨有的課，修完我也蠻推薦資工系都要修，可以認識平常在做的事，他背後的基礎或理論支撐
    - 學到很多聽過但不知道是什麼的東西，如 P&NP problem、SAT、Turing Machine
    - 而且老師很會教

### [選修] 強化學習原理 教授：謝秉均
#### 上課內容
前面先講一些 RL 的基礎，接著會介紹各種 RL 以及一些演算法，詳細可以看這張上課簡報，幾乎涵蓋整學期會上到的演算法。而同時幾乎每個演算法都是一篇論文，所以這堂課也順便整理了 RL 的沿革。

![](/assets/img/post/112-2CourseReview/RL_algo_table.png)

#### 上課方式
三堂全實體，理論課，主要探討演算法背後的數學支撐。跟機率一樣，老師很讚，但偏硬，雖然老師講的很清楚，不過可能因為我沒有 RL 的基礎，加上這堂課很理論，初期上課常常無法立即聽懂，課後花了很多時間讀，但前期讀懂後，感覺有比較了解 RL 在幹麻，就比較輕鬆了。

雖然說一個演算法約等於一篇論文，但老師整理得很好，包含這篇論文出現的原因、簡介、一些重要的數學定理、主要貢獻等，如果想走 RL 還蠻適合把這堂課當作入門，可以省去很多讀文獻的時間。

不知道是不是因為這是老師的本科，跟機率比起來他教得更有熱忱，上課也講得很開心。

#### 評分方式
- Homework*3 35%
    - 跟機率一樣皆含手寫及 coding，但 coding 的比重更重
    - 手寫通常是證明一些上課略過的定理，會需要回去看原論文（~~或自己想~~）
    - coding 則是實作演算法，會用到一點 ML（訓練模型），這部分蠻花時間的，而且我先前其實沒寫過 ML，所以等於我也從頭學了 pytorch，~~賺~~。training 需要花不少時間，所以建議早點開始寫讓他每天晚上慢慢跑
- Theory Project 30% (Hackmd Blogpost: 20%, Reviews: 10%)
    - 讀一篇 theory paper 並寫成 blog，有給清單也可以自己挑，簡單來說有點像是整理 + 提出問題
    - 建議早點做，因為是 theory paper 所以需要花時間理解裡面的數學式，感覺每篇的數學推導都蠻多的，而且為了讀懂一篇，可能要回去翻 previous work，所以最後也看了不只一篇
    - Review 則是看別人的 blog 並給回饋
- Team Implementation Project 35%
    - ablation study，想辦法增減一些小東西來改善原演算法，最後要寫一份比較正式的書面報告和上台
    - 原本覺得很難，但實際做發現其實還好，而且助教給的 instruction 蠻仔細的，幾乎可以無腦照做。也因為是 ablation study 所以可以不用有太創新的想法（但也有些組別的做法超酷），主要時間反而是花在訓練 model 上，也是這堂課讓我一直抱怨文書筆電

#### 分數
- A+

#### 評分
- Workload：4.5 / 5
    - 比機率重，前期可以算 5，後期好一點
- 甜度：4.5 / 5
    - 其實意外的分數很好
- 學到的東西：4.5 / 5
    - 超扎實，而且我還趁機學了 ML
- 綜合：3.5 / 5
    - 當初主要是看老師選的，因為課程蠻專業的，有興趣再修就好，就沒那麼推薦了
    - 但如果不知道要修什麼還是可以修，我覺得不會後悔

### [領域] 國際關係 教授：邱奕宏
#### 上課內容
國際政治的理論，主要是各種主義（現實主義、自由主義等）。

#### 上課方式
跟國際政治經濟學一樣，可以直接去看 [之前寫的](https://sean20405.github.io/posts/nycu-111-1-course-review/#%E9%A0%98%E5%9F%9F-%E5%9C%8B%E9%9A%9B%E6%94%BF%E6%B2%BB%E7%B6%93%E6%BF%9F%E5%AD%B8-%E6%95%99%E6%8E%88%E9%82%B1%E5%A5%95%E5%AE%8F)。

#### 評分方式
- 上課參與及課堂討論 20%
- 期中考試 30%
- 學期報告 25%
    - 跟之前都一樣
- 分組報告 25%
    - 這學期老師讓我們決定要做模擬 APEC 或單純分組上台報告，結果選上台報告的人比較多QQQQQ，這是我選這堂課的動力ㄝ，也算是這個老師的招牌吧，沒了很可惜，也導致這堂最後修的沒有很開心

#### 分數
- A+

#### 評分
- Workload：2 / 5
- 甜度：4 / 5
- 學到的東西：2.5 / 5
- 綜合：2.5 / 5
    - 主要分組報告改成上台報告，不然心得應該會跟國政經一模一樣

### [領域] 腦科學看人文與社會 教授：謝仁俊
#### 上課內容 & 方式
每堂課會找不同領域的人來演講，主題都是腦科學與 XXX，詳細可以看 [課程時間表](https://timetable.nycu.edu.tw/?r=main/crsoutline&Acy=112&Sem=2&CrsNo=561080&lang=zh-tw)，領域都蠻廣泛的，很適合當通識，有些講者講的也不錯，偶爾也會融入如死刑等時事。

相較之下我比較不習慣這堂的開課老師，有時候會問一些問題而導致大超時，雖然可能是為了給講者回饋，但既然演講時間到了就該停下吧。並且有一堂課主題是「誰劫奪了笛卡爾的腦袋？-醫學科學的疆界-」，上課內容跟他之前出過的書有關，主要是有關靈媒的，但我覺得那堂課太像在傳（ㄒ一ˇ）教（ㄋㄠˇ），之後就對他的印象不是很好。

#### 評分方式
- 隨堂小問答 70%
    - 課後寫表單回饋就好
- 期末報告 30%
    - 給定題目寫報告
    - 今年的題目：以一個理性公民的素養（不以政黨傾向，而以法案本質），你會如何分析、看待及思辨出最近的國會改革法案事件與目前部分團體圈圍國會塑造政治壓力事件的 the first principle 及處理（如果你有能力），從而你會建議政治神經科學（political neuroscience）/ 神經政治學（neuropolotics）未來應該研究的課題
    - 當時我寫的蠻上頭，剛好那時有時間 + 對這議題有興趣。但撇開主題外這就是一篇正常的報告

#### 分數
- A+

#### 評分
- Workload：1 / 5
- 甜度：5 / 5
    - 看那評分標準就知道又涼又甜
- 學到的東西：3 / 5
    - 以通識來說算還不錯
- 綜合：2 / 5
    - 老師問題😵‍💫

### [素養] 數據與日常生活 教授：彭松嶽
#### 上課內容 & 方式
一些跟數據有關的 內容(?)，~~我好像沒有很認真上課~~，所以有點忘ㄌ

#### 評分方式
 ![](/assets/img/post/112-2CourseReview/Overall_wrapped.png){: .w-25 .right}
- 專案口頭報告 30%
    - 含提案 15 分 + 期末簡報 15 分
    - 主題：數據與我，探討自身與數據的關係
    - 其實我做的蠻開心的，我去拿 Spotify 的資料，分析從以前到現在我最常聽的歌和歌手，最後搞出了這張圖ww
    - 但因為要跟上課內容有關，所以我掰了一些這背後衍伸的議題（推薦演算法、同溫層等等）
- 專案書面報告 20%
    > 請以個人的專案出發，嘗試說明你如何運用課程內容理解專案中觀察到之不同數據與個人關係，及探討這樣的關係是否在其他社會場域當中發生？可能或已經產生哪些影響？
- 課程閱讀回饋 20%
    > - 針對當週指定閱讀的內容提出討論，認同、反對、或補充等觀點
	> - 運用自身觀察與案例協助說明前述觀點
	> - 鼓勵彙整同組同學觀點的異同
	> - 探討與理解這些造成差異的因素
- 作業*2 15%
    - Data about Me
        > 哪些可能紀錄了自己的數據
    - Data Fantasies
        > 數據如何能協助生活與社會變得更完美的文字、圖片或影音資料，並嘗試思考這些論述可能忽略的面向或是可能導致的問題
- （剩下的不確定了，可能是課堂參與和討論）

#### 分數
- A+

#### 評分
- Workload：1.5 / 5
- 甜度：2.5 / 5
- 學到的東西：2 / 5
- 綜合：3 / 5