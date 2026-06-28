# libass/libass version example

`ass_library_version` returns the libass ABI version as a packed integer, without needing a library handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libass\Libass;

// ass_library_version() returns the ABI version packed as 0xMMmmpp00.
$v = Libass::ass_library_version();
$v = is_object($v) ? $v->toInt() : $v;
printf("libass ABI version: 0x%08x\n", $v); // e.g. 0x01704000
```
