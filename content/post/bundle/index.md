---
title: '使用 Hugo 頁面套組（Page Bundles）'
description: '頁面套組是 Hugo 中一種可選的內容組織方式。'
summary: "頁面套組是 Hugo 中一種可選的頁面資源組織方式。你可以透過網站設定中的 `usePageBundles`，或是在單一頁面的 front matter 中，選擇是否在 Hugo Clarity 啟用頁面套組。" # 用於文章列表的摘要文字。
date: '2022-03-24'
aliases:
  - hugo-page-bundles
author: 'Hugo 作者群'
usePageBundles: true

featureImage: 'https://images.unsplash.com/photo-1447069387593-a5de0862481e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1169&q=80' # 文章頂部圖片。
# featureImageAlt: '圖片描述' # 特色圖片的替代文字。
# featureImageCap: '這是特色圖片。' # 圖說（選填）。
# thumbnail: 'thumbnail.jpg' # 文章列表中顯示的縮圖。
# shareImage: 'share.jpg' # 用於 SEO 與社群媒體分享摘要。

categories:
  - syntax
tags:
  - Hugo
series: 佈景主題指南
# 以下設定會覆蓋 params.toml 中的預設值：
showRelatedInArticle: true
showRelatedInSidebar: true
---

[頁面套組（Page Bundles）](https://gohugo.io/content-management/page-bundles/) 是 Hugo 中一種可選的[頁面資源組織方式](https://gohugo.io/content-management/page-resources/)。

你可以透過網站設定中的 `usePageBundles`，或是在單一頁面的 front matter 中，選擇是否在 Hugo Clarity 啟用頁面套組。[進一步了解 `usePageBundles`。](https://github.com/chipzoller/hugo-clarity#organizing-page-resources)

使用頁面套組時，頁面或區段所需的資源（例如圖片或附加檔案）會存放在**與內容檔案本身相同的目錄**中，而不是放在 `static` 目錄裡。

Hugo Clarity 支援[葉節點套組（leaf bundles）](https://gohugo.io/content-management/page-bundles/#leaf-bundles)，也就是 `content` 目錄底下任何包含 `index.md` 檔案的資料夾。Hugo 官方文件提供了以下範例：

```text
content
├── about
│   ├── index.md
├── posts
│   ├── my-post
│   │   ├── content1.md
│   │   ├── content2.md
│   │   ├── image1.jpg
│   │   ├── image2.png
│   │   └── index.md
│   └── my-other-post
│       └── index.md
│
└── another-section
    ├── ..
    └── not-a-leaf-bundle
        ├── ..
        └── another-leaf-bundle
            └── index.md
```

<blockquote>
在上方的 <code>content</code> 目錄範例中，共有四個葉節點套組：

<strong>about</strong>：這個葉節點套組位於根層級（直接位於
    <code>content</code> 目錄下），僅包含 <code>index.md</code>。

<strong>my-post</strong>：這個葉節點套組包含 <code>index.md</code>、另外兩個
    Markdown 內容檔案，以及兩個圖片檔案。<strong>image1</strong> 是 <strong>my-post</strong> 的頁面資源，僅能在
    <strong>my-post/index.md</strong> 中使用。<strong>image2</strong> 同樣是 <strong>my-post</strong> 的頁面資源，僅能在
    <strong>my-post/index.md</strong> 中使用。

<strong>my-other-post</strong>：這個葉節點套組僅包含 <code>index.md</code>。

<strong>another-leaf-bundle</strong>：這個葉節點套組巢狀位於數層
    目錄之下，同樣僅包含 <code>index.md</code>。

<em>葉節點套組建立所在的階層深度並不重要，只要它不是位於另一個
<strong>葉節點</strong>套組之內即可。</em>
</blockquote>

### 使用頁面套組的優點

下方這張圖片是本頁套組的一部分，實際存放於 `content/post/bundle/building.png`。因為它屬於這個頁面套組的一部分，圖片的標記語法只需要指定檔名 `building.png` 即可。

![一棟建築物](building.png)

日後如果你更改了這個 Markdown 檔案與圖片所在目錄的名稱，圖片的參照路徑也不需要另外修改。

除了能讓內容與相關資源的組織更加清晰之外，使用頁面套組時，**Hugo Clarity 還會自動產生現代圖片格式的標記語法**，讓圖片檔案體積更小。

舉例來說，當你參照像 `building.png` 這樣的圖片時，Hugo Clarity 會檢查是否存在相同檔名的 [WebP](https://en.wikipedia.org/wiki/WebP)、[AVIF](https://en.wikipedia.org/wiki/AVIF) 或 [JXL](https://en.wikipedia.org/wiki/JPEG_XL) 格式版本。若你檢視上方的圖片原始碼，會看到一個對應 `building.webp` 的 `<source>` 元素，因為該檔案確實存在。Hugo Clarity 只會在這些圖片實際存在時才產生對應的標記語法。

[支援這些格式與 `<picture>` 元素](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture#the_type_attribute)的瀏覽器會載入這些格式，不支援的瀏覽器則會退回使用預設圖片。[進一步了解此運作方式。](https://github.com/chipzoller/hugo-clarity#support-for-modern-image-formats)

最後，如果需要的話，頁面資源也可以在[頁面的 front matter 中](https://gohugo.io/content-management/page-resources/#page-resources-metadata)做進一步管理與調整，而且不僅限於圖片。

### 使用頁面套組的缺點

套組中的頁面資源僅供該頁面本身使用——也就是說，你無法在某個頁面中引入圖片後，再從另一個頁面參照同一張圖片。

若圖片需要在多處重複使用，會更適合放在 Hugo 的 [`assets` 目錄](https://gohugo.io/hugo-pipes/introduction/)中。與 Hugo 的 `static` 目錄不同，`assets` 目錄中的檔案可以透過 Hugo Pipes 處理，其中[包含圖片處理功能](https://gohugo.io/content-management/image-processing/)。
