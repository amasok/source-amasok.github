---
title: 【middleman】ブログのカレンダーで月単位の表示
date: 2013-11-30 12:20 JST
tags: middleman
---

久々にブログの構造自体をちょっといじったのでメモ

middleman-blogではテンプレートで年単位のカレンダーを表示してくれます。  
しかし、一般的には月単位でのカレンダーになると思うので、その変更点を書きます。

## 対象

* middleman blogのテンプレートを生成した人
* 月単位のカレンダーを表示させたい人

##

## 方法

カレンダー部分で年単位表示をさせる部分があると思います。

*source/layout.erb*

~~~erb
<h2>By Year</h2>
<ol>
  <% blog.articles.group_by {|a| a.date.year }.each do |year, articles| %>
    <li><%= link_to year, blog_year_path(year) %> (<%= articles.size %>)</a></li>
  <% end %>
</ol>
~~~

修正後

~~~erb
<h2>By Year</h2>
<ul>
  <% blog.articles.group_by {|a| a.date.year }.each do |year, articles_year | %>
      <li><%= link_to year, blog_year_path(year) %>(<%= articles_year.size %>)</li>
    <ul>
    <% blog.articles.group_by {|a| a.date.month }.each do |month, articles_month | %>
      <li><%= link_to month, blog_month_path(year, month) %> (<%= articles_month.size %>)</li>
    <% end %>
    </ul>
  <% end %>
</ul>
~~~

簡単な修正だったけど久々にいじれてよかった。

### 参考

http://rubydoc.info/github/middleman/middleman-blog/master/Middleman/Blog/Helpers#blog_month_path-instance_method
