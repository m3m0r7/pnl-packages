# libvterm/libvterm attribute value types

Use `vterm_get_attr_type()` to look up which value type (bool, int, color, ...) each pen attribute carries.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libvterm\Libvterm;

// vterm_get_attr_type(int) maps a pen attribute to the value type it carries.
// VTERM_ATTR_BOLD=1 -> VTERM_VALUETYPE_BOOL=1
// VTERM_ATTR_FONT=8 -> VTERM_VALUETYPE_INT=2
// VTERM_ATTR_FOREGROUND=9 -> VTERM_VALUETYPE_COLOR=4
foreach (['BOLD' => 1, 'FONT' => 8, 'FOREGROUND' => 9] as $name => $attr) {
    $t = Libvterm::vterm_get_attr_type($attr);
    $t = is_object($t) ? $t->toInt() : $t;
    echo "attr $name ($attr) -> valuetype $t\n";
}
```
