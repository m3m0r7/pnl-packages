# GSL Package

Package: `libgsl/libgsl`

Base library: GSL

License: GPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgsl
```

The package requires GSL headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libgsl\Libgsl;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libgsl = $runtime->load(Libgsl::class);

// Evaluate a Bessel function J0(x) and a polynomial power
$j0 = $libgsl->gsl_sf_bessel_J0(5.0);
echo "J0(5.0) = " . $j0 . "\n";

$pow3 = $libgsl->gsl_pow_int(2.0, 10);
echo "2^10 = " . $pow3 . "\n";

// gsl_version is a global const char* string exposed as a method
// echo "GSL version: " . $libgsl->gsl_version() . "\n";
```

This snippet is printed when `pnl install libgsl` finishes — it comes from the package's `examples` field in `pnlx.json`.
