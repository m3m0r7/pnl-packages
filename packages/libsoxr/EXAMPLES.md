# libsoxr/libsoxr examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsoxr\Libsoxr;

// soxr_version() returns the libsoxr version string.
$version = Libsoxr::soxr_version();
echo "libsoxr: $version\n";

// Explore further: soxr_create(), soxr_process(),
// soxr_oneshot(), soxr_delete(), ...
```
