# OpenBLAS Package

Package: `libopenblas/libopenblas`

Base library: OpenBLAS

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libopenblas
```

The package requires OpenBLAS headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libopenblas\Libopenblas;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libopenblas = $runtime->load(Libopenblas::class);

// Compute dot product of two double vectors: [1,2,3] · [4,5,6] = 32
// cblas_ddot(n, x, incx, y, incy) → double (returned as PHP float)
$n = 3;
$x = \FFI::new("double[$n]");
$y = \FFI::new("double[$n]");
$x[0] = 1.0; $x[1] = 2.0; $x[2] = 3.0;
$y[0] = 4.0; $y[1] = 5.0; $y[2] = 6.0;

$dot = $libopenblas->cblas_ddot($n, $x, 1, $y, 1);
echo "Dot product: $dot\n"; // 32
// ... use cblas_dgemm() for matrix multiplication ...
```

This snippet is printed when `pnl install libopenblas` finishes — it comes from the package's `examples` field in `pnlx.json`.
