---
title: Installation
---

Repository: [webklex/laravel-imap](https://github.com/Webklex/laravel-imap)

[![Latest Version on Packagist](https://img.shields.io/packagist/v/Webklex/laravel-imap.svg?style=flat-square)](https://packagist.org/packages/Webklex/laravel-imap)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://github.com/Webklex/laravel-imap/blob/master/LICENSE)
[![Build Status](https://img.shields.io/scrutinizer/build/g/Webklex/laravel-imap/master?style=flat-square)](https://scrutinizer-ci.com/g/Webklex/laravel-imap/code-structure)
[![Total Downloads](https://img.shields.io/packagist/dt/Webklex/laravel-imap.svg?style=flat-square)](https://packagist.org/packages/Webklex/laravel-imap)
[![Hits](https://hits.webklex.com/svg/webklex/laravel-imap)](https://hits.webklex.com)


Installation of laravel-imap is a trivial process.In fact, there is no real installation.

## Install php dependencies
laravel-imap requires two common php modules **mbstring** and **mcrypt**.
```bash
sudo apt-get install php*-mbstring php*-mcrypt
sudo apache2ctl graceful
```

## Install with composer
The easiest way to install laravel-imap is to require it using Composer.
```bash
composer require webklex/laravel-imap
```
If you want to check out a different version of laravel-imap, add the desired version as an additional parameter:
```bash
composer require webklex/laravel-imap:2.2.0
```

## Legacy support
If you plan to use legacy protocols such as **pop3** or **nntp** you also have to install the native php php-imap module:
```bash
sudo apt-get install php*-imap
sudo apache2ctl graceful
```

## Older Laravel versions < 5.5
If you're using Laravel >= 5.5, package discovery will configure the service provider and Client alias out of the box.
Otherwise, for Laravel <= 5.4, edit your config/app.php file and:

- Add the following to the providers array:
```php
Webklex\IMAP\Providers\LaravelServiceProvider::class,
```
- add the following to the aliases array:
```php
'Client' => Webklex\IMAP\Facades\Client::class,
```

## Publish the configuration file
It's highly recommended you use and modify your own copy of the config file. Execute the following command to publish
the package config file. It will be placed under config/imap.php.

```bash
php artisan vendor:publish --provider="Webklex\IMAP\Providers\LaravelServiceProvider"
```
