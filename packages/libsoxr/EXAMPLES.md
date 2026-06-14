# libsoxr/libsoxr examples

```php
use Pnlx\Libsoxr\Libsoxr;

$libsoxr = new Libsoxr();

// soxr_version() returns the libsoxr version string.
$version = $libsoxr->soxr_version();
echo "libsoxr: $version\n";

// Explore further: soxr_create(), soxr_process(),
// soxr_oneshot(), soxr_delete(), ...
```
