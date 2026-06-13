# libsoxr/libsoxr examples

```php
use Pnlx\Libsoxr\Libsoxr;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsoxr = $runtime->load(Libsoxr::class);

// soxr_version() returns the libsoxr version string.
$version = $libsoxr->soxr_version();
echo "libsoxr: $version\n";

// Explore further: soxr_create(), soxr_process(),
// soxr_oneshot(), soxr_delete(), ...
```
