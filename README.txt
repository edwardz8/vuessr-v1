=== VueSSR ===
Version: 1.0

== Description ==

working + experimental wordpress theme using carbon fields

add repo to themes folder of wordpress instance 

$ composer install 

reference: https://docs.carbonfields.net/ 

== Installation ==

1. In your admin panel, go to Appearance -> Themes and click the 'Add New' button.
2. Type in Tom in the search form and press the 'Enter' key on your keyboard.
3. Click on the 'Activate' button to use your new theme right away.

== Copyright ==

...

== Todos ==

add inputs and forms with and without gravity forms using carbon fields inside /metabox/carbon-fields

example: 

```
// form.php 

<?php

use Carbon_Fields\Container;
use Carbon_Fields\Field;

add_action('carbon_fields_register_fields', 'crb_attach_text');
function crb_attach_text()
{
    Container::make('post_meta', __('Text'))
        ->where('post_type', '=', 'page')
        ->add_fields(array(
            Field::make('text', 'crb_phone_number', __('Phone Number'))
                ->set_help_text('Add number here'),
            /* Field::make('sidebar', 'crb_custom_sidebar')
                ->set_help_text('Add sidebar') */
        ));
}
```

```
// api/get/page-item.php 

/* form and phone number */
    $phone_number = carbon_get_post_meta($post->ID, 'crb_phone_number');

    $item = [
     ...
     'phone_number' => $phone_number,
    ];

    return $item;
}

```

```
// functions.php:

include 'inc/metabox/carbon-fields/text.php';

```


