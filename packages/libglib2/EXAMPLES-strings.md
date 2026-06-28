# libglib2 string helpers

GLib ships handy string predicates and comparisons: `g_str_has_prefix()` / `g_str_has_suffix()` test boundaries and `g_strcmp0()` is a NULL-safe `strcmp`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libglib2\Libglib2;

$i = static fn($x) => is_object($x) ? $x->toInt() : $x;

// g_str_has_prefix() / g_str_has_suffix() test string boundaries.
echo 'has prefix "file://": ', $i(Libglib2::g_str_has_prefix('file:///etc/hosts', 'file://')), "\n";
echo 'has suffix ".png": ', $i(Libglib2::g_str_has_suffix('logo.png', '.png')), "\n";

// g_strcmp0() is a NULL-safe strcmp returning <0, 0, or >0.
echo 'strcmp0(abc, abd): ', $i(Libglib2::g_strcmp0('abc', 'abd')), "\n";
```
