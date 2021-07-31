---
layout: post
title:  "懶人神器！自動填體溫 讓你不再被記警告(By Python)"
author: Sean
categories: [ Bot ]
tags: [ Python, selenium, heroku ]
disqus: false
---

覺得每天早上都要打開瀏覽器填體溫很麻煩嗎？因此被記的警告多到消不完嗎？那這肯定是你脫離苦海的最佳解藥！安全、可靠、穩定的機器人上線啦，於每天早上的隨機時間（當然在限定時間內），填報合乎正常範圍的隨機體溫，就算被稽查也不用怕，甚至會根據新系統發布更新（v.1.1.0：新增破解驗證碼），有興趣？歡迎私訊獲得更多資訊！

### 開發緣由

其實實施線上填體溫這個制度已經快一年了，但因為那時工程師（或老師？）新增了驗證碼希望解決機器人，激起了我想挑戰的衝動(?)，因此便著手開發。

### Selenium 簡介
一套瀏覽器自動化的工具，爬蟲的利器。可自動開啟瀏覽器，執行似人的點選、滾度、輸入等，也可取得網頁資訊，並進一步分析（常搭配 BeautifulSoup 一同使用）

### heroku 簡介

常被用來架設網站，而這次被用來當作線上執行程式碼的地方（需要先設置環境變數，如參考1）

直接上程式碼吧

### 程式碼

```py
from selenium import webdriver
from selenium.webdriver.support.select import Select
import os
import sys
import random

# set up
options = webdriver.ChromeOptions()
options.binary_location = os.environ.get("GOOGLE_CHROME_BIN")
options.add_argument("--headless")
options.add_argument("--disable-dev-shm-usage")
options.add_argument("--no-sandbox")

# build driver
driver = webdriver.Chrome(executable_path=os.environ.get("CHROMEDRIVER_PATH"), options=options)
driver.get("https://webap1.kshs.kh.edu.tw/kshsSSO/publicWebAP/bodyTemp/index.aspx")

# find the security number (string security_code)
secutity_number = driver.find_element_by_id("ContentPlaceHolder1_lbN").text

# send security number
i=0
while True:
    select = driver.find_element_by_id(f'ContentPlaceHolder1_RadioButtonList1_{i}')
    value = select.get_attribute("value")
    if secutity_number == value:
        select.click()
        break
    i+=1
    if i > 100: # protection mechanism
        driver.close()
        sys.exit()

# send ID and submit
ID = driver.find_element_by_id("ContentPlaceHolder1_txtId")
ID.send_keys("<MYID>")
submit_1 = driver.find_element_by_name("ctl00$ContentPlaceHolder1$btnId")
submit_1.click()

# send info
ways = driver.find_element_by_id("ContentPlaceHolder1_rbType_1")
ways.click()

temp_1 = driver.find_element_by_id("ContentPlaceHolder1_ddl1")
Select(temp_1).select_by_value("36")

temp_2 = driver.find_element_by_id("ContentPlaceHolder1_ddl2")
Select(temp_2).select_by_value(str(random.randint(4, 8)))

attendance = driver.find_element_by_id("ContentPlaceHolder1_ddl3")
Select(attendance).select_by_value("1")

submit_2 = driver.find_element_by_id("ContentPlaceHolder1_btnId0")
submit_2.click()

# Close window
driver.switch_to.alert.accept()
driver.close()
sys.exit()

# DONE!
```

### 運作邏輯

就跟一般使用一樣，只是因為要放上 Heroku 所以前面須設定一些東西，找驗證碼的部分就慢慢找，先找到驗證碼再去跟選項中的比對，如果一樣就選那個選項，之後就是普通的填表單、Submit。

其中還下了一些安全機制（迴圈跑太多次就自動結束程式），防止網站的 id 等等跑掉，抓不到導致無限迴圈或一些奇怪的 Bug。

### 轉折？

然而就在我寫好的一個禮拜後，那時候的我還在搞定 Heroku 排程的問題，並且順便用手動執行程式看看有沒有神奇的 Bug（Heroku 有內建 Console 能在上面執行），結果，結果，系統突然開始換題目QAQ，不僅每天題目不一樣，甚至還有不同形式！！！ 之前用 click 就可以了，那時還多了下拉式選單。

但其實還算好解決，一個方法是我乖乖觀察個幾個禮拜，找出規律再寫，第二個就是 trial and error，然後再將答案存到資料庫遇到同樣的問題時直接抓答案，反正不限次數，況且又交給程式跑。然而，某一天突然出現了一題，「你是否有萬華等地之接觸史？」（當時恰逢萬華疫情剛爆發），無論填是或否都會過，但如果填是的話會被約談（還好那時候我還在觀望），之後我也不敢用第二種方法了。

觀察個幾天後，疫情愈來越嚴重，基於良心的譴責我也把這機器人關掉了。接著，「政府宣布發布三級警戒，高中職及以下學生停課！」好喔，看來用不到了呢：）

### 未來

* 把排程設定好
* 解決換題目的問題
* 製作手機 GUI，更容易推廣給其他人而不需洩漏身分證字號

### Reference

[Heroku 中使用 selenium 設定方法](https://aishuafei.com/heroku-selenium/)

[動態網頁爬蟲第一道鎖 — Selenium教學：如何使用Webdriver、send_keys(附Python 程式碼)](https://medium.com/marketingdatascience/selenium%E6%95%99%E5%AD%B8-%E4%B8%80-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8webdriver-send-keys-988816ce9bed)