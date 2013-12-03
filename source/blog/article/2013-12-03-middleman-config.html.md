---
title: middlemanのconfig.rb
date: 2013-12-03 23:36 JST
tags: middleman
---

さて、今回はこのブログの現時点のconfig.rbを大公開
ほとんど他のところのコピペだけど。。

後、githubにもあがってるからわざわざ書く必要もないけど、一応備忘録的に。

*config.rb*

~~~ruby

###
# Blog settings
###

 Time.zone = "Tokyo"

activate :blog do |blog|
  blog.prefix = "blog/article"
  blog.default_extension = ".md"
  blog.tag_template = "blog/tag.html"
  blog.taglink = "categories/:tag.html"
  blog.calendar_template = "blog/calendar.html"
  blog.paginate = true
  blog.per_page = 5
  blog.page_link = "page/:num"
end

page "blog/feed.xml", :layout => false
page "blog/article/*", :layout => "layouts/article"

###
# markdown settings
###

activate :syntax, :line_numbers => true
set :markdown, :tables => true, :autolink => true, :gh_blockcode => true,  \
    :fenced_code_blocks => true, :with_toc_data => true, :smartypants => true

set :markdown_engine, :redcarpet



###
# delecty settings
###

set :css_dir, 'stylesheets'

set :js_dir, 'javascripts'

set :images_dir, 'images'

activate :livereload

###
# build settings
###

configure :build do
   activate :minify_css
   activate :minify_javascript
end


###
# deploy settings
###

activate :deploy do |deploy|
    deploy.method = :git
    deploy.remote = "deploy"
    deploy.branch = "master"
end

~~~

言うほどたいした設定してない。
今日はとりあえず載っけただけにしとく。

今後、この記事をちまちま更新するようにする。
