---
title: oAuth
---

In order to use oAuth you need to obtain an access token first.
Once you have the token, please proceed by setting the `authentication` to `oauth` and provide the access token as `password`:

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */

$client = $cm->make([
   'host'           => 'some.host.tld',
   'port'           => 993,
   'encryption'     => 'ssl',
   'validate_cert'  => true,
   'protocol'       => 'imap',
   'username'       => 'username@host.tld',
   'password'       => 'ACCESS-TOKEN',
   'authentication' => "oauth",
]);
```

# Google / Gmail
## Connect using an application password
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
   'validate_cert' => true,
   'protocol'      => 'imap',
   'username'      => 'username@gmail.com',
   'password'      => 'new-generated-password'
]);
```

_Credits: [@stacyprowell](https://medium.com/swlh/setting-up-gmail-and-other-email-on-a-raspberry-pi-6f7e3ad3d0e)_


# Outlook / Office 365
1. Register an app in Azure AD
2. Configured it properly in Azure AD (add all required scopes for IMAP/SMTP like IMAP.AccessAsUser.All, offline_access, etc.)

!! Ensure your scope is set to https://outlook.office.com/IMAP.AccessAsUser.All

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */
$client = $cm->make([
        'host' => 'outlook.office365.com',
        'port' => 993,
        'encryption' => 'ssl', // 'tls',
        'validate_cert' => true,
        'username' => 'xyz@outlook.com',
        'password' => 'AccessToken',
        'protocol' => 'imap',
        'authentication' => "oauth",
]);
```

_Credits: [@EthraZa](https://github.com/EthraZa)_

## Additional links:
- https://github.com/MicrosoftDocs/office-developer-exchange-docs/issues/87
- https://github.com/Webklex/php-imap/issues/81
- https://github.com/MicrosoftDocs/office-developer-exchange-docs/issues/100

