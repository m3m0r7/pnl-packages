# libssh/libssh examples

```php
use Pnlx\Libssh\Libssh;
use function Pnlx\Util\is_null;

// Create a new SSH session.
$session = Libssh::ssh_new();
if (is_null($session)) { throw new \RuntimeException('ssh_new failed'); }

// Configure the host before connecting.
Libssh::ssh_options_set($session, 0 /* SSH_OPTIONS_HOST */, 'example.com');

// Connect, authenticate, run commands, then free the session.
// Libssh::ssh_connect($session);
Libssh::ssh_free($session);
```
