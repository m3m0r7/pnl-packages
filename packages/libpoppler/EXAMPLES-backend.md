# libpoppler/libpoppler backend and NSS-directory example

Query the active rendering backend enum and the configured NSS certificate directory used for signature verification.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpoppler\Libpoppler;

// poppler_get_backend() reports which rendering backend the library was built
// with, as a PopplerBackend enum value.
$backend = Libpoppler::poppler_get_backend();
echo "Poppler backend id: " . (is_object($backend) ? $backend->toInt() : $backend) . "\n";

// poppler_get_nss_dir() returns the configured NSS certificate directory used
// for digital-signature verification (empty when none is configured).
$nss = Libpoppler::poppler_get_nss_dir();
$nss = $nss === null ? '' : (string) $nss;
echo "Poppler NSS dir: " . ($nss === '' ? "(none configured)" : $nss) . "\n";
```
