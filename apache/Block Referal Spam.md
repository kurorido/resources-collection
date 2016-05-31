# .htaccess

```
<IfModule mod_setenvif.c>
SetEnvIfNoCase  Referer  humanorightswatch.org spam=yes
SetEnvIfNoCase  User-Agent  humanorightswatch.org  spam=yes
SetEnvIfNoCase  Referer  semalt.com spam=yes
SetEnvIfNoCase  Referer  semalt.semalt.com spam=yes
SetEnvIfNoCase  Referer  social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site33.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site22.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site12.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site10.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  www1.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site14.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site20.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site23.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site28.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site34.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site35.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  site38.social-buttons.com spam=yes
SetEnvIfNoCase  Referer  simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  site11.simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  site14.simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  site22.simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  site25.simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  site33.simple-share-buttons.com spam=yes
SetEnvIfNoCase  Referer  s.click.aliexpress.com spam=yes
SetEnvIfNoCase  Referer  o-o-6-o-o.com spam=yes
SetEnvIfNoCase  Referer  oo-8-oo.com spam=yes
SetEnvIfNoCase  Referer  buttons-for-website.com spam=yes
SetEnvIfNoCase  Referer  editors.choice47490884.hulfingtonpost.com  spam=yes
SetEnvIfNoCase  Referer  forum.topic47490884.darodar.com spam=yes
SetEnvIfNoCase  Referer  humanorightswatch.org spam=yes
SetEnvIfNoCase  Referer  cookie-law-enforcement-cc.xyz spam=yes
SetEnvIfNoCase  Referer  eu-cookie-law-enforcement2.xyz spam=yes
SetEnvIfNoCase  Referer  popads.net spam=yes
Deny  from  env=spam 
</IfModule>
```
