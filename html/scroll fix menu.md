* http://stackoverflow.com/questions/13274592/leave-menu-bar-fixed-on-top-when-scrolled

```javascript
$(window).bind('scroll', function () {
    if ($(window).scrollTop() > 50) {
        $('.menu').addClass('fixed');
    } else {
        $('.menu').removeClass('fixed');
    }
});
```
