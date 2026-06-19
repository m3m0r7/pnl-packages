# libhunspell/libhunspell examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhunspell\Libhunspell;

// Create a Hunspell handle from an affix + dictionary pair, then free it.
$handle = Libhunspell::Hunspell_create('en_US.aff', 'en_US.dic');
Libhunspell::Hunspell_destroy($handle);

// Explore further: Hunspell_spell(), Hunspell_suggest(),
// Hunspell_analyze(), Hunspell_free_list(), ...
```
