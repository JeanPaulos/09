<?php 

/**
 * Plugin Name: Extra Order Status
 * Plugin URI: https://www.bedrukt.nl
 * Description: WooCommerce Custom Extra Order Status voegt een extra order status toe aan de bestellingen.
 * Version: 2.0.0
 * Author: J.P. van der Meer
 * Author URI: https://www.bedrukt.nl
 * License: GPL2
 * WC requires at least: 3.3
 * WC tested up to: 4.7.0
 */

function register_new_wc_order_statuses() {
    register_post_status( 'wc-shipping-progress', array(
        'label'                     => 'In productie',
        'public'                    => true,
        'exclude_from_search'       => false,
        'show_in_admin_all_list'    => true,
        'show_in_admin_status_list' => true,
        'label_count'               => _n_noop( 'In productie (%s)', 'In productie (%s)' )
    ) );
}
add_action( 'init', 'register_new_wc_order_statuses' );
 
// Add new statuses to list of WC Order statuses
function add_new_wc_statuses_to_order_statuses( $order_statuses ) {
 
    $new_order_statuses = array();
 
    // add new order statuses after processing
    foreach ( $order_statuses as $key => $status ) {
 
        $new_order_statuses[ $key ] = $status;
 
        if ( 'wc-processing' === $key ) {
            $new_order_statuses['wc-shipping-progress'] = 'In productie';
            // Add a $new_order_statuses[key] = value; for each status you've added (in the order you want)
        }
    }
 
    return $new_order_statuses;
}
add_filter( 'wc_order_statuses', 'add_new_wc_statuses_to_order_statuses' );
