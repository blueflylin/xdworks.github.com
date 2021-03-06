---
layout: post
title: "網站程式上線前需要準備的事 （五）"
date: 2012-03-19 02:13
comments: true
categories: 
---

## 第 5 件事：Close Alpha Test、Close Open Test

終於談到跟這個系列標題比較吻合的內容了！最後一個月上線前該做些什麼事？

在 本系列[（一）](http://blog.xdite.net/posts/2012/03/17/website-online-todo-1/) ，我提到了無論如何最後一個月是測試期。這一個月又分成

* close alpha
* close beta

### Close Alpha 內測 (一週)

close alpha 的對象是開發組以及營運組人員。也就是與核心較為相關的組別。此時針對的測試目標是這個 project 業務上應該被「實作」的 functionalty。比如說是食譜網站，就應該可以

* 上傳食物照片
* 新增烹飪步驟
* 站方精選
* 有熱門食譜、新進食譜
* 分享到社群網路 ...etc

如果是討論區，要應該可以

* 可以發表文章
* 可以回應文章
* 可以貼圖
* 可以收藏
* 可以搜尋
* 編輯器運作正常 ...etc.

另外測試時要擬定使用「未登入會員」、「登入會員」、「營運權限」、「Admin 權限」各測過一次。

因為開發組成員在撰寫功能時，為了方便，幾乎都是以 admin 帳號在開發，如果不制定測試步驟和角色，很容易沒測到死角。

此時的修復重點放在 feature complete ( 或取捨 ) 以及 functionaly 是否正常運作。

** 請不要在此時進行任何 UI 動線調整 **。 

### Close Beta 半公測 (二週+)

close beta 的對象是全公司所有人，公司員工的親朋好友，可以信賴的死忠會員等等...etc. 此時針對的測試目標是這個 project 的 UI 動線。

如果是討論區：

* 發表的動線是否順暢 
* 是否 UI 的暗示容易讓使用者 miss 掉上傳照片步驟
* 回應文章的動線是否流暢
* 網站新訊息的流動是否不夠快速，容易造成網站看起來一片死城。

此時已經是視同準上線了（所以 Close Alpha 階段的資料會清掉），所有營運組的人必須視同營運狀態一樣運營站務，以避免正式開站遇到狀況時手忙腳亂。

（這一招是從參訪壹電視時學到的。當時壹電視快開台時有受邀去內部參訪，當時聽到他們已經內部試 run 報新聞 run 了一年時，震撼非常...XD）

此時的修復重點放在 UI 動線的調整，以及運營方針、步驟的調整，避免開站之後網站就變成死城。

### Performance Tuning 與 Website Optimized （一週）

我在開發階段時，最常向 RD 宣導的事情是：我不想管你這個功能怎麼寫出來，但我要你準時交出來。（但最少要符合內部寫程式規範，有辦法讀懂）

原因是：網站最重要的是 Deliver 上線。而不是站上的 feature 用了多屌的技術，用了多棒的 best practices，沒有用戶會在意這件事。而「貪玩」「遲交」會砸了一切。

直到 Open Beta 期，Optimized 這件事都不會被提到。因為在網站稍微 stable 之前，所有的 optimized 都毫無意義，做了也是白作。因為會發生效能瓶頸的地方，永遠在你設計時意想不到的地方。

#### Backend Performance Tuning 

如何作 Performance Tuning？

* 抓出最慢的地方 Refactor 掉

幸運的是，我的專案都是 Rails Project，有[New Relic](http://newrelic.com/) 這套軟體可以用。它可以幫你找出你的網站哪一段 Ruby Code 特別沒效率，哪一段 code 製造出來的 SQL query 特別 slow。

其他技巧請看：[Rapid development with Rails](http://www.slideshare.net/xuitejoke/rapid-development-with-rails-7394238) P.54- P.59

* [Scaling Rails Site：Reading Material # 1](http://wp.xdite.net/?p=1597)
* [Scaling Rails Site：Reading Material # 2](http://wp.xdite.net/?p=1617)
* [Scaling Rails Site：Reading Material # 3](http://wp.xdite.net/?p=1664)
* [Scaling Rails Site：Reading Material # 4](http://wp.xdite.net/?p=1682)
* [Scaling Rails Site：Reading Material # 5](http://wp.xdite.net/?p=1704)

這是其他題目了。有空我會再整理 update 一篇 Rails Performance Tuning 的文章。

* 找出最常造訪的頁面壓力測試

既然已經進入 Open Beta 期了，這時候手上應該可以拿到這個網站最常造訪和效率最差的頁面。

可以使用 [ab](http://httpd.apache.org/docs/2.0/programs/ab.html) 去對網站進行壓力測試。

再決定是要 refactor slow code 或者是先上 cache 檔著先。


#### Frotend Performance Tuning

影響網站使用者感受最大的其實不是 backend 的效率，而是 Browser side 的效率。上線前我會

* 按照 [Best Practices for Speeding Up Your Web Site](http://developer.yahoo.com/performance/rules.html) 調整

其他技巧請看：

1. [Rapid development with Rails](http://www.slideshare.net/xuitejoke/rapid-development-with-rails-7394238) P.42- P.53
2. [Scaling Rais Site by default](http://www.slideshare.net/xuitejoke/scaling-rails-sites-by-default)

#### Website Optimized

以上說的都只是 Performance。但是這跟實際運營沒有那麼大的正關係。我擅長開發的是「內容網站」以及「社群網站」，這一類的網站重點其實是 SEO 以及社群穿透力。

* SEO 以及 Facebook OpenGraph

比如說：這是在 T 客邦累積出來的兩套 gem。

* [seo_helper](https://github.com/techbang/seo_helper)
* [open_graph_helper](https://github.com/techbang/open_graph_helper)

網站的每一個頁面都會確保分享至社群網站是正常的。

* Advertising

靠廣告賺錢，所以要調整廣告板位

* RSS / Email Subscribe / 粉絲團活動經營操作

跟 user 的互動...etc.

### 開站

這些都確認沒什麼問題了，然後才是開站。然而開站不是這一切的結束，還有其他事情需要作...

＝＝＝＝

系列文章：

* [網站程式上線前需要準備的事 （一）](/posts/2012/03/17/website-online-todo-1/)
* [網站程式上線前需要準備的事 （二）](/posts/2012/03/18/website-online-todo-2/)
* [網站程式上線前需要準備的事 （三）](/posts/2012/03/18/website-online-todo-3/)
* [網站程式上線前需要準備的事 （四）](/posts/2012/03/18/website-online-todo-4/)
* [網站程式上線前需要準備的事 （五）](/posts/2012/03/19/website-online-todo-5/)


