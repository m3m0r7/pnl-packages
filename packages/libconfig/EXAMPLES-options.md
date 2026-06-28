# libconfig formatting options

Tune the output-formatting options on a `config_t` (tab width and float precision) using their setter/getter pairs, without parsing any input.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libconfig\Libconfig;
use Pnlx\Libconfig\Types\config_t;

// Allocate and initialise a config_t, then tune output-formatting options
// (these setters/getters operate on the config object itself, no parsing needed).
$cfg = new config_t();
Libconfig::config_init($cfg);

// Tab width controls indentation when writing configs back out (0-15).
Libconfig::config_set_tab_width($cfg, 4);
$tab = Libconfig::config_get_tab_width($cfg);
echo 'tab width: ' . (is_object($tab) ? $tab->toInt() : $tab) . "\n"; // 4

// Float precision controls how many digits floats are written with.
Libconfig::config_set_float_precision($cfg, 6);
$prec = Libconfig::config_get_float_precision($cfg);
echo 'float precision: ' . (is_object($prec) ? $prec->toInt() : $prec) . "\n"; // 6

Libconfig::config_destroy($cfg);
```
