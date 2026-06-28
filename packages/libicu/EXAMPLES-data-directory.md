# libicu/libicu data directory

`u_getDataDirectory()` reports the external ICU data directory (the path set via `u_setDataDirectory()` or the `ICU_DATA` environment variable); an empty value means ICU is resolving data from its built-in package.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libicu\Libicu;

// u_getDataDirectory() reports the external ICU data directory (set via
// u_setDataDirectory()/ICU_DATA). Like every ICU entry point it is exported
// version-suffixed (u_getDataDirectory_NN) and pnl recovers the public name.
$dir = (string) Libicu::u_getDataDirectory();
echo "ICU data directory: " . ($dir === '' ? '(none — using built-in data)' : $dir) . "\n";
```
