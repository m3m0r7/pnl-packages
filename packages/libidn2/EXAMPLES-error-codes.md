# libidn2/libidn2 error code lookup

`idn2_strerror_name()` returns the symbolic constant and `idn2_strerror()` the human-readable description for any libidn2 return code (the `Idn2_rc` enum).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libidn2\Libidn2;

// idn2_strerror_name() returns the symbolic constant and idn2_strerror() the
// human-readable description for any libidn2 return code (Idn2_rc enum).
foreach ([0, -100, -200, -206] as $rc) {
    $name = Libidn2::idn2_strerror_name($rc);
    $msg  = Libidn2::idn2_strerror($rc);
    echo $rc . ": " . (string)$name . " — " . (string)$msg . "\n";
}
```
