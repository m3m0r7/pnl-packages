# libfftw3/libfftw3 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfftw3\Libfftw3;
use function Pnlx\Util\is_null;

// Allocate a complex input/output array and create a 1-D DFT plan.
$n = 8;
$in  = Libfftw3::fftw_alloc_complex($n);
$out = Libfftw3::fftw_alloc_complex($n);
if (is_null($in) || is_null($out)) {
    throw new \RuntimeException('fftw_alloc_complex() failed');
}

// FFTW_FORWARD = -1, FFTW_ESTIMATE = (1 << 6) = 64
$plan = Libfftw3::fftw_plan_dft_1d($n, $in, $out, -1, 64);
Libfftw3::fftw_execute($plan);
Libfftw3::fftw_destroy_plan($plan);
Libfftw3::fftw_free($in);
Libfftw3::fftw_free($out);
echo "1-D DFT of {$n} complex samples computed." . PHP_EOL;
```
