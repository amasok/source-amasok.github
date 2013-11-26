---
title: middlemanの導入
date: 2013-11-25 12:47 JST
tags: middleman
---

## 前提知識
* 簡単なコマンドライン操作ができる
* rubyを自分のPCにインストールするこができる
* gem,bundle installができる


## 実行環境
* mac(Mountain Lion)
* ruby(2.0.0p247)
* middleman(3.2.0)

※windowsだとあんまりうまく動かないという話をよく目にします。

## middlemanのインストール

gemからインストールするだけです。

*terminal*

~~~shell
$gem install middleman
~~~


## middlemanのコマンド

~~~
middleman build [options]           # 最終成果物を生成する
middleman console [options]         # irbが立ち上がり、rubyを直書きして実行できたり
middleman extension NAME [options]  # middlemanのプラグイン？をつくる時のやつ？
middleman init NAME [options]       # プロジェクトを生成する
middleman server [options]          # 開発時にプレビューする用のサーバをたてる
middleman upgrade                   # bundle installされたものをアップグレードする
middleman version                   # バージョンを表示
~~~


## middleman init の実行

*terminal*

~~~
> middleman init testProject

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

bundle installが実行された後middlemanに必要なプロジェクトが生成されます。

### よく触るファイルとディレクトリ

* config.rb
* sourceディレクトリ配下全部

config.rbで設定を行った後はsourceの中をごりごりいじっていきます。

## middleman server の実行

上記のようにプロジェクトを作ったら、まずは開発環境でプロジェクトを実行してみる。

*terminal*

~~~shell
$ middleman server  #middleman s でも可
~~~

http://localhost:4567/

middleman serverが立ち上がっている状態で上記URLを確認してみましょう。

![画像](middleman.png)

上記のように表示されたらOKです。


## middleman build の実行

webサイトが完成したらこのコマンドで静的ファイルを生成します。

*terminal*

~~~shell
$ middleman build  #middleman b でも可

WARN: Unresolved specs during Gem::Specification.reset:
      activesupport (~> 3.2.6)
      listen (~> 1.1)
WARN: Clearing out unresolved specs.
Please report a bug if this causes problems.
      create  build/images/background.png
      create  build/images/middleman.png
      create  build/javascripts/all.js
      create  build/stylesheets/normalize.css
      create  build/stylesheets/all.css
      create  build/index.html
~~~

なんかいろいろ作られてます。(WARNはほっといてください。めんどいだけです)
このbuild配下を全部サーバにあげればwebサイトの完成。

こういう構造になってます。

~~~
.
├── Gemfile
├── Gemfile.lock
├── build #ここのファイルをサーバにUP
│   ├── images
│   │   ├── background.png
│   │   └── middleman.png
│   ├── index.html
│   ├── javascripts
│   │   └── all.js
│   └── stylesheets
│       ├── all.css
│       └── normalize.css
├── config.rb
└── source
    ├── images
    │   ├── background.png
    │   └── middleman.png
    ├── index.html.erb
    ├── javascripts
    │   └── all.js
    ├── layouts
    │   └── layout.erb
    └── stylesheets
        ├── all.css
        └── normalize.css
~~~

## 感想

ほんとrailsっぽいって思った。（あんまりrails知らないけど）

基本的な仕組みはそんなに難しくないし、練習用にどんどん書いていこうと思う。  
ちなみに、今回この記事を書く上で一番はまった点は、このブログの記事がmiddlemanを利用した初めての画像投稿となった点でした。

markdownでの画像の投稿の仕方がわからない。  
通常道理に記述したらどのようなパスになるのかがわからない。  
等々まだまだ初心者丸出しですが、まがりなりにもブログを書くところまで至ったので、それができるようになるところまでは今後も書いていきたいと思います。


