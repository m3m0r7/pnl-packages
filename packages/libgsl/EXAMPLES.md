# libgsl/libgsl examples

```php
use Pnlx\Libgsl\Libgsl;

$libgsl = new Libgsl();

// Evaluate a Bessel function J0(x) and a polynomial power
$j0 = $libgsl->gsl_sf_bessel_J0(5.0);
echo "J0(5.0) = " . $j0 . "\n";

$pow3 = $libgsl->gsl_pow_int(2.0, 10);
echo "2^10 = " . $pow3 . "\n";

// gsl_version is a global const char* string exposed as a method
// echo "GSL version: " . $libgsl->gsl_version() . "\n";
```
