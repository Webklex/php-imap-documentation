---
title: Configuration
---

If you are planning to use a single account, you might want to add the following to your .env file.

```
IMAP_HOST=somehost.com
IMAP_PORT=993
IMAP_ENCRYPTION=ssl
IMAP_VALIDATE_CERT=true
IMAP_USERNAME=root@example.com
IMAP_PASSWORD=secret
IMAP_DEFAULT_ACCOUNT=default
IMAP_PROTOCOL=imap
```

Please take a look ath the [php-imap configuration](../../../configuration/configuration) for more detail.
