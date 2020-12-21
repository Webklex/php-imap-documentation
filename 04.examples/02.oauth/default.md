---
title: oAuth using Google
---

In order to use oAuth you need to obtain an access token first.
Once you have the token, please proceed by setting the `authentication` to `oauth` and provide the access token as `password`:

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */

$client = $cm->make([
   'host'           => 'imap.googlemail.com',
   'port'           => 993,
   'encryption'     => 'ssl',
   'validate_cert'  => false,
   'protocol'       => 'imap',
   'username'       => 'username@gmail.com',
   'password'       => 'ACCESS-TOKEN',
   'authentication' => "oauth",
]);
```

# Connect using an application password
1. Go to [https://myaccount.google.com/](https://myaccount.google.com/) and click on "Security"
2. Under "Signing in to Google" click on "App passwords"
3. Click on "Select app" and choose "Mail" and click on "Select device" and choose "Other"
4. Click on "Generate" and use the displayed password (without any spaces) as your password

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */

$client = $cm->make([
   'host'          => 'imap.googlemail.com',
   'port'          => 993,
   'encryption'    => 'ssl',
   'validate_cert' => false,
   'protocol'      => 'imap',
   'username'      => 'username@gmail.com',
   'password'      => 'new-generated-password'
]);
```

_Credits: [@stacyprowell](https://medium.com/swlh/setting-up-gmail-and-other-email-on-a-raspberry-pi-6f7e3ad3d0e)_
