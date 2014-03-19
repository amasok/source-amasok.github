---
title: 【iOS】上にスクロールした時だけバーを表示する
date: 2014-03-19 19:20 JST
tags: Objective-C, iOS
---


1.上にスクロールした時だけバーを表示する  
2.下にスクロールした際はバーを非表示にする  
3.一番下までスクロールした際のバウンス時はバーを非表示にする  


~~~c

//scrollしている間呼び出され続ける
- (void)scrollViewDidScroll:(UIScrollView *)scrollView
{
	//scrollした位置を取得する
    CGPoint currentPoint = [scrollView contentOffset];

    //上にスクロールした場合にバー(_tabBar)を表示する
    _tabBar.hidden = scrollBeginingPoint.y < currentPoint.y ? YES : NO;
    

    //バウンスした際にhiddenが解除されてしまうので、
    //scrollViewの一番下までスクロールした際にバーを削除する
    //scrollView.bounds.size.height=画面サイズ
    //scrollView.contentOffset.y=スクロールした位置

    int viewSize = scrollView.bounds.size.height + scrollView.contentOffset.y;

    //scrollView.contentSize.height=scrollView全体のサイズ
    int contentSize = scrollView.contentSize.height;
    if (viewSize >= contentSize) {
        _tabBar.hidden = YES;
    }
    
}

//scrollを開始した時点で一度だけ呼ばれる
- (void)scrollViewWillBeginDragging:(UIScrollView *)scrollView
{
	//scrollを開始した値を取得する
    scrollBeginingPoint = [scrollView contentOffset];
}

~~~

これでできた。