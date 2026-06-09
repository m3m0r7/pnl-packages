# MPFR Package

Package: `libmpfr/libmpfr`

Base library: MPFR

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmpfr
```

The package requires MPFR headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmpfr\Libmpfr;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmpfr = $runtime->load(Libmpfr::class);

// Query library version
$version = $libmpfr->mpfr_get_version(); // returns char* → PHP string
echo "MPFR version: $version\n";

// Allocate a mpfr_t variable and compute a high-precision value
$x = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libmpfr->mpfr_init2($x, 256);           // 256-bit precision
$libmpfr->mpfr_set_d($x, 3.14159, 0);   // MPFR_RNDN = 0
$result = $libmpfr->mpfr_get_d($x, 0);
echo "Value: $result\n";
$libmpfr->mpfr_clear($x);
```

This snippet is printed when `pnl install libmpfr` finishes — it comes from the package's `examples` field in `pnlx.json`.
