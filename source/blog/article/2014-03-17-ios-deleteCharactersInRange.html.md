---
title: 【Objective-C】文字列内に特定の文字列があったら削除する
date: 2014-03-17 23:32 JST
tags: Objective-C
---

HTMLソースから特定のデータを削除する

~~~c
  //
  // 引数htmlSourceはHTMLソース
  //
- (NSMutableString *)delete:(NSMutableString *)htmlSource
{

    NSRange searchStart = [htmlSource rangeOfString:@"search_start"];
    NSRange searchEnd = [htmlSource rangeOfString:@"serach_end"];
    
    //  searchStartとsearchEndが両方があった場合に処理する
    if (searchSocialStart.location != NSNotFound &&
        searchSocialEnd.location != NSNotFound) {

        int deleteLocation = searchSocialStart.location;
        int deleteLength = searchSocialEnd.location-searchSocialStart.location+searchSocialEnd.length;
        
        //  deleteLocationは削除する位置
        //  deleteLengthは削除する長さ
        [htmlSource deleteCharactersInRange:NSMakeRange(deleteLocation, deleteLength)];

    }
    return htmlSource;
}
~~~


