---
layout: post
title: "Thoughts on HTML5 & Mobile App"
date: 2011-11-19 16:14
comments: true
categories: 

---

這篇文章是看完陳鐘誠教授寫的「[HTC 最需要的軟體能力](http://ccckmit.wikidot.com/in:htc)」的文章後，自己的感想。

坦白說，我真的覺得這是一篇相當天真的文章。


[在看下去之前，先警告讀者本文是一篇 TL;DR 的文章。]


## Thoughts on Flash

上個禮拜網路界的熱門是，Adobe 宣布放棄了繼續在 Mobile Browser 上 Flash 的繼續開發（見 36kr 的 [有关Flash移动浏览器插件，Flash平台和Flash未来的几点澄清](http://www.36kr.com/p/59728.html) ）。這篇文章提到幾件重要的事：

1. mobile 版上的 flash 不可能完成 flash 在 desktop 上的規模偉業
2. HTML5 可以在 mobile browser 完成類似 flash 在 desktop browser 上能做出來的成果
3. 使用者在 mobile device 上的閱讀的需求與體驗和 desktop 上有著很大的不同
4. mobile 版上的 flash plugin scabilty 不好 ( 這與硬體有很大的關係 )

這時候，再回去看去年 Steve Jobs 當初寫的那一篇 [Thoughts on Flash](http://www.techbang.com.tw/posts/2405-steve-jobs-thoughts-on-flash-full-translation)，儘管當時很多人罵 Steve Jobs 霸道，為了保護自己的商業利益、不惜故意扭曲放大 Flash 的缺點云云。

你不得不能說 Steve Jobs 其實當年其實是講了真話，這是「他看見的事實」。只是很多人「當時還沒有自己跳下來作，沒有那個深刻體會」，沒有辦法接受這個論點。

### mobile flash 致命的缺點

如果你是蘋果的長期使用者的話，應該知道蘋果最 care 的其實不是賺錢，而是「**使用者體驗**」這件事。(別鞭我)

mobile flash 是個 container（iOS） 中的 container ( flash ) 這件事，其實沒什麼不好。就如同現在普遍的解決方案也是 container (iOS) 中的 container (HTML5 in Browser)。** Flash 平台上就跟 HTML 一樣有著累積已久的解決方案和人才，不是 Native API 短期可以衝出來的。**

但 Flash 的缺陷就如同 Jobs 所說的一樣，無法解決或者是解決速度緩慢：

1. Flash 無法夠流暢的在智慧型手機上運作。
2. Flash 在 Mobile 的版本幾乎要被重寫過，這件事情讓「累積方案」看起來沒有那麼值錢了。
3. 使用者操作的行為不一樣。在 Desktop 上只有一種行為，也就是「滑鼠行為」。但 Mobile 上重要的是「手勢」。
4. 耗電與效能問題。Flash 想作為 container 中的 container，但是要花費大量額外的人力去對硬體客製，否則無法達成目的。而耗電與效能正是智慧型手機上最被開發者和使用者所在乎的事情。
5. Native API 的支援。想要做到幫助開發者做到寫跨平台程式，平台支援 Native API 的速度至關重要，但 Adobe 這部分的速度慢的要死。

所以 Jobs 才會在該篇文章的後面，這麼結語：「希望 Adobe 應該將焦點多放在製作 HTML5 的工具上」。我相信這是他的真心話。

## Thoughts on HTML5 & Mobile App

除了 Flash 之外，能夠解決「跨平台」這個目的的，就只剩下 HTML 這個方案了。

如果想在智慧型手機上開發軟體不那麼事倍功半的話，只有一個策略，那就是支援標準。

為什麼影音市場會傾向 H264，跨平台媒體方案會傾向 HTML5。因為「硬體」廠商和「OS」廠商會支援「標準」並可能實作「加速」，開發者就不需要那麼累的反而去對「每個平台」作客製。

有人打趣說寫 Mobile Web 真是愉快，因為開發者不需要像在 Desktop 的環境時，面對那麼多不同的 browser (特別是 IE6)。在智慧型手機上只有一種 browser，那就是 webkit-based。

### Mobile App 上的實戰

前陣子自己實際寫了一套 Mobile 上的電子出版架構，更能深刻體悟到為何現在多數的工具型 App，其實都是 Native API 與 HTML5 混搭的策略。

1. Native API 門檻太高。Native API 要練成絕世高手，絕非一朝一夕。但 mobile apps 的市場需求又遠超過開發者市場的供給。
2. HTML 上累積的解決方夠多。在 mobile apps 上介面上實作一段很絢麗的跳出框或特效，用 Native API 可能要刻上一週甚至更久。但是如果使用 jQuery 在 HTML 上實作就不用。
3. 使用 HTML 的開發者夠多。撰寫 HTML 的門檻比起 Native API 門檻實在太低了，開發者容易培養訓練。

### 實質的解決方案：Titanium

[Titanium](http://www.appcelerator.com/) 就是這樣的解決方案，簡介可見 [跨平台移動應用程式的解決方案 – Titanium](http://www.inside.com.tw/2011/03/30/titanium-cross-platform-mobile-application-solution)。

多數的開發者的策略轉變成，以 Titanium 寫出符合 HIG 或者是 Mobile App Best Pratices 的原生介面（按鈕、流程），但媒體內容卻全以 HTML5 實作。

Titanium 主要的開發語言是 JavaScript，開發者可以透過 JavaScript 撰寫 function，交由 Titanium 轉換編譯成平台上的原生原始碼。

好處是：JavaScript 原本就是 Web Developer 平日使用的工具之一。開發者只要專心與 JavaScript / HTML / CSS 打交道即可，而它們都是「標準」。

這樣就可以將 Mobile App 的開發工作拆得更單純，讓 container 上的開發歸 container ( iOS )，媒體內容歸媒體內容。


## 真正的決戰場在螢幕尺寸

坦白說我看 「[HTC 最需要的軟體能力](http://ccckmit.wikidot.com/in:htc)」此文，最難以理解的是這一段

<blockquote>
更棒的是，程式設計師將不再需要為每一個平台撰寫一套程式，一個以 HTML5 為主的程式，可以同時在「iOS, Android, Windows」 等作業系統中執行，也可以跨越「手機、平板、筆電、桌電」等裝置的限制，成為名符其實的「Write Once, Run Anywhere !」的跨平台系統。
</blockquote>

<blockquote>
但是 HTML5 畢竟只是前端的顯示技術，這個技術並沒有制定出關於後端的標準，因此要能用 HTML5 統一「手機、平板、筆電、桌電」等裝置，仍然有一塊標準技術上的空白之地，而這塊領域也正是台灣廠商可以深耕的領域，這就是以 HTML5 為核心的伺服端技術。
</blockquote>

<blockquote>
這種伺服端技術不只可以用在傳統的桌上型電腦上，更可以直接用在「手機與平板」電腦當中，舉例而言，我們只要撰寫一個簡單的小型伺服器，放在手機上常駐執行，當 HTML5 網頁需要執行系統功能時，就用 AJAX 或 WebSocket 的方式，呼叫這些小型伺服器，以便執行系統功能，並且傳回系統相關的資訊，如此就能讓 HTML5 程式完成幾乎所有原本只有作業系統才能完成的功能，成為名符其實的「ＷebOS」。

</blockquote>

What The H…

我不確定作者知不知道自己在說什麼？但 Mobile App 與 Desktop App，甚至是 Mobile Web 與 Desktop Web 上開發的挑戰根本不是 OS 的 API 問題。在不同平台上，使用者與平台互動機制與媒體的需求是完全不同的兩回事。

「Write Once, Run Anywhere !」沒什用，因為不能「Use」就沒有用。

Again：問題在於螢幕尺寸造成的 render 效果差異，和 device 不同的輸入互動模式。

### Responsive Design 不是終點

對於螢幕尺寸造成的 render 效果差異，有人提出了「Responsive Design」這個概念。

Responsive design 是一個全新的設計概念，開發者可以使用 CSS3 的 media query ，去對不同 device 的寬度去對 HTML 作出不同的 styling。

很理想對吧？

我手上有兩個以上採 Responsive design 的 websites。還有一個採 Responsive design 的 mobile app。

實際開發出來進行維護（可以看 [T客邦](http://www.techbang.com.tw) 和 [Digiphoto](http://digiphoto.techbang.com.tw) ）才發現這也只是個理想國的概念。

**Responsive design 在 iPhone / iPad App 上的確很威，只要寫四套 CSS 就可以解決所有的問題。（iphone 直排/橫排, iPad 直排/橫排）**

有些開發者說，Mobile Web 上面沒有惡魔 IE6 了 YA! 

錯了，真正的惡魔是 Android。

#### Mobile 開發上的大惡魔：不同尺寸的 Android 手機與 Android 平板

網頁開發者痛恨 IE 系列的原因是，明明寫的是正確的 CSS。但是 IE 就是會 render 出詭異的結果。

而不同尺寸的 Android 手機 / 平板，給開發者的惡夢就是：「無論你怎麼排版，View 就是會爆炸。」

今天在 Samsung 平版上看可能沒有問題，但是在 HTC 平板上，menu bar 可能就爆掉了。

使用者只會要求在它的 device 上的體驗要是完美的。

當然，PM 也不是沒有好心的告訴我一些他認為「可能」可以解決這樣問題的方案。比如砍字！

在 Flyer 上 menu 可以是「拍攝技法」、「哈燒新品」。但在 Sensation 上 menu 可以變成是「技法」、「新品」！

這是解法嗎？不是。Responsive 是提供 CSS styling 的解法，而砍字這個解法是要求我偵測 Agent 用程式去解決。(我知道可以用 responsive design 去另包元素作 display none; 我不可能配合，這是改動結構。因為使用者提出的需求不僅是這樣而已，還有加字、改 bar、改設計。簡直是瘋了。這樣偵測 Agent 重寫一版網頁版程式還比較快)

簡而言之，Responsive Design 遇到 device 的直排/橫排的情況是很棒的解法，但是它無法解決內容一直在變動，Device 尺寸不一的問題。

Desktop 瀏覽器視窗放大縮小造成破版的問題，使用者不會 Care，完全不是問題。但在 Mobile 瀏覽器上，這就是 Bug！

## 螢幕的尺寸不一破壞了軟體生態圈

這個世界已經漸漸告訴我們，智慧型手機的戰場不在於硬體規格，也不在於 OS 威不威。因為硬體和 OS 系統商「不可能自己做完任何事」。所以拼的就是軟體生態圈的品質。

消費者買智慧型手機，不是買 featues，而是想買「體驗良好」、「解決需求」的「app solutions」。

好的軟體生態圈才有辦法造出這些 solutions。

如何培育軟體生態圈？

其實開發者心聲多數相當單純：「少給我找麻煩」、「讓我可以賺到錢」，而不是「這技術門檻有多低」。

如果把開發者搞得半死不活，絕大精力都在處理硬體和 OS 製造出的愚蠢 bug。開發者也要吃飯，也要領錢，沒有人會願意餓著肚子陪你辦家家酒的。

而螢幕的尺寸不一就足夠把 Mobile App / Web Developer 搞垮

## 小結

其實不難規結，開發 Mobile App 的重點是什麼：

1. 流暢 (UI / Network Latency)、低耗能、高效率
2. 支援標準
3. Native 與 HTML 技術混搭
4. 固定螢幕尺寸
5. 符合 [HIG](http://developer.apple.com/library/ios/#documentation/userexperience/conceptual/mobilehig/Introduction/Introduction.html) 標竿的工藝
6. 可以賺到錢

HTML5 可以解決這當中的一些事情，如 (1) (2) (3)。但要做到「Write Once, Run Anywhere !」，跨越「手機、平板、筆電、桌電」等裝置的限制。看看目前的 Android 機海（4吋,7吋,10吋）情況，只能說算了吧…

而且這四種 Device 的需求原本就不同，HTML5 不是大靈丹。

[HTC 最需要的軟體能力](http://ccckmit.wikidot.com/in:htc) 是什麼？

我想絕對不會是往 HTML5 「微型伺服器」 這樣的方向，何況我也聽不太懂這是什麼東西。



