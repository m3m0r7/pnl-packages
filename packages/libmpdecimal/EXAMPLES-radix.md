# libmpdecimal/libmpdecimal radix and word digits

Inspect library-level numeric properties: the arithmetic radix and the number of decimal digits stored in a single mpdecimal word.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmpdecimal\Libmpdecimal;

// mpd_radix() returns the arithmetic radix (10) used by the library.
$radix = Libmpdecimal::mpd_radix();
echo (is_object($radix) ? $radix->toInt() : $radix) . PHP_EOL;
// mpd_word_digits() returns the number of decimal digits in a single word.
$digits = Libmpdecimal::mpd_word_digits(123456);
echo (is_object($digits) ? $digits->toInt() : $digits) . PHP_EOL;
```
