+++
author = "Hugo 作者群"
title = "Markdown 語法指南"
date = "2019-03-11"
description = "展示 Hugo 內容中基本 Markdown 語法與 HTML 元素樣式的範例文章。"
featured = true
tags = [
    "markdown",
    "css",
    "html",
    "themes",
    "featured"
]
categories = [
    "themes",
    "syntax",
]
series = "佈景主題指南"
aliases = ["migrate-from-jekyl"]
thumbnail = "images/building.png"
+++

這篇文章示範了可用於 Hugo 內容檔案中的基本 Markdown 語法，同時也展示了此 Hugo 佈景主題是否有為基本 HTML 元素套用 CSS 樣式。
<!--more-->

## 標題

以下 HTML 的 `<h1>`—`<h6>` 元素代表六個層級的章節標題。`<h1>` 為最高層級，`<h6>` 為最低層級。

# H1
## H2
### H3
#### H4
##### H5
###### H6

## 段落

這裡是一段示範用的段落文字，用來展示 Hugo 佈景主題中段落的排版樣式。文字內容可以包含各種標點符號、數字與中英文混排，藉此測試行高、字距與換行是否美觀。一段良好的段落排版，能讓讀者在長篇閱讀時感到舒適，不會因為字距過密或行距過窄而產生視覺疲勞。透過適當的字型大小與行高設定，即使是技術性較高的文章，也能維持良好的可讀性。

這是接續段落之後的第二段文字，用來測試段落之間的間距是否恰當，也讓讀者可以觀察標題與內文之間的層級關係。

## 圖片

### 本機圖片，使用替代文字作為圖說

以下圖片存放於 Hugo 網站內。因為它只有替代文字（alt text）而沒有標題文字，圖說會依替代文字自動產生。

![王小美](../images/jane-doe.png)

### 遠端圖片，指定圖說文字

以下圖片是從遠端網址載入。替代文字相同（供螢幕報讀器使用，或圖片載入失敗時顯示），但因為額外提供了標題，圖說會改用標題文字：

![王小美](https://raw.githubusercontent.com/chipzoller/hugo-clarity/master/exampleSite/static/images/jane-doe.png "這是王小美")

### 只有替代文字、沒有圖說的圖片

替代文字對 SEO、無障礙以及圖片載入失敗時都相當重要，因此建議一律加上。不過並非每張圖片都需要顯示圖說，這時只要在標題欄位放入一個空白字元即可：

![一棟建築物](../images/building.png " ")

## 引言區塊

引言區塊（blockquote）元素用來表示引用自其他來源的內容，可以選擇性地在 `footer` 或 `cite` 元素中加入出處，也可以在其中加入行內的註解或縮寫等變化。

#### 無出處的引言區塊

> 這是一段沒有標明出處的引言範例文字，可以用來測試引言區塊的樣式呈現。
> **請注意**在引言區塊中也可以使用 *Markdown 語法*。

#### 附出處的引言區塊

> 不要透過共享記憶體來溝通，而要透過溝通來共享記憶體。<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: 以上引言節錄自 Rob Pike 於 2015 年 11 月 18 日 Gopherfest 活動的[演講內容](https://www.youtube.com/watch?v=PAAkCSZUG1c)。

## 表格

表格並非 Markdown 核心規格的一部分，但 Hugo 開箱即支援表格語法。

   姓名 | 年齡
--------|------
    小明 | 27
    小華 | 23

#### 表格內的行內 Markdown

| 斜體      | 粗體     | 程式碼  |
| --------  | -------- | ------ |
| *斜體文字* | **粗體文字** | `程式碼` |

## 程式碼區塊

#### 使用反引號的程式碼區塊

```html
<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <title>HTML5 文件範例</title>
</head>
<body>
  <p>測試</p>
</body>
</html>
```

#### 使用四個空格縮排的程式碼區塊

    <!doctype html>
    <html lang="zh-Hant">
    <head>
      <meta charset="utf-8">
      <title>HTML5 文件範例</title>
    </head>
    <body>
      <p>測試</p>
    </body>
    </html>

#### 使用 Hugo 內建 highlight 短代碼的程式碼區塊
{{< highlight html >}}
<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <title>HTML5 文件範例</title>
</head>
<body>
  <p>測試</p>
</body>
</html>
{{< /highlight >}}

## 清單類型

#### 有序清單

1. 第一項
2. 第二項
3. 第三項

#### 無序清單

* 清單項目
* 另一個項目
* 還有一個項目

#### 巢狀清單

* 水果
  * 蘋果
  * 柳橙
  * 香蕉
* 乳製品
  * 牛奶
  * 起司

## 其他元素 — abbr、sub、sup、kbd、mark

<abbr title="Graphics Interchange Format">GIF</abbr> 是一種點陣圖影像格式。

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

按下 <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> 可結束此工作階段。

大多數的<mark>蠑螈</mark>屬於夜行性動物，會獵食昆蟲、蠕蟲及其他小型生物。
