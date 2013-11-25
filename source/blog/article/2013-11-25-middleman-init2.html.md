---
title: middlemanの起動
date: 2013-11-25 12:47 JST
tags: middleman
published: false
---

## 前提知識
* 簡単なコマンドライン操作ができる
* rubyを自分のPCにインストールするこができる
* gem,bundle installができる


## 実行環境
* mac(Mountain Lion)
* ruby(2.0.0p247)
* middleman(3.2.0)

## middleman install



*terminal*

~~~shell
"$middleman init testProject"

      create  testProject/Gemfile
         run  bundle install from "."
Fetching gem metadata from http://rubygems.org/........
Fetching gem metadata from http://rubygems.org/..
Resolving dependencies...
Using i18n (0.6.5)
Using multi_json (1.8.2)
Using activesupport (3.2.15)
       ・
       ・
       ・
       ・bundle install の実行
       ・
       ・
       ・
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
      create  testProject/.gitignore
      create  testProject/config.rb
      create  testProject/source/index.html.erb
      create  testProject/source/layouts/layout.erb
      create  testProject/source/stylesheets
      create  testProject/source/stylesheets/all.css
      create  testProject/source/stylesheets/normalize.css
      create  testProject/source/javascripts
      create  testProject/source/javascripts/all.js
      create  testProject/source/images
      create  testProject/source/images/background.png
      create  testProject/source/images/middleman.png
~~~

