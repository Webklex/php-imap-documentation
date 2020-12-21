---
menu: Options
title: Base Configuration
---

The default package configuration file is located under [vendor/webklex/php-imap/src/config/imap.php](https://github.com/Webklex/php-imap/blob/master/src/config/imap.php)
and consists of a multidimensional array.

It's recommended to copy the config file into your project config directory and modify that version instead.
Otherwise you might not be able to update the package in the future.

## Default date format
The default date format is used to convert any given Carbon::class object into a valid date string. These are currently
known working formats: "d-M-Y", "d-M-y", "d M y".
```text
Property: date_format
Value:    "d-M-Y", "d-M-y" or "d M y"
```

## Default account
The default account identifier. It will be used as default for any missing account parameters. If however the default account is missing a parameter the package default will be used. Set to 'false' [boolean] to disable this functionality.

```text
Property: default
Value:    Any of your under "accounts" defined account array keys
```

## Available accounts
Contains a list of all available and therefor predefined accounts you might want to use within your application.
Please take a look at the [account configuration](../account/account) section for more detail.

```text
Property: accounts
Value:    List of predefined accounts
```


## Advanced fetching configuration
Contains a list of all available and therefor predefined advanced fetching options you might want to use within your application.
Please take a look at the [advanced configuration](../advanced) section for more detail.

```text
Property: options
Value:    List of advanced options
```

## Event configuration
Contains a list of all available and therefor predefined events you might want to use within your application.
Please take a look at the [event configuration](../events) section for more detail.

```text
Property: events
Value:    Lists of registered events
```

## Mask configuration
Contains a list of all available and therefor predefined masks you might want to use within your application.
Please take a look at the [mask configuration](../masks) section for more detail.

```text
Property: masks
Value:    List of default masks
```

