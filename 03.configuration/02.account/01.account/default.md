---
menu: Options
title: Account Configuration
---
The key assigned within the `accounts` array can be used to provide a different default account. Every key has to unique.

## Host
```text
Property: host
Value:    Any domain name or ip address
```

## Port
```text
Property: port
Value:    Any port between 0 and 65535
```

## Protocol
The Protocol you want to utilize. If you want to use legacy-imap, pop3 or nntp you have to install the legacy support as
described in the [installation](/installation) section.

**Available protocols:**<br />
`imap` &mdash; Use IMAP<br />
`legacy-imap` &mdash; Use the php imap module instead<br />
`pop3` &mdash; Use POP3<br />
`nntp` &mdash; Use NNTP<br />

```text
Property: protocol
Value:    any of the above
```

## Encryption method
Used encryption method. Use false to disable encryption.

**Available methods:**<br />
`false` &mdash; Disable encryption<br />
`ssl` &mdash; Use SSL<br />
`tls` &mdash; Use TLS<br />
`starttls` &mdash; Use STARTTLS (alias TLS) (legacy only)<br />
`notls` &mdash; Use NoTLS (legacy only)<br />

```text
Property: encryption
Value:    any of the above
```

## Certificate validation
The certificate gets validated by default. You can turn this off, by setting it to false.
```text
Property: validate_cert
Value:    true or false
```

## Username
Your account username.
```text
Property: username
Value:    anything
```

## Password
Your account password.
```text
Property: password
Value:    anything
```

## Authentication method
Set it to `oauth` if you want to authenticate using oAuth. You may provide your access token as `password`.
An example is available here:  [oAuth using Google](../../../examples/oauth)
```text
Property: authentication
Value:    "oauth" or null
```

## Proxy
Contains a list of all required proxy settings.
Please take a look at the [proxy configuration](../proxy) section for more detail.

```text
Property: proxy
Value:    proxy settings
```
