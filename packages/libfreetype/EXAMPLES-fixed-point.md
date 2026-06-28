# libfreetype fixed-point arithmetic

FreeType ships standalone 16.16 fixed-point helpers — multiply, divide and round — that need no `FT_Library` handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfreetype\Libfreetype;

$num = fn($x) => is_object($x) ? $x->toInt() : $x;

// FT_MulFix multiplies two 16.16 fixed values: 1.0 * 0.5 = 0.5 (0x8000).
$mul = Libfreetype::FT_MulFix(0x10000, 0x8000);
echo 'FT_MulFix(1.0, 0.5) = 0x' . dechex($num($mul)) . "\n";

// FT_DivFix divides two fixed values: 1.0 / 2.0 = 0.5 (0x8000).
$div = Libfreetype::FT_DivFix(0x10000, 0x20000);
echo 'FT_DivFix(1.0, 2.0) = 0x' . dechex($num($div)) . "\n";

// FT_RoundFix rounds a fixed value to the nearest integer: 1.5 -> 2.0 (0x20000).
$round = Libfreetype::FT_RoundFix(0x18000);
echo 'FT_RoundFix(1.5) = 0x' . dechex($num($round)) . "\n";
```
