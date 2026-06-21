# libmecab/libmecab examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmecab\Libmecab;

echo Libmecab::mecab_version() . PHP_EOL;

// mecab_new2() builds a tagger from a command-line string; "" uses the system
// dictionary configured at install time. mecab_sparse_tostr() returns the parse
// as the familiar TSV lattice (surface \t feature, one token per line, EOS last).
$mecab = Libmecab::mecab_new2('');
if ($mecab === null) {
    throw new \RuntimeException('mecab_new2 failed: dictionary not found');
}
echo Libmecab::mecab_sparse_tostr($mecab, '日本語の形態素解析');
Libmecab::mecab_destroy($mecab);
```
