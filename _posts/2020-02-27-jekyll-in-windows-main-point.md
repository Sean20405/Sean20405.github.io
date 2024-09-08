---
title: 在 Windows 上用 Jekyll 架設自己的 Blog - 精簡版
date: 2020-02-27 18:00:00 +0800
author: Sean
categories: [ 教學 ]
tags: [ Website, Jekyll, Cmder, GitHub Page ]
summary: 因為我覺得我上一篇好像打太多廢話了，所以整理了架設的重點
---

因為我覺得我上一篇好像打太多廢話了，所以整理了架設的重點

### 創建 GitHub Page
URL：[https://github.com/](https://github.com/)  
創建資料庫(Ｃreate Repository)，名稱：`[User name].github.io`（中括號裡填自己的使用者名稱）  

### 下載 Ruby
URL：[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)  
載 WITH DEVKIT 的

### 找主題
URL：[http://jekyllthemes.org/](http://jekyllthemes.org/) or [https://jekyllthemes.io/](https://jekyllthemes.io/) or any others.

### 打指令
##### in "Start Command Prompt with Ruby"
更新 gem
```shell
gem upgrade
```
下載 Jekyll & bundler
```shell
gem install jekyll bundler
```
檢查版本（順便確認是否成功下載）
```shell
jekyll -v
```
##### in "Powershell"
clone 主題
```shell
git clone https://github.com/wowthemesnet/jekyll-theme-memoirs.git
```
移進主題的資料夾
```shell
cd jekyll-theme-memoirs
```
安裝 bundle
```shell
bundle install
```
在本機端執行
```shell
bundle exec jekyll server --watch
```
### DONE！