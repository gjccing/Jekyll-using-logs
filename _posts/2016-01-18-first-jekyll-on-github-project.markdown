---
layout: post
title:  "初次使用Jekyll建立GitHub專案網頁"
date:   2016-01-18 00:46:26 +0800
categories: jekyll update
---
此篇文章將一步步介紹如何用Jekyll建立GitHub專案網頁。

簡單的說明，Jekyll是一個靜態網站&Blog的產生器。它的工作原理很簡單，你給他文章和網頁框架他給你靜態網站，很簡單吧。而它只是一個靜態網站產生器，如果你想讓人看到你的網站還需要一個架站的空間來放置你產出的網站。架設靜態網站的首選當然是GitHub囉。而GitHub也[支援Jekyll][jekyll-gh]，會自動幫你build且順便幫做版本控管，兩者簡直絕配。

你想要在GitHub使用Jekyll，只要三個步驟：

  1. [在GitHub專案上建立`gh-pages` brach][github-cppm]
  2. [安裝Jekyll][jekyll-install]
  3. [使用Jekyll產生一個初始的網站][jekyll-qs]

基本上按照上述教學就能上手了，以下是我的整理。

### 1.在GitHub專案上建立`gh-pages`Brach
觸發GitHub使用Jekyll有兩種情況：

  *   `username.github.io`專案的`master`
  *   一般專案的`gh-pages` brach

這次的情況是一般專案，可以參考此[教學][github-cppm]。這邊的關鍵指令是這個：
{% highlight ruby %}
# 請先把專案clone下來並進入目錄
git checkout --orphan gh-pages
{% endhighlight ruby %}
用此指令創建出來的branch是完全獨立的不是從其他brach分出來的，很適合GitHub page這種形式的原始碼。

如果你喜歡GUI也可以依照此[教學][github-pages]。GitHub會幫你建立`gh-pages`並引導你在建立個還不錯看的網頁，如果你沒有日誌的需求這個網頁就已經夠用囉。再來把內容清掉就是了，挺笨的方法，可惜GitHub上沒提供產生Jekyll的選項。

### 2.安裝Jekyll
基本上依照教學就OK了，但Jekyll它是預設是不支援`Windows`的喔！得另外看這篇[教學][jekyll-windows]，看到第二步就夠用了，其實只多安裝個`RubyDevKit`而已。

### 3使用Jekyll產生一個初始的網站
這裡請使用terminal，cd到git專案的目錄下，輸入：
{% highlight ruby %}
jekyll new .
{% endhighlight ruby %}
就能產生一個起始的網站囉！這時你可以下：
{% highlight ruby %}
jekyll serve
{% endhighlight ruby %}
Jekyll會先幫你build再幫你開啟一個簡易的http server讓你觀看結果。進入[http://127.0.0.1:4000/](http://127.0.0.1:4000/)看看結果吧！

這時一切看起來都很美好，但請先不要Push上GitHub，還有一個地方需要設定。因為本次的主角是GitHub專案，它的GitHub pages的url規則是：
{% highlight ruby %}
<username>.github.io/<repository-name>
{% endhighlight ruby %}
直接上上去的話路徑會錯亂。這時看到這個檔案`_config.yml`，這是Jekyll的設定檔，修改裡面的`baseurl`：
{% highlight ruby %}
# 最後面不可接斜線
baseurl: "/<repository-name>"
{% endhighlight ruby %}
修改完就可以Push上去囉！

建議想知道更多的人可以直接看[官網][jekyll]，另外英文苦手也可以去[中文網][jekyllcn]看看喔。

[jekyllcn]: http://jekyllcn.com/
[jekyll]: http://jekyllrb.com/
[jekyll-gh]: https://github.com/jekyll/jekyll
[github-cppm]: https://help.github.com/articles/creating-project-pages-manually/
[github-pages]: https://pages.github.com/
[jekyll-install]: http://jekyllrb.com/docs/installation/
[jekyll-qs]: http://jekyllrb.com/docs/quickstart/
[jekyll-windows]: http://jekyll-windows.juthilo.com/
