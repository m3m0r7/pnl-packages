# libmpfr/libmpfr examples

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
