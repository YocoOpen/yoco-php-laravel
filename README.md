
# yoco-php-laravel

This laravel package is a laravel-friendly library which wraps the [Yoco PHP](https://github.com/yoco/yoco-php) library to 
provides access to the Yoco Payment API from PHP.  It does this by providing a ChargeController and associated routes 
that can be called from the javascript frontend documented in the [Yoco API Docs](https://developer.yoco.com/online/api-reference/api-overview).

This library is used in conjunction with the frontend api described [here (for a js popup)](https://developer.yoco.com/online/popup/popup) 
 and [here (for an inline form)](https://developer.yoco.com/online/inline/inline) 
 which capture the actual card details.
 
Put simply, the process is 

  * Capture card details (choose a javascript library as indicated above)
  * Charge the card via your laravel application's ChargeController deployed by this library

A full demo implementation of the API in a laravel application is available [here](https://github.com/yoco/yoco-web-sdk-sample-php)

For more information on the end to end process, you can refer to the [Yoco API Docs](https://developer.yoco.com/online/api-reference/api-overview).

## Requirements

PHP 7.0 and later. Laravel 7+

## Installation

Install the library into your laravel application with [Composer](http://getcomposer.org/) and publish core files:

```bash
# Composer install
composer require yoco/yoco-php-laravel
# Publish config and charge controller
php artisan vendor:publish --tag=yoco
```

The above installation will add the files **/config/yoco.php** and **/app/Http/Controllers/ChargeController.php** 
to your source tree and also add the route **/yoco/charge** to your route list

### Setup your keys

Edit the file **/config/yoco.php** and set the secret and public key you received from yoco.

### Making a purchase

  * Setup the frontend to capture the card token, amount and currency as 
    described in the API docs [(for a js popup)](https://developer.yoco.com/online/popup/popup) or 
    [(for an inline form)](https://developer.yoco.com/online/inline/inline).
  * Use ajax to make a call to your charge route **/yoco/charge** which is processed by your **ChargeController.php** controller.
  * The result will be returned to your frontend as json. 

A full demo of this functionality is available at https://github.com/yoco/yoco-web-sdk-example-php under the laravel-app folder.

## Yoco API Documentation

See the [API docs](https://developer.yoco.com/online/api-reference/api-overview).


