## Learning WordPress

1. 本来是一个博客系统，后来发展成了一个CMS（内容管理系统），可以用来搭建各种类型的网站。
2. PHP编写，使用MySQL作为数据库。
3. page本质上是一个post，只是有一个page_type的字段来区分。自己创建的post_type也是一个post。
4. theme里面的php文件对应的就是WordPress的模板文件，WordPress会根据URL来选择使用哪个模板文件。详见`wp-admin/includes/file.php`的`$wp_file_descriptions`。
    - page的模板文件是`page.php`，自定义的 post_type 的模板文件是`single-{post_type}.php`，如果没有就使用`single.php`，如果没有就使用`index.php`。
    - post的模板文件是`single.php`，如果没有就使用`index.php`。

## How to add custom type

1. Install the plugin: Advanced Custom Fields (ACF)
2. Create a new field group in ACF

## `mu-plugins` folder

- Create a folder in `wp-content` called `mu-plugins`
- Create a PHP file in the `mu-plugins` folder with the following code:

```php
<?php
/*
Plugin Name: Custom Post Type Registration
Description: Registers a custom post type.
Version: 1.0
Author: Your Name
*/
function custom_post_type() {
    register_post_type('your_custom_post_type', array(
        'labels' => array(
            'name' => __('Your Custom Post Types'),
            'singular_name' => __('Your Custom Post Type')
        ),
        'public' => true,
        'has_archive' => true,
        'supports' => array('title', 'editor', 'thumbnail'),
    ));
}
add_action('init', 'custom_post_type');
?>
```

## Reset post data after a custom query

```php
<?php
// Custom query
$args = array(
    'post_type' => 'your_custom_post_type',
    'posts_per_page' => 10,
);
$query = new WP_Query($args);
if ($query->have_posts()) {
    while ($query->have_posts()) {
        $query->the_post();
        // Your loop code here
    }
}
// Reset post data
wp_reset_postdata();
?>
```