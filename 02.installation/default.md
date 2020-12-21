---
title: Installation
---

Installation of php-imap is a trivial process.
In fact, there is no real installation.

You have two options for installing php-imap.
The first - and simplest - way is to install with **Composer**.
The second way is to clone the source project directly from **GitHub**, and then run an included script command to install needed dependencies.

## Install php dependencies
php-imap requires two common php modules **mbstring** and **mcrypt**.
```bash
sudo apt-get install php*-mbstring php*-mcrypt
sudo apache2ctl graceful
```

## Option 1: Install with composer
The easiest way to install php-imap is to require it using Composer.
```bash
composer require webklex/php-imap
```
If you want to check out a different version of php-imap, add the desired version as an additional parameter:
```bash
composer require webklex/php-imap:2.2.5
```

## Option 2: Install from GitHub
Another method is to clone php-imap from the GitHub repository, and then run a simple dependency installation script:

1. Clone the php-imap repository from GitHub to a folder in the webroot of your application, e.g. ~/webroot. Launch a terminal or console and navigate to the webroot folder:
```bash
cd ~/webroot
git clone https://github.com/Webklex/php-imap.git
```

2. Install vendor dependencies via composer:
```bash
cd php-imap
composer install
```

## Legacy support
If you plan to use legacy protocols such as **pop3** or **nntp** you also have to install the native php php-imap module:
```bash
sudo apt-get install php*-imap
sudo apache2ctl graceful
```
