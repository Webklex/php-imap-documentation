---
title: Proxy
---

Basic proxy example with authorization:

```php
/** @var \Webklex\PHPIMAP\Clientmanager $cm */
/** @var \Webklex\PHPIMAP\Client $client */

$client = $cm->make([
    'host' => 'imap.somehost.com',
    'port' => 993,
    'encryption' => 'ssl',
    'validate_cert' => true,
    'username' => 'example@somehost.com',
    'password' => 'Password',
    'protocol' => 'imap',
    'proxy' => [
        'socket' => "tcp://proxy.com:3444",
        'request_fulluri' => false,
        'username' => "my_username",
        'password' => "secret_password",
    ]
]);
```
