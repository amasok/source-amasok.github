---
title: iOSアプリを実機で動かすまで
date: 2014-01-15 10:23 JST
tags: iOS
---

iOSのディベロッパー登録めんどくさいです。

http://mushikago.com/i/?p=917

こことかを見てやるといいです。

##前提条件

* iOSのディベロッパー登録を済ませておく
* シミュレータでiOSアプリを動かしたことがある

##Provisioning Profileの入手

https://developer.apple.com/

iOS Dev Center

＞ [iOS Developer Program] Certificates, Identifiers & Profiles  
＞ [iOS Apps] Provisioning Profiles  
上記をたどっていくと、
「iOS Team Provisioning Profile: *」をダウンロードしておく


##実機をxcodeに登録

今回はデバイス登録で動かすまでのmemo

* xcodeを起動
* Window -> Orgnizer(shift + command + 2)に移動
* iOSでバイスをMacとUSB接続する
* 「接続されたPCを信頼しますか？」的なダイアログがiOSでバイスで表示されるのでOKする
* Orgnizer - Devicesで接続したデバイスが認識されているかを確認する
* 「Use for Development」というボタンをクリックして全部Requestをおす
* 左のバーから「Provisioning Profiles」を選択
* 下にあるAddから先ほど入手したProvisioning Profileを追加する

## アプリを動かす

* Xcode右上の [アプリ名]　＞　iPhone(シミュレータ名)　をクリックして実際のデバイス名を選択
* ▶(Run)をクリック








