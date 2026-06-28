# libaspell/libaspell config examples

`new_aspell_config` creates a default configuration whose values can be read with `aspell_config_retrieve`, while `aspell_reset_cache` clears Aspell's internal caches.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libaspell\Libaspell;

// aspell_reset_cache(which) clears an internal cache and returns 1 on success.
$r = Libaspell::aspell_reset_cache("encode");
echo "reset_cache(encode): " . (is_object($r) ? $r->toInt() : $r) . "\n"; // 1

// Read a default option value from a fresh config object.
$config = Libaspell::new_aspell_config();
echo "default encoding: " . (string)Libaspell::aspell_config_retrieve($config, "encoding") . "\n"; // UTF-8
Libaspell::delete_aspell_config($config);
```
