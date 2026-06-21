# GNU FriBidi Package

Package: `libfribidi/libfribidi`

License: LGPL-2.1-or-later

## PHP usage

```php
use Pnlx\Libfribidi\Libfribidi;

// fribidi_get_bidi_type() classifies a Unicode code point; _type_name() names it.
$type = Libfribidi::fribidi_get_bidi_type(0x0041); // 'A'
echo Libfribidi::fribidi_get_bidi_type_name($type) . PHP_EOL; // LTR
```
