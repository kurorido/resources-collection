# How to Style Your Pages

原文: <a href='https://www.ampproject.org/docs/guides/responsive/style_pages.html'>How to Style Your Pages</a>

如同所有的網頁， AMP 頁面也是使用 CSS 進行排版，但妳不能參考任何外部的 stylesheets (除了自訂的字形)，以及 inline styles 屬性是不被允許的。
除此之外，部分與動畫相關的屬性也因為效能問題而不被允許。所有的 styles 都要寫在 <head> 標籤內。

雖然 inline stylesheets 會增加每個頁面的 bytes 數量，但是卻可以節省外部資源請求的時間。不過將所有 stylesheets 都 inline 也就是代表妳的所有 CSS 都變成了 critical CSS，因此只包含必須的 CSS 才不會造成負擔。

## Add Styles to a page

任何 AMP 葉面上的 style 都是寫在 <style amp-custom> 標籤內，這個標籤要放在 <head> 標籤內，例如：

```
<!doctype html>
<html ⚡>
  <head>
    <meta charset="utf-8">
    <link rel="canonical" href="hello-world.html" >
    <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
    <style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
    <style amp-custom>
      /* any custom style goes here. */
      body {
        background-color: white;
      }
    </style>
    <script async src="https://cdn.ampproject.org/v0.js"></script>
  </head>
  <body>Hello World!</body>
</html>
```
注意；確保整個頁面只有一個 <style amp-custom> 標籤，否則就是不合法的 AMP 頁面
