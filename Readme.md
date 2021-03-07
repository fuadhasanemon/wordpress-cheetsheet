``` function neuron_theme_suports() {

    ## Translations can be filed in the /languages/ directory.
    load_theme_textdomain( 'neuron-f', get_template_directory() . '/languages' ); 

    ## Add default posts and comments RSS feed links to head.
    add_theme_support( 'automatic-feed-links' ); 

    ## Let WordPress manage the document title.
     add_theme_support( 'title-tag' ); 

    ## Enable support for Post Thumbnails on posts and pages.
    add_theme_support( 'post-thumbnails' );

    ## This theme uses wp_nav_menu() in one location.
	register_nav_menus(
		array(
			'menu-2' => esc_html__( 'Primary', 'neuron-f' ),
			) );

    ## to output valid HTML5.
    add_theme_support(
                'html5',
                array(
                    'search-form',
                    'comment-form',
                    'comment-list',
                    'gallery',
                    'caption',
                    'style',
                    'script',
                ) ); 
    
    ## Add theme support for selective refresh for widgets.
       add_theme_support( 'customize-selective-refresh-widgets' );
    
    ## support for core custom logo.
       add_theme_support(
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





    ## Custom Post For WP
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
