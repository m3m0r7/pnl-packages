# libssh version and copyright

Read the libssh runtime version string and its copyright notice.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libssh\Libssh;

// ssh_version() returns the libssh runtime version string.
echo 'version: ' . (string)Libssh::ssh_version(0) . "\n";

// ssh_copyright() returns the library copyright notice.
echo 'copyright: ' . (string)Libssh::ssh_copyright() . "\n";
```
