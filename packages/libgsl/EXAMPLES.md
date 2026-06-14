# libgsl/libgsl examples

```php
use Pnlx\Libgsl\Libgsl;

// Evaluate a Bessel function J0(x) and a polynomial power
$j0 = Libgsl::gsl_sf_bessel_J0(5.0);
echo "J0(5.0) = " . $j0 . "\n";

$pow3 = Libgsl::gsl_pow_int(2.0, 10);
echo "2^10 = " . $pow3 . "\n";

// gsl_version is a global const char* string exposed as a method
// echo "GSL version: " . Libgsl::gsl_version() . "\n";
```
