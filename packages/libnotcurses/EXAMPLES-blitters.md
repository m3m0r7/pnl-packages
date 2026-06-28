# libnotcurses blitter and scaling names

Resolve `ncblitter_e` and `ncscale_e` enum values to their human-readable names with the pure `notcurses_str_*` lookups.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnotcurses\Libnotcurses;

// notcurses_str_blitter() maps an ncblitter_e enum value to its human name.
for ($b = 0; $b <= 3; $b++) {
    $name = Libnotcurses::notcurses_str_blitter($b);
    echo "blitter $b => " . (string)$name . "\n";
}

// notcurses_str_scalemode() maps an ncscale_e enum value to its name.
for ($s = 0; $s <= 2; $s++) {
    $name = Libnotcurses::notcurses_str_scalemode($s);
    echo "scale $s => " . (string)$name . "\n";
}
```
