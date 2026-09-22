+++
author = "Hugo 作者群"
title = "表情符號支援"
date = "2019-03-05"
description = "在 Hugo 中使用表情符號的指南"
tags = [
    "emoji",
]
+++

在 Hugo 專案中，有多種方式可以啟用表情符號（emoji）。
<!--more-->
[`emojify`](https://gohugo.io/functions/emojify/) 函式可以直接在範本（template）或[行內短代碼（Inline Shortcodes）](https://gohugo.io/templates/shortcode-templates/#inline-shortcodes) 中呼叫。

若要全站啟用表情符號，請在網站的[設定檔](https://gohugo.io/getting-started/configuration/)中將 `enableEmoji` 設為 `true`，之後就可以直接在內容檔案中輸入表情符號的簡寫代碼，例如：

<p><span class="nowrap"><span class="emojify">🙈</span> <code>:see_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙉</span> <code>:hear_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙊</span> <code>:speak_no_evil:</code></span></p>
<br>

[表情符號速查表](http://www.emoji-cheat-sheet.com/) 是查詢表情符號簡寫代碼相當實用的參考資料。

***

**備註：** 以上步驟可以在 Hugo 中啟用 Unicode 標準的表情符號字元與序列，不過這些符號的實際呈現方式仍取決於瀏覽器與作業系統平台。若要為表情符號套用樣式，可以使用第三方表情符號字型或字型堆疊（font stack），例如：

{{< highlight html >}}
.emoji {
  font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
}
{{< /highlight >}}

{{< css.inline >}}
<style>
.emojify {
	font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
	font-size: 2rem;
	vertical-align: middle;
}
@media screen and (max-width:650px) {
  .nowrap {
    display: block;
    margin: 25px 0;
  }
}
</style>
{{< /css.inline >}}
