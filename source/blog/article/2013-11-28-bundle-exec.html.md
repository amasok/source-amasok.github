---
title: bundle execの省略が微妙
date: 2013-11-28 01:00 JST
tags: bundle
---

結論から書くと、僕が望んでいた形ではインストールできませんでした。

僕が望んでいた形は、

* gemをグローバルな領域にインストールしない(path=vendor/bundleを使用)
* プロジェクト配下のディレクトリならどの階層でも”bundle exec”を省略できる

今回は、僕が調べたことを３つ記していこうかと思います。
よかったら試してみてください。


## 対象者

* bundleを使って"bundle exec"を毎回打ってる人

## 実行環境

* mac(Mountain Lion)
* ruby(2.0.0p247)

## rbenv-binstubsを使う

### 制限事項

* rbenvを使ってrubyを管理している
* bundle installはグローバルな領域にインストールする（pathは指定しない）

### 方法

*terminal*

~~~
$ cd
$ mkdir .rbenv/plugins
$ cd .rbenv/plugins
$ git clone git://github.com/ianheggie/rbenv-binstubs.git
~~~

上記のようにrbenvのプラグインとしてrbenv-binstubsてのを導入

*terminal*

~~~
$ bundle install --binstubs=vendor/bin
$ rbenv rehash
$ middleman s
~~~

上みたいに、bundle install --binstubs=bendor/binでgem自体はグローバルな領域で作るけど、バイナリ（コマンド）ファイルはプロジェクトディレクトリ内で作る。

これならプロジェクト内のどの階層でもbundle execが必要なくなるけどgemがグローバルな領域で存在しつづけてしまう。

## binstubsで作ったbinにパスを通す

### 制限事項

* プロジェクトディレクトリの第一階層のみで省略可（プロジェクトディレクトリ内のより深い階層からは省略不可）

### 方法

*terminal*

~~~
$ export PATH=./vendor/bin:$PATH
~~~

上記パスを通した後、下記のようにbundle install時にオプションを指定

~~~
$ bundle install --path=vendor/bundle --binstubs=vendor/bin
~~~

はい、この方法でプロジェクトのディレクトリの第一階層上でのみbundle execを省略できます。  
なんか、うまいパスの通し方ないかなぁ。。  
うまくいくと、このやり方の応用が一番なんとかできそうだけど。。  

## aliasをかける

### 制限事項

* 文字数が少なければOK（完璧に省略する必要はないと考える人）

### 方法

書くまでもないかな。。。

*.bash_profile*

~~~
alias be='bundle exec'
~~~

はい、これで

*terminal*

~~~
$ be middleman s
~~~

とかができるようになりました。  
どれもいまいち腑に落ちないけど、今のところ調べた結果のログとして記します。  
なんか良い方法見つけたら新しく書こう。  
てか、誰か良い方法教えてほしい。  



#### 参考

http://blog.takapra.com/2013/04/ruby-bundler-basic/

http://qiita.com/naoty_k/items/9000280b3c3a0e74a618
