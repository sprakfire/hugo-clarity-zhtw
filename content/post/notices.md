---
author: Hugo 作者群
title: 使用提示框（Notices）
date: 2021-08-20
description: 在此佈景主題中使用提示框功能
summary: 在此佈景主題中使用提示框（Notices）功能，可標註附註、警告、小技巧等資訊。
---

「提示框（Notices）」短代碼可以讓你標註出特定資訊，例如附註、警告、小技巧等。

若要在頁面中建立提示框，可以使用 `notice` 短代碼。
使用 `notice` 短代碼時，第一個參數需為 `note`、`info`、`tip`、`warning` 其中之一，接著在引號中加入第二個參數作為提示框的標題。提示框內部的內容則可以是任何你想要撰寫的 Markdown 內容。

在 Markdown 文件中使用以下短代碼語法：
```
{{%/* notice note "備註" */%}}
這是標準的「備註」樣式。
{{%/* /notice */%}}
```
會呈現為：

{{% notice note "備註" %}}
這是標準的「備註」樣式。
{{% /notice %}}

其餘三種樣式如下所示。

{{% notice info "資訊" %}}
這是「資訊」樣式。
{{% /notice %}}

{{% notice tip "小技巧" %}}
這是「小技巧」樣式的提示框。
{{% /notice %}}

{{% notice warning "警告" %}}
這是「警告」樣式的提示框。
{{% /notice %}}


另外要留意，提示框內的內容可以放入任何一般頁面能使用的元素，如下例所示：

{{% notice tip "複雜的提示框也做得到！" %}}
這是一個包含多種內容類型的提示框範例。

* 這裡是一份項目清單
* 而且不只一個項目
    * 甚至還有多個層級

這裡也可以放程式碼區塊……
```csharp
public void SayHello()
{
    Console.WriteLine("Hello, world!");
}
```
{{% /notice %}}


{{% notice tip "生產力小幫手！" %}}
如果你使用 VS Code 編輯文章，可以將 `.vscode\clarity.code-snippets` 檔案複製到專案根目錄的 `.vscode` 資料夾中。這樣一來，只要輸入
`note` 再按 `<tab>`，接著用上下鍵選擇想要的提示框樣式，再按 `<tab>` 輸入標題，最後再按 `<tab>` 就能加入內容！

![](../images/Note-Snippet.gif)

要使用這個程式碼片段（snippet），你必須先**為 Markdown 啟用 quickSuggestions**（只需設定一次）：

1. 前往 `偏好設定 -> 設定`，接著搜尋 `quickSuggestions`
1. 依照連結前往編輯 settings.json
1. 在檔案底部貼上以下 JSON 內容：
```
"[markdown]":  {
    "editor.quickSuggestions": true
  }
```
4. 關閉並儲存設定檔。
{{% /notice %}}
