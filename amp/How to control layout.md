# How to Control Layout

<a href='https://www.ampproject.org/docs/guides/responsive/control_layout.html'>How to Control Layout</a>

## How AMP Lays out its pages

AMP layout 系統的關鍵目標是確保在其它遠端資源或是Javascript載入之前，所有的元素會預先被放到正確的位置上，這樣子可以顯著的減少繪圖時和滾動時的畫面亂跳。
表達每一個元素在葉面上的大小和位置會需要基於幾個屬性: width, height, layout, media, sizes, placeholder, fallback

## Size and position elements

AMP component 元素一定要有 width 和 height，這兩個屬性也隱含了元素的比例。
所有的外部讀取資源，例如說圖片，一定要預先知道其高度，這樣頁面讀取的時候頁面才不會跳動。

AMP 提供了一系列的 layouts 可以使用

* nodisplay
* fixed (一定需要 height, width)
* responsive (一定需要 height, width)
* fixed-height(一定需要 height)
* fill
* container

### 如果沒有 layout attribute 的話?

* 如果有 height 但是沒有 width，則會被判定為 fixed-height
* 如果有 width 或是 height 且帶有 size ，則被認為 responsive
* 如果有 width 或是 height 則被認為是 fixed
* 如果沒有 width 跟 height 則被認為是 container

## Control page layout using @media and media

除了使用 @media 來控制元素呈現外，所有的 amp 元件都可以使用 media 屬性，下面是一個例子決定在不同螢幕大小時擷取不同的圖片

```
<amp-img
    media="(min-width: 650px)"
    src="wide.jpg"
    width=466
    height=355
    layout="responsive" >
</amp-img>
<amp-img
    media="(max-width: 649px)"
    src="narrow.jpg"
    width=527
    height=193
    layout="responsive" >
</amp-img>
```

## Control element’s size and assets using srcset and sizes

使用 srcset 屬性來控制不同螢幕下的資源呈現，例如 amp-img 在不同螢幕下使用不同圖片

```
<amp-img
    src="wide.jpg"
    srcset="wide.jpg" 640w,
           "narrow.jpg" 320w >
</amp-img>
```

再來看一個使用 sizes 的範例

```
<amp-img
    src="wide.jpg"
    srcset="wide.jpg" 640w,
           "narrow.jpg" 320w
    sizes="(min-width: 650px) 50vw, 100vw" >
</amp-img>
```

當螢幕為 650px 以下時，假設 viewport 為 800px ，這個圖片的大小會是 400px (50% view width)，因此會選擇 srcset 中的 narrow.jpg

## Include placeholders and fallbacks

Placeholders

```
<amp-anim src="animated.gif" width=466 height=355 layout="responsive" >
    <amp-img placeholder src="preview.png" layout="fill"></amp-img>
</amp-anim>
```

Fallbacks

```
<amp-video width=400 height=300 src="https://yourhost.com/videos/myvideo.mp4"
    poster="myvideo-poster.jpg" >
  <div fallback>
        <p>Your browser doesn’t support HTML5 video.</p>
  </div>
</amp-video>
```
