Fat-Free Framework Form Validator
============================
This is a [CodeIgniter's](https://codeigniter.com/) ([GitHub](https://github.com/bcit-ci/CodeIgniter)) [Form Validation](https://github.com/bcit-ci/CodeIgniter/blob/3.1-stable/system/libraries/Form_validation.php) ported to [FatFreeFramework](https://fatfreeframework.com/) ([GitHub](https://github.com/bcosca/fatfree))

# Getting Start
## Install

Add the following to your composer.json file:
```json
{
    "require": {
        "edtsz/f3-form-validator": "1.0.0"
    }
}
```
Then open the terminal in your project directory and run: `composer install`

## Running
```php
$validator = new \Validator();
$validator->set_db( $f3->get('db.instance') ); // just if will use "is_unique"
$validator->set_rules(
	'username', 'Username',
	'required|min_length[5]|max_length[12]|is_unique[users.username]',
	array(
		'required'  => 'You have not provided %s.',
		'is_unique' => 'This %s already exists.'
	)
);
$validator->set_rules('password', 'Password',              'required');
$validator->set_rules('passconf', 'Password Confirmation', 'required|matches[password]');
$validator->set_rules('email',    'Email',                 'required|valid_email|is_unique[users.email]');

if ( $validator->run() === TRUE )
{
	// success
}
else
{
	print_r( $validator->error_array() );
}
```

_Full information about how to use it: [CI Docs](https://codeigniter.com/user_guide/libraries/form_validation.html)_

# Available Validators|Filters
## [CodeIgniter](https://codeigniter.com/user_guide/libraries/form_validation.html)
 - required
 - regex_match
 - matches
 - differs
 - is_unique
 - min_length
 - max_length
 - exact_length
 - valid_url
 - valid_email
 - valid_emails
 - valid_ip
 - alpha
 - alpha_numeric
 - alpha_numeric_spaces
 - alpha_dash
 - numeric
 - integer
 - decimal
 - greater_than
 - greater_than_equal_to
 - less_than
 - less_than_equal_to
 - in_list
 - is_natural
 - is_natural_no_zero
 - valid_base64
 - prep_for_form
 - prep_url
 - strip_image_tags
 - encode_php_tags

## [GUMP](https://github.com/Wixel/GUMP)
 - min_age
 - max_age
 - valid_name

## Custom
 - is_file
 - file_min_size
 - file_max_size
 - file_types
 - valid_cpf
 - valid_date
 - valid_datetime
 - valid_time
 - convert_case
 - substr

As [CI Docs](https://codeigniter.com/user_guide/libraries/form_validation.html) says: _"You can also use any native PHP functions that permit up to two parameters, where at least one is required (to pass the field data)."_

# Sources
 - [CodeIgniter Form Validation](https://github.com/bcit-ci/CodeIgniter/blob/3.1-stable/system/libraries/Form_validation.php)
 - [GUMP](https://github.com/Wixel/GUMP)

# TODO
 - Improve documentation
 - Examples
 - Tests
