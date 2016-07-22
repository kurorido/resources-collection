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

暴力解法：拿掉 examiner/inc/widget-presets.php 裡的宣告 (見註解掉的部分）

```
function exm1_one_button_preset() {
	if(is_super_admin() ){
	add_theme_page('Examiner one button install widgets', 'Examiner Widget Presets', 'read', 'exm1_one_button','exm1_prearange');
	}
	wp_enqueue_style( 'Examiner one button install widgets style', get_template_directory_uri() . '/inc/exm1-widget-presets.css' );
	// wp_enqueue_script('Examiner one button install widgets', get_template_directory_uri() . '/js/exm1-one-button-install.js', array('jquery'));

}
```

可能解法：想辦法讓 Javascript load 順序正確？
