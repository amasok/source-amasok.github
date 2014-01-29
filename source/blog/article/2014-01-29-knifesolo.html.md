---
title: knife soloの使い方
date: 2014-01-29 21:16 JST
tags: knife-solo
---

反映したいサーバにchefがはいっていない時のknife soloのコマンド。

~~~sh
$ knife solo prepare <ユーザ名@ドメイン>  
~~~

サーバに反映cookbookを反映したい時のコマンド

~~~sh
#自分のcookbookディレクトリで実行
$ knife solo cook <ユーザ@ドメイン>
~~~


たまに使うと、すぐに忘れる。。。
