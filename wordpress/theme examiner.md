# Examiner 導致的 $ is not a function

原因出在這隻 examiner/js/exm1-one-button-install.js 
```
var $ = jQuery.noConflict();
$(document).ready(function() {
	$('.yesido').on('click', function(){
		$('.warrning-button').fadeOut( 'slow' )
	});
});
```

暴力解法：拿掉 examiner/inc/widget-presets.php 裡的宣告

可能解法：想辦法讓 Javascript load 順序正確？
