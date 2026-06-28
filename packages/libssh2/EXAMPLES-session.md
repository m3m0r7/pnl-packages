# libssh2 crypto backend and session state

Report which crypto backend libssh2 was built against and inspect a fresh session's blocking mode.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libssh2\Libssh2;
use function Pnlx\Util\is_null;

Libssh2::libssh2_init(0);

// libssh2_crypto_engine() reports which crypto backend libssh2 was built against.
$engine = Libssh2::libssh2_crypto_engine();
echo 'crypto engine: ' . ($engine !== null ? $engine->name : 'unknown') . "\n";

// A fresh session reports its blocking mode (1 = blocking, the default).
$session = Libssh2::libssh2_session_init_ex(null, null, null, null);
if (!is_null($session)) {
    $blocking = Libssh2::libssh2_session_get_blocking($session);
    echo 'blocking: ' . (is_object($blocking) ? $blocking->toInt() : $blocking) . "\n";
    Libssh2::libssh2_session_free($session);
}

Libssh2::libssh2_exit();
```
