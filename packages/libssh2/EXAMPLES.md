# libssh2/libssh2 examples

```php
use Pnlx\Libssh2\Libssh2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libssh2 = $runtime->load(Libssh2::class);

// Print the libssh2 version string.
echo $libssh2->libssh2_version(0) . PHP_EOL;

// Initialise the library (call once at application start).
$libssh2->libssh2_init(0);

// Create a session for a connected socket $sock (int):
// $session = $libssh2->libssh2_session_init_ex(null, null, null, null);
// if (!is_null($session)) { $libssh2->libssh2_session_handshake($session, $sock); }
$libssh2->libssh2_exit();
```
