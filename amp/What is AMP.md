# AMP

來源: <a href='https://www.ampproject.org/docs/get_started/about-amp.html'>Waat is AMP?</a>

## 什麼是 Accelerated Mobile Pages (AMP)?

AMP 是一種讓靜態網頁讀取更快的網頁建置方法，AMP 包含了下面三部分

* AMP HTML
* AMP JS
* Google AMP Cache

## AMP HTML

AMP HTML 是基於 HTML 的延伸並使用客製的 AMP 屬性，一個基本的 AMP HTML 頁面會長的像是

```
<!doctype html>
<html ⚡>
 <head>
   <meta charset="utf-8">
   <link rel="canonical" href="hello-world.html">
   <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
   <style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
   <script async src="https://cdn.ampproject.org/v0.js"></script>
 </head>
 <body>Hello World!</body>
</html>
```

在 AMP HTML 頁面，大部分的標籤都是與正常的 HTML 一樣，只有少部分是使用 AMP 特定標籤 (參見: <a href='https://github.com/ampproject/amphtml/blob/master/spec/amp-html-format.md'>HTML Tags in the AMP spec</a>). 例如 amp-img 標籤。

## AMP JS

AMP JS library 實作了所有 <a href='https://www.ampproject.org/docs/get_started/technical_overview.html'>AMP’s best performance practices</a>

最大的最佳化就是所有的外部資源都是非同步載入，因此沒有任何東西會阻止頁面的繪製。

## Google AMP Cache

Google AMP Cache 是一個 proxy-based content delivery network ，用來傳遞所有合法的 AMP 文件。它會擷取 AMP 頁面進行緩存以及自動地提高頁面的讀取速度。 當使用 Google AMP Cache ，所有在相同域下的 JS 檔案和所有的圖片都是使用 HTTP 2.0 讀取來達到最大效益。

值得注意的是如果頁面不符合 AMP 規範，就不會被搜尋引擎收錄。


