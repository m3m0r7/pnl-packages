# libproj angle conversion

Convert between degrees and radians with the standalone `proj_torad()` / `proj_todeg()` helpers, which need no PJ context.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libproj\Libproj;

$num = static fn ($x) => is_object($x) ? $x->toFloat() : $x;

// proj_torad() / proj_todeg() are pure angle converters (no context needed).
$rad = $num(Libproj::proj_torad(180.0));   // degrees -> radians (~pi)
$deg = $num(Libproj::proj_todeg($rad));     // radians -> degrees (back to 180)

printf("180 deg = %.6f rad\n", $rad);   // 180 deg = 3.141593 rad
printf("%.6f rad = %.1f deg\n", $rad, $deg); // 3.141593 rad = 180.0 deg
```
