---
author: Hugo 作者群
title: 數學公式排版
date: 2019-03-08
description: KaTeX 設定的簡易指南
math: true
---

在 Hugo 專案中，可以透過第三方 JavaScript 函式庫來啟用數學公式排版功能。
<!--more-->

在這個範例中，我們將使用 [KaTeX](https://katex.org/)。

- 在 `/layouts/partials/hooks/head-end.html` 下建立一個部分模板（partial）
- 在新建立的部分模板中加入以下內容：

```bash
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```

- 若要全站啟用 KaTeX，請在專案設定中將參數 `math` 設為 `true`
- 若要針對單一頁面啟用 KaTeX，請在該內容檔案中加入參數 `math: true`

**備註：** 可參考線上文件 [KaTeX 支援函式一覽](https://katex.org/docs/supported.html)

{{< math.inline >}}
{{ if or .Page.Params.math .Site.Params.math }}
<!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/katex.min.css" integrity="sha384-nB0miv6/jRmo5UMMR1wu3Gz6NLsoTkbqJghGIsx//Rlm+ZU03BU6SQNC66uf4l5+" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/katex.min.js" integrity="sha384-7zkQWkzuo3B5mTepMUcHkMB5jZaolc2xDwL6VFqjFALcbeS9Ggm/Yr2r3Dy4lfFg" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.11/dist/contrib/auto-render.min.js" integrity="sha384-43gviWU0YVjaDtb/GhzOouOXtZMP/7XUzwPTstBeZFe/+rCMvRwr4yROQP43s0Xk" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
{{ end }}
{{</ math.inline >}}

### 範例

{{< math.inline >}}
<p>
行內數學公式：\(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

區塊數學公式：
$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } } 
$$
