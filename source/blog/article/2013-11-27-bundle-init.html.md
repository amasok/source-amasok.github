---
title: bundlerによるgemの管理
date: 2013-11-27 00:18 JST
tags: bundle, middleman
---

昨日書いたmiddlemanの導入の記事を見た友人から、

「gemをbundleで管理してないの？」  
という話をされ、  
「だってわざわざ"bundle exec"とかつけるのめんどくさいじゃんヾ(・д・｀ )」

と返したのですが、せっかくブログから生まれた話だし、やってみるかー。  
ということで、やってみました。  

## 対象者

* コマンドラインに慣れてる
* rubyをPC（Mac）にインストールできる
* gemで何かしらをインストールしたことある
* bundle installコマンドをわけわからずでも打ったことがある

## 実施環境
* mac(Mountain Lion)
* ruby(2.0.0p247)

## bundlerとは

完全に憶測で書くので間違ってたらしれっと直すかもですが。。

bundleとはgemをPCに依存せずプロジェクト毎に管理できるツールです。。


例えば、あるrailsプロジェクトがあったとして、一つは4.0系一つは3.2系を使っていたとします。  
リポジトリ管理されており、同じPC内で違うバージョンのプロジェクトをどう扱えばいいか？

そんな時にbundleが便利なようです（想像で書いてます）

あとは、共同開発しててAさんとBさんで入ってるgemのバージョンが違うとかかな。  
こっちのほうがよくありそう。  

## bundlerのインストール

*terminal*

~~~
$ gem install bundler
~~~

これだけでOK

さすがに、gemを管理するのにbundlerは入れないと動かないです。

## bundle initしてみる

プロジェクトのディレクトリを作って、とりあえずbundle initしてみましょう。  
*terminal*

~~~
$ mkdir project
$ cd project
$ bundle init
Writing new Gemfile to /Users/amasoktest3/Gemfile
~~~

するとGemfileファイルが出来上がると思います。

*Gemfile*

~~~ruby
# A sample Gemfile
source "https://rubygems.org"

# gem "rails"
~~~

今はせっかくmiddlemanをやってるので、middlemanをインストールしてみましょう。


*Gemfile*

~~~ruby
# A sample Gemfile
source "https://rubygems.org"

gem "middleman"
~~~

上記のように変更して、


*terminal*

~~~
$ bundle install --path vendor/boudle
~~~

上記コマンドでmiddlemanがインストールされます。

また、middlemanに必要な関連ファイルもすべてインストールされます。  
それらはすべて、vendor/bundle配下に格納されています。  
しかし、vendor/bundle配下はパスが通っていません。どう使うか？  
（パスを通すって何？って人は別で調べてください。）

そこで、一番はじめに書いた"bundle exec"が登場します。

*terminal*

~~~
$ bundle exec middleman init .
~~~

"init ."のドットはカレントディレクトリをさします。
今回でいうところの"project"です。

後はmiddlemanコマンドの前に"bundle exec"を全部つければ
[middlemanの導入](/blog/article/2013/11/25/middleman-init2.html)と同じにすればいいです。

また、rubyをrbenvでインストールしている方は"binstubs"てのを使って煩わしい"bundle exec"を省略できちゃうみたいです。

試してみてうまくいきそうなら、また別記事で書きます。
