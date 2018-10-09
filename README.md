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

### Usage

```php
$num = 456;

/**
 * Create a 7-character hash from integer
 */
$hash = \CloudVerve\HashInt::hash( $num, 7 );

// Unhash the string
$unhashed = \CloudVerve\HashInt::unhash( $hash );

echo 'Hashed: ' . $hash . '<br />';
echo 'Unhashed: ' . $unhashed;
```

### Result

```
Hashed: p3Wq1aC
Unhashed: 456
```

## Original [Author](https://github.com/KevBurnsJr) Notes

Paraphrased ([source](http://web.archive.org/web/20130727034425/http://blog.kevburnsjr.com/php-unique-hash)):

> I wanted a short, unique, alphanumeric hash with a sequence that is difficult to deduce. I could create it with md5 and trim the first _n_ chars, but storing a truncated checksum in a unique field means that the frequency of collisions will increase geometrically as the number of unique keys for a base 62-encoded integer approaches 62^n. I'd rather do it right than create a time bomb.


### Base 62
Hashes are base 62 encoded base 10 integers. 1=1, 10=a, 36=Z, 61=z, 62=10, 72=1a, etc.

### 62, 3844, 238328, 14776336, 916132832, 56800235584, 3521614606208
1 character = 62 permutations, 2 characters = 3844 permutations, etc.

### 41, 2377, 147299, 9132313, 566201239, 35104476161, 2176477521929
41 = next highest prime from golden mean of 62.

2377 = next highest prime from golden mean of 3844.

### Uniqueness
> I chose to use primes to ensure hash uniqueness. Any prime greater than one half 62^n will do, but if you use a prime near 62^n or 62^n/2 or 2*62^n/3 etc, you will detect a linearity in the sequence at certain points in the ring.

### Appearance of Randomness
> I chose primes near the golden ratio to maximize the appearance of randomness. Given a small set of hashes (even with the associated id) it would be difficult for anyone to guess the next hash.

### :warning: Minimum-Security Technique
This is a thin rotation and base re-encoding obfuscation algorithm, not an encryption algorithm. Don't use this to encrypt sensitive information - use it to obfuscate integer IDs or create short reference keys (as an example, for short URLs).

### Special Thanks
- [Prime Numbers Generator and Checker](https://www.numberempire.com/primenumbers.php?utm_source=github.com&utm_medium=referral&utm_content=link&utm_campaign=dmhendricks%2Fhash-int)
- [Ernesto Preste](https://www.linkedin.com/in/ernesto-preste-4377912b/) for adding [bcmath support](http://web.archive.org/web/20130727034425/http://blog.kevburnsjr.com/php-unique-hash#comment-2792)
- [Padraig Kennedy](https://twitter.com/Padraig) for adding [hash reversibility](http://web.archive.org/web/20130727034425/http://blog.kevburnsjr.com/php-unique-hash#comment-2805)
