# libsodium random numbers

Generate cryptographically secure random numbers and inspect the active RNG implementation.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsodium\Libsodium;

// Initialise the library (must be called once before any crypto operation).
Libsodium::sodium_init();

$toInt = static fn ($v) => is_object($v) ? (int) (string) $v : (int) $v;
$toStr = static fn ($v) => is_object($v) ? (string) $v : (string) $v;

// Numeric library version (distinct from the version *string*).
$major = $toInt(Libsodium::sodium_library_version_major());
$minor = $toInt(Libsodium::sodium_library_version_minor());
echo "library version: {$major}.{$minor}" . PHP_EOL;

// Name of the active random-bytes implementation.
$impl = $toStr(Libsodium::randombytes_implementation_name());
echo "rng implementation: {$impl}" . PHP_EOL;

// A cryptographically secure 32-bit random number.
$r = $toInt(Libsodium::randombytes_random());
echo "random uint32: {$r}" . PHP_EOL;

// A uniform random integer in [0, 6) — e.g. a fair dice roll (1-6).
$roll = $toInt(Libsodium::randombytes_uniform(6)) + 1;
echo "dice roll (1-6): {$roll}" . PHP_EOL;
```
