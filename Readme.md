## Custom Post For WP

```
function neuron_custom_post() {
    register_post_type('slide',
        array(
            'labels'      => array(
                'name'          => __('slides'),
                'singular_name' => __('slide'),
            ),
                'suports'     => array('title', 'thumbnail', 'custom-field', 'text-attributes', 'editor'),
                'public'      => false,
                'show_ui' => true,
        )
    );
}

add_action('init', 'neuron_custom_post');
```