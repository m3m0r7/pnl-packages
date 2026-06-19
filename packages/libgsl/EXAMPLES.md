# libgsl/libgsl examples

GSL's BLAS routines live in `libgsl` but call into a **second** shared library,
`libgslcblas`, which `libgsl` does not link itself. `libgslcblas` is co-loaded via
`dependencies`, so the BLAS functions resolve and work from a single
`Pnlx\Libgsl\Libgsl` entity.

```php
use Pnlx\Libgsl\Libgsl;

// Plain math (libgsl).
echo "2^10        = " . Libgsl::gsl_pow_int(2.0, 10) . "\n";   // 1024
echo "hypot(3,4)  = " . Libgsl::gsl_hypot(3.0, 4.0) . "\n";    // 5

// BLAS dot product: gsl_blas_ddot (in libgsl) calls cblas_ddot (in libgslcblas).
$x = Libgsl::gsl_vector_alloc(3);
$y = Libgsl::gsl_vector_alloc(3);
foreach ([[0, 1.0, 4.0], [1, 2.0, 5.0], [2, 3.0, 6.0]] as [$i, $a, $b]) {
    Libgsl::gsl_vector_set($x, $i, $a);
    Libgsl::gsl_vector_set($y, $i, $b);
}
$result = 0.0;                       // double* out-parameter
Libgsl::gsl_blas_ddot($x, $y, $result);
echo "[1,2,3]·[4,5,6] = " . $result . "\n";   // 32
```
