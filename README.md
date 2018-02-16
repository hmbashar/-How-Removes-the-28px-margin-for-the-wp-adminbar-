# How Removes the 28px margin for the WordPress adminbar

A disabled Admin Bar leave a 28px space at the top of the page, the snip below removes the extra space. The
example removes the space for both the Admin Area and Websites.

place that codes in your functions.php page

```
/*
* Removes the 28px margin for the Admin Bar
*/
function remove_adminbar_margin() {
$remove_adminbar_margin = '<style type="text/css">
html { margin-top: -28px !important; }
* html body { margin-top: -28px !important; }
</style>';
echo $remove_adminbar_margin;
}
/* wp-admin area */
if ( is_admin() ) {
remove_action( 'init', '_wp_admin_bar_init' );
add_action( 'admin_head', 'remove_adminbar_margin' );
}
/* websites */
if ( !is_admin() ) {
remove_action( 'init', '_wp_admin_bar_init' );
add_action( 'wp_head', 'remove_adminbar_margin' );
}
```
