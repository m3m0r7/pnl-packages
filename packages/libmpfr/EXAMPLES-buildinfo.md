# libmpfr/libmpfr build info and defaults

Query MPFR build metadata and runtime defaults: applied patches, thread-local-storage support, and the default working precision in bits.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmpfr\Libmpfr;

// mpfr_get_patches() lists the patches applied to this MPFR build.
echo "patches: [" . (string) Libmpfr::mpfr_get_patches() . "]" . PHP_EOL;
// mpfr_buildopt_tls_p() reports whether MPFR was built with thread-local storage.
$tls = Libmpfr::mpfr_buildopt_tls_p();
echo "tls: " . (is_object($tls) ? $tls->toInt() : $tls) . PHP_EOL;
// mpfr_get_default_prec() returns the default working precision in bits.
$prec = Libmpfr::mpfr_get_default_prec();
echo "default_prec: " . (is_object($prec) ? $prec->toInt() : $prec) . PHP_EOL;
```
