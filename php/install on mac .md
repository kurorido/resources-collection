# 安裝 php56 跟 xdebug

```
fontechs-MacBook-Air:~ roli$ sudo brew install php56-xdebug
To finish installing xdebug for PHP 5.6:
  * /usr/local/etc/php/5.6/conf.d/ext-xdebug.ini was created,
    do not forget to remove it upon extension removal.
  * Validate installation via one of the following methods:
  *
  * Using PHP from a webserver:
  * - Restart your webserver.
  * - Write a PHP page that calls "phpinfo();"
  * - Load it in a browser and look for the info on the xdebug module.
  * - If you see it, you have been successful!
  *
  * Using PHP from the command line:
  * - Run `php -i "(command-line 'phpinfo()')"`
  * - Look for the info on the xdebug module.
  * - If you see it, you have been successful!
==> Summary
🍺  /usr/local/Cellar/php56-xdebug/2.4.0: 2 files, 205.6K
fontechs-MacBook-Air:~ roli$ php --version
PHP 5.6.23 (cli) (built: Jun 24 2016 21:14:33)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
    with Xdebug v2.4.0, Copyright (c) 2002-2016, by Derick Rethans
```

# 安裝 php70 & xdebug

```
sudo brew unlink php56
sudo brew install php70
php-version 7
sudo brew install php70-xdebug
```
# 設定可 remote debug
```
vim /usr/local/etc/php/7.0/conf.d/ext-xdebug.ini

# 如果你是用 homebrew 裝 xdebug，你會發現他已經幫你指定好 xdebug 執行路徑了
# 類似下面這行
zend_extension="/usr/local/opt/php56-xdebug/xdebug.so"

# 一定要加入下面這行才能 debug web application
xdebug.remote_enable=1
```
