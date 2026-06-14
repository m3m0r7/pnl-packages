# libgnutls/libgnutls examples

```php
use Pnlx\Libgnutls\Libgnutls;

$libgnutls = new Libgnutls();

// gnutls_check_version(null) returns the runtime version string.
$version = $libgnutls->gnutls_check_version(null);
echo "GnuTLS: $version\n";

// Explore further: gnutls_global_init(), gnutls_init(),
// gnutls_handshake(), gnutls_record_send(), ...
```
