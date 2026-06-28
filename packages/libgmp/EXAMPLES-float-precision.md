# libgmp default float precision

GMP's `mpf` floating-point type has a global default precision (in bits); read it with `__gmpf_get_default_prec()` and change it with `__gmpf_set_default_prec()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgmp\Libgmp;

$i = static fn($x) => is_object($x) ? $x->toInt() : $x;

// __gmpf_get_default_prec() reports the default precision (in bits) used for
// new mpf floating-point values; __gmpf_set_default_prec() changes it.
echo 'default prec: ', $i(Libgmp::__gmpf_get_default_prec()), "\n";
Libgmp::__gmpf_set_default_prec(256);
echo 'after set 256: ', $i(Libgmp::__gmpf_get_default_prec()), "\n";
```
