---
title: 【Objective-C】カスタムセル内の状態を永続化(保存)させたい
date: 2014-03-18 00:18 JST
tags: Objective-C
---


以下のやり方でできました。 永続化させるためにNSUserDefaultを使用する。

カスタムセル用クラスcell.mにて セル毎にユニークなIDを取得できるようsetterを作成する。

ユニークな文字列は自分で生成する。

~~~c

//   #indexPath=セル毎に割り振られたユニークな文字列
- (void)setIndex:(NSString *)indexPath{
    //indexPathをインスタンス変数化
    index = indexPath;
    //NSUserDefaultsを生成
    NSUserDefaults *checkDefaults = [NSUserDefaults standardUserDefaults];
    //NSUserDefaultからindexをキーに値を取得する
    NSString *check = [checkDefaults stringForKey:index];
    if (check != NULL){//値があればその値をボタンにセット
        [_checkButton setTitle:check forState:UIControlStateNormal];
    }else{//値がなければデフォルトの◯をセット&◯をindexをキーとしてセット
        [_checkButton setTitle:@"◯" forState:UIControlStateNormal];
        [checkDefaults setObject:@"◯" forKey:index];
    }
}
//ボタンをタップした時の処理

- (IBAction)checkAction:(id)sender
{
    #NSUserDefaultsを生成
    NSUserDefaults *checkDefaults = [NSUserDefaults standardUserDefaults];
    #ボタンにセットされている文字列ば☓なら◯を、◯なら☓の文字列を変数checkに取得。
    NSString *check = [_checkButton.titleLabel.text isEqual: @"☓"] ? @"◯" : @"☓";
    #NSUserDefaulsでcheckをindexをキーとしてセット
    [checkDefaults setObject:check forKey:index];
    #ボタン名にcheckをセット
    [_checkButton setTitle:check forState:UIControlStateNormal];
}

~~~
