# libssh2/libssh2 examples

```php
use Pnlx\Libssh2\Libssh2;
use function Pnlx\Util\is_null;

// Print the libssh2 version string.
echo Libssh2::libssh2_version(0) . PHP_EOL;

// Initialise the library (call once at application start).
Libssh2::libssh2_init(0);

// Create a session for a connected socket $sock (int):
// $session = Libssh2::libssh2_session_init_ex(null, null, null, null);
// if (!is_null($session)) { Libssh2::libssh2_session_handshake($session, $sock); }
Libssh2::libssh2_exit();
```
