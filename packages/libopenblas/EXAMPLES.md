# libopenblas/libopenblas examples

```php
use Pnlx\Libopenblas\Libopenblas;

$libopenblas = new Libopenblas();

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
