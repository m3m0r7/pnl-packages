# libnng/libnng examples

```php
use Pnlx\Libnng\Libnng;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnng = $runtime->load(Libnng::class);

// nng_version() returns the NNG version string, e.g. "1.8.0".
$version = $libnng->nng_version();
echo "nng: $version\n";

// Explore further: nng_req0_open(), nng_dial(),
// nng_send(), nng_recv(), nng_listen(), ...
```
