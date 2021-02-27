---
layout: post
title:  "在Windows上用Jekyll架設自己的Blog 精簡版"
author: Sean
categories: [ 教學 ]
tags: [ Website, Jekyll, Cmder, Github Page ]
disqus: false
---

因為我覺得我上一篇好像打太多廢話了，所以整理了架設的重點

#### 創建 github page
URL：https://github.com/
創建資料庫(Ｃreate Repository)，名稱：`[User name].github.io`（中括號裡填自己的使用者名稱）

#### 下載Ruby
URL：https://rubyinstaller.org/downloads/
載 WITH DEVKIT 的

#### 下載Cmder
URL：https://cmder.net/
mini 版無 git 工具

#### 找主題
URL：http://jekyllthemes.org/ or https://jekyllthemes.io/ or ant others.

#### 打指令
##### in "Start Command Prompt with Ruby"
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
##### in "Cmder"
clone 主題
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
# DONE！