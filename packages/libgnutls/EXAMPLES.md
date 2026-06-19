# libgnutls/libgnutls examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgnutls\Libgnutls;

// gnutls_check_version(null) returns the runtime version string.
$version = Libgnutls::gnutls_check_version(null);
echo "GnuTLS: $version\n";

// Explore further: gnutls_global_init(), gnutls_init(),
// gnutls_handshake(), gnutls_record_send(), ...
```
