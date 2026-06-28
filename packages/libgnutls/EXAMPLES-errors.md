# libgnutls error lookups

Turn a numeric GnuTLS error code into a human-readable description with `gnutls_strerror()` or into its symbolic constant name with `gnutls_strerror_name()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgnutls\Libgnutls;

// gnutls_strerror() / gnutls_strerror_name() turn a numeric error code into a
// human-readable description and its symbolic constant name.
echo 'name(0):    ', (string)Libgnutls::gnutls_strerror_name(0), "\n";
echo 'strerror(-25): ', (string)Libgnutls::gnutls_strerror(-25), "\n";
echo 'strerror(-50): ', (string)Libgnutls::gnutls_strerror(-50), "\n";
```
