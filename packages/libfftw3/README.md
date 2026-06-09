# FFTW Package

Package: `libfftw3/libfftw3`

Base library: FFTW

License: GPL-2.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libfftw3
```

The package requires FFTW headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libfftw3\Libfftw3;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libfftw3 = $runtime->load(Libfftw3::class);

// Allocate a complex input/output array and create a 1-D DFT plan.
$n = 8;
$in  = $libfftw3->fftw_alloc_complex($n);
$out = $libfftw3->fftw_alloc_complex($n);
if (is_null($in) || is_null($out)) {
    throw new \RuntimeException('fftw_alloc_complex() failed');
}

// FFTW_FORWARD = -1, FFTW_ESTIMATE = (1 << 6) = 64
$plan = $libfftw3->fftw_plan_dft_1d($n, $in, $out, -1, 64);
$libfftw3->fftw_execute($plan);
$libfftw3->fftw_destroy_plan($plan);
$libfftw3->fftw_free($in);
$libfftw3->fftw_free($out);
echo "1-D DFT of {$n} complex samples computed." . PHP_EOL;
```

This snippet is printed when `pnl install libfftw3` finishes — it comes from the package's `examples` field in `pnlx.json`.
