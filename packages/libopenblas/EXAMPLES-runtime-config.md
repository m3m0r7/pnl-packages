# libopenblas/libopenblas runtime config

Query the OpenBLAS build/runtime info with no-argument introspection functions: `openblas_get_config` and `openblas_get_corename` return `char*` strings, while `openblas_get_num_procs` returns an int.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenblas\Libopenblas;

// Build configuration string (char* → PHP string)
$config = Libopenblas::openblas_get_config();
echo 'Config: ' . (string)$config . "\n"; // e.g. OpenBLAS 0.3.33 DYNAMIC_ARCH ...

// Number of physical processors detected
$procs = Libopenblas::openblas_get_num_procs();
echo 'Num procs: ' . (is_object($procs) ? $procs->toInt() : $procs) . "\n";

// Active CPU micro-architecture kernel name (char* → PHP string)
$core = Libopenblas::openblas_get_corename();
echo 'Core name: ' . (string)$core . "\n"; // e.g. vortexm4
```
