# libssh/libssh examples

```php
use Pnlx\Libssh\Libssh;
use function Pnlx\Util\is_null;

$libssh = new Libssh();

// Create a new SSH session.
$session = $libssh->ssh_new();
if (is_null($session)) { throw new \RuntimeException('ssh_new failed'); }

// Configure the host before connecting.
$libssh->ssh_options_set($session, 0 /* SSH_OPTIONS_HOST */, 'example.com');

// Connect, authenticate, run commands, then free the session.
// $libssh->ssh_connect($session);
$libssh->ssh_free($session);
```
