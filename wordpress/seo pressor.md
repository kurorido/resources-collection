# 轉移 HTTPS

```
[wp-content]$ grep -i -R '400,300,300italic,400italic,700,700italic' *
plugins/seo-pressor/templates/css/seop-box.css:@import url(http://fonts.googleapis.com/css?family=Roboto:400,300,300italic,400italic,700,700italic);
plugins/seo-pressor/templates/css/seops.css:@import url(http://fonts.googleapis.com/css?family=Roboto:400,300,300italic,400italic,700,700italic);
```
上面的 HTTP 改成 https
