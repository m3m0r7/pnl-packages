# liblame/liblame examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblame\Liblame;

// lame_init() allocates an encoder context; lame_close() frees it. This confirms
// the LAME MP3 encoder loads and its core entry points bind correctly.
$gf = Liblame::lame_init();
echo ($gf === null ? "lame_init failed" : "lame initialized") . PHP_EOL;
Liblame::lame_close($gf);
```
