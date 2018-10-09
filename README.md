[![Release](https://img.shields.io/github/release/dmhendricks/hash-int.svg?style=flat-square)](https://github.com/dmhendricks/hash-int/releases)
[![GitHub License](https://img.shields.io/badge/license-MIT-yellow.svg?style=flat-square)](https://raw.githubusercontent.com/dmhendricks/hash-int/master/LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/dmhendricks/hash-int.svg?style=flat-square)](https://packagist.org/packages/dmhendricks/hash-int?utm_source=github.com&utm_medium=referral&utm_content=button&utm_campaign=dmhendricks%2Fhash-int)
[![Analytics](https://ga-beacon.appspot.com/UA-126205765-1/dmhendricks/hash-int?flat)](https://ga-beacon.appspot.com/?utm_source=github.com&utm_medium=campaign&utm_content=button&utm_campaign=dmhendricks%2Fhash-int)
[![Twitter](https://img.shields.io/twitter/url/https/github.com/dmhendricks/hash-int.svg?style=social)](https://twitter.com/danielhendricks)

# Hash Integer

A PHP class to generate a short hash from an integer.

```
composer require dmhendricks/hash-int
```

## Usage

```php
$num = 456;

// Create 7-character hash from integer
$hash = \CloudVerve\HashInt::hash( $num, 7 );

// Unhashed value
$unhashed = \CloudVerve\HashInt::unhash( $hash );

echo 'Hashed: ' . $hash . '<br />';
echo 'Unhashed: ' . $unhashed;
```

### Result

```
Hashed: cJinsP6
Unhashed: 456
```
