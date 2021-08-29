# Laravel Mobile Detection in Blade

A package that enables you to use device detection right in your Blade templates. (Utilises the well-known, constantly updated [PHP mobile detection library](http://mobiledetect.net/).)

### When would you use this package?
Responsive CSS may help to make content in the browser look nice on different devices but it won't help you serve responsive content from your backend (at least not the easy way). This can have a really bad knock-on effect on the user experience (have you ever waited for a large image to load while having a bad connection on your mobile?). This package will make it a breeze to serve device-specific content right from your back-end.

### How does this package work?
The package implements various Blade directives that you can use to serve different content from your Blade template for different device types.

### Installation
Install the package through composer:

```sh
$ composer require NxtCode/laravel-mobile-detect
```

### Laravel 5.4 or earlier
Add the service provider to your **config/app.php** file:

```php
NxtCode\Laravel\MobileDetect\MobileDetectServiceProvider::class
```

Optionally, you can add an alias as well if you'd like to use the underlying instance anywhere else (or have access to all the functions):
```php
'MobileDetect' => NxtCode\Laravel\MobileDetect\Facades\MobileDetect::class
```

### Usage
Use the new Blade directives in your template files:

```php
@desktop
    <img src="/path/to/high-definition/image"/>
@elsedesktop
    <img src="/path/to/handheld-optimised/image"/>
@enddesktop
```

> **NOTE** You might have to run `php artisan view:clear` to have the new Blade directives take effect!

### Available directives

| Device  | directives |
| ------------- | ------------- |
| Destkop devices  | `@desktop`, `@elsedesktop`, `@enddesktop`  |
| Mobile and tablet  | `@handheld`, `@elsehandheld`, `@endhandheld`  |
| tablet devices | `@tablet`, `@elsetablet`, `@endtablet`  |
| Non-tablet (desktop or mobile) devices | `@nottablet`, `@elsenottablet`, `@endnottablet`  |
| Mobile devices | `@mobile`, `@elsemobile`, `@endmobile`  |
| Non-mobile (desktop or tablet) devices | `@notmobile`, `@elsenotmobile`, `@endnotmobile` |
| iOS platforms | `@ios`, `@elseios`, `@endios`  |
| Android platforms | `@android`, `@elseandroid`, `@endandroid`  |
 
 

The usage of `@else...` directives are optional.
