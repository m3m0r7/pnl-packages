# libopenblas/libopenblas examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenblas\Libopenblas;
use Pnlx\Libopenblas\Types\double as DoubleVector;

// Compute dot product of two double vectors: [1,2,3] · [4,5,6] = 32
// cblas_ddot(n, x, incx, y, incy) → double (returned as PHP float).
// The `const double *` inputs are read-only buffers: allocate them as the
// generated `Types\double` wrapper (a `double[$n]`) and fill the elements.
$n = 3;
$x = new DoubleVector(null, $n);
$y = new DoubleVector(null, $n);
foreach ([1.0, 2.0, 3.0] as $i => $value) { $x->cdata()[$i] = $value; }
foreach ([4.0, 5.0, 6.0] as $i => $value) { $y->cdata()[$i] = $value; }

$dot = Libopenblas::cblas_ddot($n, $x, 1, $y, 1);
echo "Dot product: $dot\n"; // 32
// ... use cblas_dgemm() for matrix multiplication ...
```
