# jqueryupdater

//jquery updater

function abt_jquery_updater() {
	$ver = '3.5.1';
    $ver_core = $ver;
    $ver_migrate = '3.3.0';
    $slim = false;
    $min = true;
    $cdn = false; // google, microsoft, cdnjs, jsdelivr
    $migrate = true;
    $enqueue_admin = false;

    // jQuery Core
    // Deregister jQuery core
    wp_deregister_script( 'jquery-core' );
    // Reregister jQuery core
    wp_register_script( 'jquery-core', get_template_directory_uri() . '/js/jquery-3.5.1.min.js', [], $ver_core );

    // jQuery Migrate
    // Deregister jQuery Migrate
    wp_deregister_script( 'jquery-migrate' );
    // Reregister jQuery Migrate
    wp_register_script( 'jquery-migrate', get_template_directory_uri() . '/js/jquery-migrate-3.3.0.min.js', ['jquery-core'], $ver_migrate );

    // jQuery
    // Deregister jQuery ( Meta )
    wp_deregister_script( 'jquery' );
    // Reregister jQuery ( Meta )
    wp_register_script( 'jquery', false, ['jquery-core', 'jquery-migrate'], $ver );
}

add_action( 'wp_enqueue_scripts', 'abt_jquery_updater' );
add_action( 'login_enqueue_scripts', 'abt_jquery_updater' );
