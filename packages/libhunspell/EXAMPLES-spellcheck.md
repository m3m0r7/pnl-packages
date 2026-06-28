# libhunspell spell checking

Load a dictionary with `Hunspell_create()`, then check words with `Hunspell_spell()` (nonzero means correct) and read the dictionary encoding with `Hunspell_get_dic_encoding()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhunspell\Libhunspell;

// Write a tiny affix + dictionary pair so the example is self-contained.
$dir = sys_get_temp_dir() . '/hunspell_demo_' . getmypid();
@mkdir($dir);
file_put_contents("$dir/en.aff", "SET UTF-8\n");
file_put_contents("$dir/en.dic", "3\nhello\nworld\nexample\n");

$h = Libhunspell::Hunspell_create("$dir/en.aff", "$dir/en.dic");

$enc = Libhunspell::Hunspell_get_dic_encoding($h);
echo "encoding: " . (string)$enc . "\n";

$ok = Libhunspell::Hunspell_spell($h, 'hello');
echo "spell hello: " . (is_object($ok) ? $ok->toInt() : $ok) . "\n";

$bad = Libhunspell::Hunspell_spell($h, 'helllo');
echo "spell helllo: " . (is_object($bad) ? $bad->toInt() : $bad) . "\n";

Libhunspell::Hunspell_destroy($h);
```
