# libunistring character-class predicates

`uc_is_alpha()`, `uc_is_digit()` and `uc_is_space()` classify a Unicode code point, returning a non-zero value when it belongs to the class.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libunistring\Libunistring;

// Character-class predicates classify a Unicode code point; each returns a
// non-zero value when the code point belongs to the class.
$unwrap = static fn ($x) => is_object($x) ? $x->toInt() : $x;

echo 'A is alpha: ' . $unwrap(Libunistring::uc_is_alpha(0x0041)) . PHP_EOL; // 1
echo '7 is digit: ' . $unwrap(Libunistring::uc_is_digit(0x0037)) . PHP_EOL; // 1
echo 'space is space: ' . $unwrap(Libunistring::uc_is_space(0x0020)) . PHP_EOL; // 1
```
