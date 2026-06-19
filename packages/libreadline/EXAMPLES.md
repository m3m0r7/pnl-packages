# libreadline/libreadline examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libreadline\Libreadline;

// tilde_expand() expands a leading ~ to the home directory — a pure call that needs
// no terminal.
echo Libreadline::tilde_expand('~/.bashrc') . "\n"; // e.g. /root/.bashrc
```
