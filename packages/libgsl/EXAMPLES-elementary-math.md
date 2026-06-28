# libgsl/libgsl elementary math

The `gsl_math.h` helpers return plain doubles, including integer powers and the `log1p`/`expm1` variants that stay accurate near zero.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgsl\Libgsl;

// Elementary helpers from gsl_math.h that return plain doubles.
echo "pow_2(7)    = " . Libgsl::gsl_pow_2(7.0) . "\n";    // 49
echo "pow_3(3)    = " . Libgsl::gsl_pow_3(3.0) . "\n";    // 27
echo "log1p(1e-9) = " . Libgsl::gsl_log1p(1e-9) . "\n";   // ~1e-9 (accurate near 0)
echo "expm1(1e-9) = " . Libgsl::gsl_expm1(1e-9) . "\n";   // ~1e-9 (accurate near 0)
echo "acosh(1)    = " . Libgsl::gsl_acosh(1.0) . "\n";    // 0
```
