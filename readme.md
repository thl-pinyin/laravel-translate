Translation manager for Laravel 4
===============

Managing translations can be a pain, switching between different language files, adding new strings, keeping everything in sync and removing translations which are no longer being used.

But that's in the past if you install this package!

## Features
Lets take a look at all the features included in this package.

### Adding new translations
To add a new translation you need to open your terminal, and run the following command:

`php artisan translate:add <group> <line>`

So for a example:  
`php artisan translate:add account upgrade`

<img src="http://d.pr/i/jQmr+">

As you can see, you will get the blade syntax returned so you can copy and paste it to your view. Adding variables to your string will result in a different syntax:  
`php artisan translate:add account welcome`

<img src="http://d.pr/i/AWXe+">

Translation files are dynamically generated in alphabetical order and equally spaced.

<img src="http://d.pr/i/9ZaS+">

### Removing translations

To remove translations you can use the remove command which has the same syntax as the add command:  

`php artisan translate:remove account upgrade`

<img src="http://d.pr/i/2EVm+">

### Clean up
The clean up command will search your files for language strings which are no longer used.

`php artisan translate:clean-up`

<img src="http://d.pr/i/sJ3M+">

Foreach line that was not found, you will get a confirmation if you want to delete the line in question.

In case you you don't want to confirm each line, you can add the `--silent` parameter.  

`php artisan translate:clean-up --silent`

By default the clean up command will look through all your language files. In case you want to focus on one specific group, you can add the `--group="account"` parameter.  

`php artisan translate:clean-up --group="account"`

## Installation
The package can be installed via Composer by requiring the "philo/laravel-translate": "dev-master" package in your project's composer.json.

```
{
    "require": {
        "laravel/framework": "4.1.*",
        "philo/laravel-translate": "dev-master"
    },
    "minimum-stability": "dev"
}
```

Next you need to add the service provider to app/config/app.php

```
'providers' => array(
    // ...
    'Philo\Translate\TranslateServiceProvider',
)
```

## Config

You can publish the config file in case you want to make some adjustments to the clean up command:
`php artisan config:publish --path=philo/translate philo/translate`

```
<?php
return array(
	'search_ignore_folders'  => array('commands', 'config', 'database', 'lang', 'start', 'storage', 'tests'),
	'search_exclude_files'   => array('pagination', 'reminders', 'validation'),
);
```

#### Notes
When you start using the translation manager you need to make sure that all your translation files are in sync.
The translation manager does not work with language files that contain multidimensional arrays.