---
title: webViewを継承しているclassでscrollViewのメソッドを使う時のメモ
date: 2014-03-18 05:26 JST
tags: Objective-C
---

簡単なんだけど、最初よくわからなかったのでメモ

test.h

~~~c
//UIScrollViewDelegateをデリゲート？する。

@interface webtest : UIWebView <UIScrollViewDelegate>

@end

~~~


viewDidLoad内でsubScrollViewを許可。

test.m

~~~c

- (void)viewDidLoad
{
    [super viewDidLoad];

    self.subScrollView.delegate = self;

}

~~~

これによってUIScrollViewDelegate内のメソッドが使えるようになる。
