## Translations can be filed in the /languages/ directory.

`   function neuron_theme_suports() {  
   load_theme_textdomain( 'neuron-f', get_template_directory() . '/languages' );`

 ## Add default posts and comments RSS feed links to head.
 
    add_theme_support( 'automatic-feed-links' ); 

    ## Let WordPress manage the document title.
    ``` add_theme_support( 'title-tag' ); ```

    ## Enable support for Post Thumbnails on posts and pages.
    ```add_theme_support( 'post-thumbnails' );```

    ## This theme uses wp_nav_menu() in one location.
	```register_nav_menus(
		array(
			'menu-2' => esc_html__( 'Primary', 'neuron-f' ),
			) );```

    ## to output valid HTML5.
   ``` add_theme_support(
                'html5',
                array(
                    'search-form',
                    'comment-form',
                    'comment-list',
                    'gallery',
                    'caption',
                    'style',
                    'script',
                ) ); ```
    
    ## Add theme support for selective refresh for widgets.
      ``` add_theme_support( 'customize-selective-refresh-widgets' );```
    
    ## support for core custom logo.
       ```add_theme_support(
        'custom-logo',
        array(
            'height'      => 250,
            'width'       => 250,
            'flex-width'  => true,
            'flex-height' => true,
            )
        );
    }

    add_action('after_setup_theme', 'neuron_theme_suports' );
```




    ## Custom Post For WP
   ``` function neuron_custom_post() {
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

## custom Slider
``` <?php
                        global $post;
                        $args = array('posts_per_page' => 7, 'post_type' => 'slide', 'orderby' => 'menu_order', 'order' => 'ASC');
                        $myposts = get_posts($args);
                        foreach ($myposts as $indexpost => $post) : setup_postdata($post); ?>
			
			<img src="<?php the_post_thumbnail_url('large'); ?>" alt="" data-bgposition="bottom">
			<p class="h_title"><?php the_title() ?> </p>
			<?php the_content(); ?>
					<?php
                        endforeach;
                        wp_reset_query();
                        ?>
```		

``` 
### Loop custom post type

   <?php
    global $post;
    $args = array( 'post_per_page' => -1, 'post_type' => 'posttype', 'orderby' => 'menu_order', 'order' => 'ASC');
    $myposts = get_posts( $args );
    foreach( $myposts as $post ) : setup_postdata($post); 
    ?>

    <?php 
        $custom_link = get_post_meta( $post -> id,  $single -> true );
    ?>
    <h2><?php the_title( ); ?></h2>
    <?php the_content(); ?>

    <?php endforeach; wp_reset_query(); ?>
    
    ````
    
    ```
    ### WP QUERY CUSTOM POST
    <?php
        $wpnew=array(
            'post_type' => 'slides',
            'post_status' => 'publish'
        );

        $newsquery=new WP_Query($wpnew);
        while($newsquery->have_posts()) {
            $newsquery->the_post();
            $imagepath=wp_get_attachment_image_src(
                get_post_thumbnail_id(), 'large'
            );
        }
        ?>
```
									
