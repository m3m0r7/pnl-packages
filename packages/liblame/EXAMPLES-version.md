# liblame/liblame version strings

The `get_lame_*` family returns build/version metadata as plain strings, useful for logging which LAME build is linked.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblame\Liblame;

$ver = Liblame::get_lame_version();
echo "version: " . (string)$ver . PHP_EOL;

$short = Liblame::get_lame_short_version();
echo "short: " . (string)$short . PHP_EOL;

$url = Liblame::get_lame_url();
echo "url: " . (string)$url . PHP_EOL;
```
