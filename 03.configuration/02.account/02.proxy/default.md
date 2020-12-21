---
menu: Proxy
title: Proxy Configuration
---
Optional proxy settings.

## Socket
```text
Property: socket
Value:    Used proxy socket (protocol + host + port)
```

## Request full uri
When set to true, the entire URI will be used when constructing the request. While this is a non-standard request
format, some proxy servers require it.
```text
Property: request_fulluri
Value:    true or false
```

## Username
Optional username if required
```text
Property: username
Value:    anything or null
```

## Password
Optional password if required
```text
Property: password
Value:    anything or null
```
