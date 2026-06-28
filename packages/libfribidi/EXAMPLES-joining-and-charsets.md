# libfribidi joining types and character sets

Look up a code point's Arabic joining type and resolve a character-set name to its id and human-readable title.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfribidi\Libfribidi;

$num = fn($x) => is_object($x) ? $x->toInt() : $x;
$str = fn($x) => $x === null ? '(null)' : (string)$x;

// fribidi_get_joining_type() classifies the Arabic joining behaviour of a code
// point; _name() turns the result into its short name ('D' = dual-joining).
$jt = Libfribidi::fribidi_get_joining_type(0x0628); // Arabic letter Beh
echo 'joining type = ' . $str(Libfribidi::fribidi_get_joining_type_name($jt)) . "\n";

// fribidi_parse_charset() resolves a charset name to its id; _name()/_title()
// round-trip it back to canonical and descriptive strings.
$cs = Libfribidi::fribidi_parse_charset('UTF-8');
echo 'charset id = ' . $num($cs) . "\n";
echo 'charset name = ' . $str(Libfribidi::fribidi_char_set_name($cs)) . "\n";
echo 'charset title = ' . $str(Libfribidi::fribidi_char_set_title($cs)) . "\n";
```
